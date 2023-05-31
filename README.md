# Get-Chrome-Cache
A PERL Script to Extract all Files Saved within the local Chrome/Chromium Cache

## *Basics*
This script file is designed for use by any-user (no root access required) within a Terminal. It’s principal purpose is to make it easy & reliable to extract all files from the current Chrome / Chromium cache into a dir of your choice. These are mostly various image & text files. In addition to PERL, the main utilities required are BROTLI, CONVERT (part of ImageMagick-ims6.q16 suite), DD, GUNZIP & TOUCH. These are Apps are tested at program start to make sure that they are available. Also within the *Global CONSTANTS* are `$IN` & `$OUT`:–

* `$IN` : disk location for the CHROME Cache
* `$OUT` : disk location for files extracted from the CHROME Cache

## *Begin*
The following will assume that you have created a dir `~/.local/sbin` within which you store the bash-file; this is to set the script as executable for current user only:

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
