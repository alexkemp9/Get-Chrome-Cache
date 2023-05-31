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
No parameters are required. However, you *do* need to check every *Global CONSTANT*, and make sure that you have created a user-accessible dir `$OUT` to catch all output. The script will begin immediately to extract ALL accessible files; here is an example obtained just now (the script counts up as each file is extracted :

```bash
$ ~/.local/sbin/getCC
Checking required installations … (all required apps appear to be installed just fine)
Now extract files into $OUT=/home/user/Personal/ChromeCache/Files:
Extracting #2552 of 23960 files
```
