---
title:  What is Direct Craft?
date:   2010-02-06
cover:  /media/header.png
excerpt: DirectCraft is a library that generates object serialization code and stores it in a way that can be easily saved/loaded and converted...
---
DirectCraft is a library that generates object serialization code and stores it in a way that can be easily saved/loaded and converted.  "dcx", the DirectCraft Extensions library, wraps useful functionality into interfaces that are easy to use.

DirectCraft's "resource" framework is used by the Evidyon game editor to store game files.  Using this library is a big reason that the editor was fairly straightforward to develop, even though it has a ton of different objects that all need to be serialized.  It gets really tedious to write serialization/loading code for every single member of every class--this was the primary inspiration for the DC library.

The definition of a WavSound is simply:

```
class WAVSound : public dc::dcResource<WAVSound> {
public:
static std::string staticTypeName() { return "WAVSound"; }
public:
WAVSound();
bool compile(Sound* sound);
void setSourceFile(const std::string& source_file);
private:
dc::dcFileName source_file_; // this is a DirectCraft resource type
};
```

With a single line of code in the constructor to define source_file_ as a member of the class, WAVSound is now a class that can be serialized and inflated without me having to write any of the code that actually does that.  While a serialization helper is not particularly unique, storing the whole hierarchy of all objects is extremely useful.

In the game editor, you'll notice that every object has a context menu.  DirectCraft is also responsible for generating that menu; after defining a class in this way,  DirectCraft's `dcResource<>` template class references a static global variable unique to this class, so WAVSound is forced to resolve an action list specific to its own type.  This is how the WAVSound can get a different action list from, say, the Map class--or any other class.

Finally, DirectCraft is also able to save references (pointers, basically) between classes.  Resources are all related hierarchically from one root resource, so there is a dcReference class that allows one class to contain a pointer to another class.  The pointer is automatically serialized just like any other DirectCraft object.

To check out how DC is used in practice, look at the editor's `CompleteEditor` class (completeeditor.cpp & .h) and any file under the `/shared/.../tools/` folder.