# Binary blobs

I needed a place to put binary blobs, and this was easier than the song-and-dance for doing it from a desktop into a gist.


### bench-trimmed.zip
`bench-trimmed.zip` is collection of benchmark results for use with `benchseries`,
a [not-yet-checked-in extension](https://go-review.googlesource.com/c/perf/+/218923) to golang.org/x/perf/cmd.
To use:
```
unzip bench-trimmed.zip
cd bench
shopt -s extglob
benchseries -png ../png -series bentstamp -last ns-per-op,build-user-ns-per-op Go*-opt.* !(Go)*-opt.*
```
This should produce output along the lines of
```
ns/op:: ValidateVersionTildeFail-12:-4.9%, GM:+0.8%, BaseTest2KB-12:+40%
build-user-ns/op:: Commonmark_markdown:-5.8%, GM:-0.05%, Ajstarks_deck_generate:+4.3%
```
as well as populating the sibling `png` directory with a bunch of graphs.
