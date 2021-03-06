picopt
======

A multi-format, recursive, multiprocessor aware, command line image optimizer utility that uses external tools to do the optimizing.

Picopt depends on Python [PIL](http://www.pythonware.com/products/pil/) to identify files and [rarfile](https://pypi.python.org/pypi/rarfile) to open CBRs.

To optimize JPEG images. Picopt needs either [jpegrescan](https://github.com/kud/jpegrescan) or [jpegtran](http://jpegclub.org/jpegtran/) on the path. jpegrescan is preferred.

To optimize lossless images like PNG, PNM, GIF, TIFF and BMP, picopt requires either [optipng](http://optipng.sourceforge.net/), [advpng](http://advancemame.sourceforge.net/doc-advpng.html) or [pngout](http://advsys.net/ken/utils.htm) be on the path. Optipng provides the most advantage, but best results are acheived by using pngout as well. Advpng support is disabled by default and must be explicitly enabled on the command line.

Animated GIFs are optimized with [gifsicle](http://www.lcdf.org/gifsicle/) if it is available. Picopt may also nag you to use [HTML5 video](http://gfycat.com/about) instead.

Picopt uncompresses, optimizes and rezips [comic book archive files](https://en.wikipedia.org/wiki/Comic_book_archive). Be aware that CBR rar archives will be rezipped into CBZs instead of CBR. Comic book archive optimization is off by defualt.

Picopt allows you to drop picopt timestamps at the root of your recursive optimization trees so you don't have to remember which files to optimize or when you last optimized them.

Installation
------------

### Lossless external program packages
#### OS X
    brew install optipng pngout jpeg gifsicle

#### Debian / Ubuntu
    apt-get install optipng pngout libjpeg-progs gifsicle python-imaging

#### Redhat / Fedora
    yum install optipng pngout libjpeg-progs gifsicle python-imaging

### jpegrescan
jpegrescan is a better jpeg optimizer than jpegtran, unfortunately it
remains unpackaged :(

    git clone git@github.com:kud/jpegrescan.git
    ln -s jpegrescan/jpegrescan /usr/local/bin/jpegrescan

### Picopt
    pip install picopt

Usage
-----
Optimize all JPEG files in a dirctory:

    picopt *.jpg

Optimize all files and recurse directories:

    picotpt -r *

Optimize files and recurse directories AND optimize comic book archives:

    picopt -rc *

Optimize files, but not lossless files:

    picopt -OPG *

Optimize files, but not jpegs:

    picopt -JT *

Optimize files, but not animated gifs:

    picopt -G *

Just list files picopt.py would try to optimize:

    picopt -l *

Optimize everything in my iPhoto library, but only after the last time i did this, skipping symlinks to avoid massive amounts of duplicate work. Don't convert lossless files to PNGs because that would confuse iPhoto. Also drop a timestamp file so I don't have to remember the last time I did this:

    picopt -rSYt -D '2013 June 1 14:00' 'Pictures/iPhoto Library'

Packaged For
------------

* [PyPI](https://pypi.python.org/pypi/picopt/)
* [Arch Linux](https://aur.archlinux.org/packages/picopt/)


Alternatives
------------

[Imageoptim](http://imageoptim.com/) is an all-in-one OS X GUI optimizer. Imageoptim command line usage is possible with [an external program](https://code.google.com/p/imageoptim/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Type%20Status%20Priority%20Milestone%20Owner%20Summary%20Stars&groupby=&sort=&id=39).
