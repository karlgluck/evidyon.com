---
title:  confirm() it!
date:   2010-02-13
cover:  /media/header.png
excerpt: One piece of code you'll see integrated into Evidyon in many places--and may strike you as odd--is `confirm()`.  First, an example...
---
One piece of code you'll see integrated into Evidyon in many places--and may strike you as odd--is `confirm()`.  First, an example:

```
bool isEqualToZero(int* ptr) { confirm (ptr != NULL) else return false;  return (*ptr) == 0; }
```

This code acts like an assert with a conditional expression that can be attached to it when triggered.  If the pointer is null, an assertion is triggered when in debug mode.  When in release mode, however, the app doesn't crash.  Instead, it returns false from the method.  So why not just `assert(ptr != NULL)`?

Consider this:  you have a giant program (Evidyon) with hundreds of essentially independent processes (NPCs, players) running in parallel.  There are many, many places a pointer can be null when it's not supposed to be.  If an NPC finds itself outside of the map's boundaries--which can happen for a number of reasons--then when it goes to look up its location the map manager will return NULL.  Should the entire server crash just because this one NPC went bonkers?  Probably not.  The programmer still wants to know what happened so the problem can be fixed, but keeping the game running is top priority.  The NPC can just be deleted or moved without causing any more problems.

In most cases, when an assertion fails there is some logical thing the program can do to fix or ignore the problem after reporting it.  This is why confirm() is so useful.

There is one more trick to using `confirm()`.  Sometimes you want to make sure a variable does have a certain value, then do something.  This is done in the following example:

```
void setPointerValue(int* ptr, int value) { confirm (ptr != NULL) then { *ptr = value; } }
```

The syntax makes it very clear that you want the pointer to not be null before entering the conditional block.  In this case, the code just doesn't do anything if that condition isn't met (other than logging an error).

Unlike `assert()`, `confirm()` also presents the user with the option to ignore errors on a given line any time they occur so that the program can continue.  For release mode, there is an option for `confirm()` that allows it to remain enabled, but always ignore errors--this makes any failed conditions show up in stdout and an attached debugger, but prevents prompting the user (since, for Evidyon's server app, there is not usually someone sitting there waiting for a dialog to come up).

To check out the implementation for yourself, see `./common/fracture/confirm.h` & `.cpp` in the released code.