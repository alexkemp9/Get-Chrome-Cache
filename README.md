# Get-Chrome-Cache
A PERL Script to Extract all Files Saved within the local Chrome/Chromium Cache

## *Basics*
This script file `getCC` is designed for use by any-user (no root access required) within a Terminal. It’s principal purpose is to make it easy & reliable to extract all files from the current Chrome / Chromium cache into a dir of your choice. These are mostly various image & text files. In addition to PERL, the main utilities required are BROTLI, CONVERT (part of ImageMagick-ims6.q16 suite), DD, GUNZIP & TOUCH. These are Apps are tested at program start to make sure that they are available. Also within the *Global CONSTANTS* are `$IN` & `$OUT`:–

* `$IN` : disk location for the CHROME Cache
* `$OUT` : disk location for files extracted from the CHROME Cache

A final important App is `webp-pixbuf-loader` (to install: `sudo apt install webp-pixbuf-loader`). That will add WEBP-support to imagemagick (and other GDK progs such as YAD), and that will be required for producing Thumbnails of the increasingly-common webp-image files.

## *Begin*
The following will assume that you have created a dir `~/.local/sbin` within which you store the perl-file; this is to set the script as executable for current user only:

```bash
$ chmod 0700 ~/.local/sbin/getCC
$ la ~/.local/sbin/getCC
-rwx------ 1 user user 24137 May 31 20:50 /home/user/.local/sbin/getCC
```
## *Help*
No parameters are required. However, you *do* need to check every *Global CONSTANT*, and make sure that you have created a user-accessible dir `$OUT` to catch all output. The script will begin immediately to extract ALL accessible files at launch; here is the beginning of an example obtained just now (the script counts up as each file is extracted) with `head` & `tail` after interruption (you will notice that the script creates a thumbnail for every image, and gzipped/brotlied files are zipped up):

```bash
$ ~/.local/sbin/getCC
Checking required installations … (all required apps appear to be installed just fine)
Now extract files into $OUT=/home/user/Personal/ChromeCache/Files:
Extracting #2552 of 23960 files

$ la ~/Personal/ChromeCache/Files | head
total 176372
-rw-r--r-- 1 user user   12700 May 29 18:00 00017634715d4481_0.jpg
-rw-r--r-- 1 user user   11326 May 24 11:30 00081ab7041ab087_0.webp
-rw-r--r-- 1 user user   23606 May 30 12:44 00115c17609cb04e_0.jpg
-rw-r--r-- 1 user user     529 May 25 17:44 00118c57e87322ab_0.png
-rw-r--r-- 1 user user    7519 May 25 13:26 0011fef14b5b903c_0.js
-rw-r--r-- 1 user user     573 May  2 09:25 001b6deb054b3094_0.svg
-rw-r--r-- 1 user user    3917 May 25 11:14 002d30ee645c0713_0.js
-rw-r--r-- 1 user user    1955 May 26 16:13 0030f8d4bf683e0e_0.jpg
-rw-r--r-- 1 user user   11137 May  8 22:20 003154a4a21ab035_0.js
$ la ~/Personal/ChromeCache/Files | tail
-rw-r--r-- 1 user user   14942 May 31 21:48 thumb-ffbf8448256da635_0.ico
-rw-r--r-- 1 user user     866 May 31 21:48 thumb-ffc91f940b775e13_0.webp
-rw-r--r-- 1 user user    2653 May 31 21:49 thumb-ffdbbb18cf9c63f9_0.jpg
-rw-r--r-- 1 user user    2370 May 31 21:46 thumb-ffddaf8dfe778fd2_0.jpg
-rw-r--r-- 1 user user     105 May 31 21:50 thumb-ffdeb415b9fbfcae_0.gif
-rw-r--r-- 1 user user    2621 May 31 21:41 thumb-fffa4a665856928f_0.jpg
-rw-r--r-- 1 user user    1728 May 31 21:46 thumb-fffad8b3bd269a29_0.jpg
-rw-r--r-- 1 user user    2352 May 31 21:46 thumb-fffcfe78f0154bb9_0.png
-rw-r--r-- 1 user user  151425 May 31 21:50 tls.txt
-rw-r--r-- 1 user user 1030722 May 31 21:50 yad.txt
```
… and now a full extraction sequence with timings (those errors are *normal*; your browser hides them from you in the background then — for some bizarre reason — caches the file(s) nonetheless):–

```
$ time ~/.local/sbin/getCC
Checking required installations … (all required apps appear to be installed just fine)
Now extract files into $OUT=/home/user/Personal/ChromeCache/Files:
Extracting #4489 of 23964 files'/home/user/.cache/chromium/Default/Cache/Cache_Data/c01c3521f74474f6_s': error finding end of data at /home/user/.local/sbin/getCC line:187
Extracting #5561 of 23964 filesgzip: /home/user/Personal/ChromeCache/Files/8f86a375b9f22ab8_0: unknown suffix -- ignored
Extracting #5569 of 23964 filesgzip: /home/user/Personal/ChromeCache/Files/5f4f7cf3619eb81e_0: unknown suffix -- ignored
Extracting #6447 of 23964 filesgzip: /home/user/Personal/ChromeCache/Files/e45d7840df26c3c5_0: unknown suffix -- ignored
Extracting #7755 of 23964 files'/home/user/.cache/chromium/Default/Cache/Cache_Data/2605dabe6db345f1_s': error finding end of data at /home/user/.local/sbin/getCC line:187
Extracting #13721 of 23964 filesconvert: width or height exceeds limit `/home/user/Personal/ChromeCache/Files/828312e46e6364a5_0.png' @ error/cache.c/OpenPixelCache/3909.
Extracting #14948 of 23964 filesgzip: /home/user/Personal/ChromeCache/Files/775aaee39e14bc01_0: unknown suffix -- ignored
Extracting #15165 of 23964 filesconvert: profile 'icc': 'RGB ': RGB color space not permitted on grayscale PNG `/home/user/Personal/ChromeCache/Files/thumb-8c29387e3c4140b2_0.png' @ warning/png.c/MagickPNGWarningHandler/1668.
Extracting #18635 of 23964 files'/home/user/.cache/chromium/Default/Cache/Cache_Data/f5494c459b5b4823_s': error finding end of data at /home/user/.local/sbin/getCC line:187
Extracting #19067 of 23964 filesArgument "\0\0\0\0" isn't numeric in addition (+) at /home/user/.local/sbin/getCC line 184.
'/home/user/.cache/chromium/Default/Cache/Cache_Data/index': error finding end of data at /home/user/.local/sbin/getCC line:187
Extracting #23304 of 23964 files'/home/user/.cache/chromium/Default/Cache/Cache_Data/ea8757ff56f6c660_s': error finding end of data at /home/user/.local/sbin/getCC line:187
Extracting #23782 of 23964 filesgzip: /home/user/Personal/ChromeCache/Files/c2fbaf419c83a8a8_0: unknown suffix -- ignored
Extracting #23964 of 23964 files
The extraction is now complete.

real	10m13.586s
user	4m33.216s
sys	4m47.984s
```

PS    Stat extracts have been put in place to be able to use YAD (Yet Another Dialog) and tested by me as working, then ~~I've lost that section of code. Ooops.~~ The launch code is within `browseCC`, but that code is unfinished.

## *Begin*
The following will assume that you have created a dir `~/.local/sbin` within which you store the bash-file; this is to set the script as executable for current user only:

```bash
$ chmod 0700 ~/.local/sbin/browseCC
$ la ~/.local/sbin/browseCC
-rwx------ 1 user user 10488 Apr 25 18:06 /home/user/.local/sbin/browseCC
```
It works fine, and the example of calling it is:

```bash
$ ~/.local/sbin/browseCC ~/Personal/ChromeCache
1. Checking required files … FAD: TLS:  (all required files appear installed just fine)
2. Checking required apps … 
awk: GNU Awk 5.1.0, API: 3.0 (GNU MPFR 4.1.0, GNU MP 6.2.1)
convert: Version: ImageMagick 6.9.11-60 Q16 x86_64 2021-01-25 https://imagemagick.org
fgrep: grep (GNU grep) 3.6
sed: /bin/sed (GNU sed) 4.7
sort: sort (GNU coreutils) 8.32
tput: ncurses 6.2.20201114
yad: 0.40.0 (GTK+ 3.24.24)

Display Summary of files available:
```
And here is what the YAD window looks like (swift appearance):

![yad dialog 1](https://github.com/alexkemp9/Get-Chrome-Cache/blob/main/Screenshot_2023-05-31_23-28-47.png)

Selecting one of the image files will show all thumbnails for that filetype (this takes some time to appear):

```bash
Now to load your selected filetypes from $FAD to $SUM:
Extracting #59931 lines (for 3807 files) from 59990 lines
```

What it can NOT do is extract a selected Image file from the dir to another place, nor search within text files.  Pull Requests welcomed.
