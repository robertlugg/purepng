README for PurePNG
scondo@mail.ru


INTRODUCTION

PurePNG provides Python code for encoding/decoding PNG files.  In
particular png.py is a Python module written entirely in Python.


PurePNG home page: http://github.com/scondo/purepng/
PurePNG documentation: http://purepng.readthedocs.org/en/latest/

QUICK START

    import png
    png.from_array([[255, 0, 0, 255],
                    [0, 255, 255, 0]], 'L').save("small_smiley.png")

After that, try "import png" then "help(png)".


INSTALLATION

PurePNG requires Python version 2.3 (and that's all), or any compatible
higher version(incl. Python 3).  It works best on Python 2.4 and above. 

PurePNG comes with a setup.py script to use with distutils.  After
unpacking the distribution, cd into the directory and execute the
command:

python setup.py install

The png module will be installed; "import png" will allow you to use it
from your Python programs.

Alternatively, you can copy code/png/png.py wherever you like.
It's intended that you can copy png.py into your application and distribute
it. The following "curl" command should copy the latest version into your
current directory:

curl -O https://raw.github.com/scondo/purepng/master/code/png.py


MIGRATION FROM PYPNG

PurePNG is successor of PyPNG - nice and simple module to work with png.

If you work with PyPNG in most cases you can use PurePNG as drop-in replace,
but few things are changed:

* Rows in boxed flat row now may be any buffer-compatible, not only array.
  Use str(buffer(row)) instead of 'tostring' method or memoryview(row).
  
* Python 2.2 support removed. Too much important features (like deinterlace)
  fails on Python 2.2. Now all version should pass all tests.
  
* Work with Netpbm images using only copied 'png.py' deprecated. (will be removed soon)


RELEASE NOTES

PurePNG 0.1.0 Initial rework led to fork.

Reworked Cython concept.
Add optional filtering on save.
Module/package duality
Python 2/3 polyglot (and partitial Cython)
Using bytearray when possible.

(For issues see https://github.com/scondo/purepng/issues?state=open )

PyPNG release history:
Release 0.0.16

Compatible with nose: `nosetests png.py` now works.

Allow any "file-like" object as an input.

Handle newlines in texttopng.


Release 0.0.15

Fixed various URLs to point at github.com instead of googlecode.


Release 0.0.14

When using png.py as a command line tool, it can now produce
non-square test images.

PyPNG now installs "out of the box" on Python 3 on a plain install
(previously distribute or pip was required).

PyPNG welcomes the following community contributions:

  Joaquín Cuenca Abela speeds up PNG reading when Cython is available.

  Josh Bleecher Snyder adds a lenient mode which has relaxed checksum
  checking.

  nathan@dunfield.info fixed a problem writing files when using
  the command line tool on Windows (Issue 62).

The following issues have been fixed:

  On github:

  Issue 6: Palette processing is annoying

  On googlecode:

  Issue 62: Problem writing PNG files on Windows

Development has moved from googlecode to github.  All issues below here,
and the one immediately above, are from the googlecode issue tracker.
All newer issue should be on github.


Release 0.0.13

PyPNG now installs "out of the box" on Python 3.  Thanks to
simon.sapin@kozea.fr and nathan@dunfield.info for the patch.

The following issues have been fixed:

  Issue 63: setup.py does not use 2to3
  Issue 64: Typo in documentation


Release 0.0.12

PyPNG now works on Python 3 if you use the 2to3 tool.  Fix for
converting grey images to RGBA.

The following issues have been fixed:

  Issue 60: Greyscale images not properly being converted to RGBA
  Issue 61: Doesn't work on Python 3


Release 0.0.11

Added the "How Fast is PyPNG" section to the documentation.  Changed it
so that more PNG formats return their rows as Python array.array
instances.


Release 0.0.10

Fix for read_flat method (broken for ages).

The following issues have been fixed:

  Issue 56:  read_flat broken


Release 0.0.9

Tentative fix for a deprecation warning on 64-bit Python 2.5 systems.
Conversion tool for Plan 9 images.

Issue 54 (below) is tentative.  The PyPNG developers have been unable to
reproduce the error (as it seems to be on 64-bit Python 2.5 systems);
any user reports would be most welcome.

The following issues have been fixed:

  Issue 54:  Deprecation warnings when using pypng.
  Issue 55:  Cannot convert Plan 9 images.


Release 0.0.8

Mostly more robust to dodgy input PNGs, as a result of testing with
brokensuite.  One fixed bug was a critical: an infinite loop for a least
one input (Issue 52 below).

The following issues have been fixed:

  Issue 47:  Leading blanks when using write_packed.
  Issue 48:  pipdither fails when input has no gamma chunk.
  Issue 49:  pipdither fail with 1-bit input.
  Issue 50:  pipchunk adds second gamma chunk.
  Issue 51:  piprgb and pipasgrey fail for color mapped images.
  Issue 52:  Some inputs cause infinite loop.

Release 0.0.7

Better documentation (in html/ex.html mostly) for NumPy integration.

The following issues have been fixed:

  Issue 46:  Unclear how to get PNG pixel data into and out of NumPy.

Release 0.0.6

NumPy integer types now work.

The following issues have been fixed:

  Issue 44:  Cannot use numpy.uint16 for pixel values.

Release 0.0.5

sBIT chunks are now handled, meaning that PyPNG can handle any (single)
bit depth from 1 to 16 from end to end.

The following issues have been fixed:

  Issue 28:  Does not add sBIT chunk.
  Issue 36:  Ignores sBIT chunk when present.

Release 0.0.4

PyPNG now works on Python 2.2 (significant for Symbian users as PyS60 is
based on Python 2.2).  Not all features are supported on Python 2.2.

The following issues have been fixed:

  Issue 16:  Source and doc uses 'K' where it should use 'L'.
  Issue 32:  Does not accept packed data.
  Issue 33:  Cannot create greyscale PNG with transparency.
  Issue 35:  Does not work on Python 2.2.

Release 0.0.3

Handling PAM files allows end to end handling of alpha channels in
workflows that involve both Netpbm formats and PNG.  PyPNG now works in
Python 2.3.

The following issues have been fixed:

  Issue 14:  Does not read PAM files.
  Issue 15:  Does not write PAM files.
  Issue 25:  Incorrect handling of tRNS chunk.
  Issue 26:  asRGBA8 method crashes out for color type 2 images.
  Issue 27:  Fails on Python 2.3.

Release 0.0.2

Lickable HTML documentation is now provided (see the html/ directory),
generated by Sphinx.

The following issues have been fixed:

  Issue 8:  Documentation is not lickable.
  Issue 9:  Advantage over PIL is not clear.
  Issue 19: Bogus message for PNM inputs with unsupported maxval
  Issue 20: Cannot write large PNG files

Release 0.0.1

Stuff happened.


MANIFEST

.../ - top-level crud (like this README, and setup.py).
.../code/ - the Python code.
.../html/ - lickable manuals (generated).
.../man/ - manuals (in source/plain-text).
.../proc/ - documented procedures (release procedure).


REFERENCES

Python: www.python.org
PNG: http://www.w3.org/TR/PNG/
