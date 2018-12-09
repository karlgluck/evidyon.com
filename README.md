To generate the `_site` directory that gets uploaded to S3, go on Mac and use:

```
bundle exec jekyll serve
```

To upload to the live website, use `s3cmd`:

```
bundle exec jekyll build
~/Downloads/Tools/s3cmd/s3cmd sync ./_site/ --delete-removed --add-header='Cache-Control: public, max-age=86400' s3://evidyon.com
```

Check out `jekyll.org` for more.
