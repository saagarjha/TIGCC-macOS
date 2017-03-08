# TIGCC-macOS
[TIGCC](http://tigcc.ticalc.org) (and goodies like [tixcode](http://www.ticalc.org/archives/files/fileinfo/330/33001.html)) modified and compiled for macOS, so you don't have to do it yourself.

Note: I did not write TIGCC, or have anything to do with its development. I'm just an ordinary user trying to get it to work on my computer.

## Usage
Download the repository and move it to wherever you like (for example, `/usr/local/tigcc`). Make sure to set `TIGCC` in your `.bash_profile` (or equivalent):
```shell
export TIGCC=/usr/local/tigcc # or wherever you copied the files to
```
and add TIGCC and its related tools to your `PATH` if you so desire:
```shell
export PATH="$PATH:$TIGCC/bin"
```

## Compiling TIGCC yourself
Download the source code for TIGCC for Linux and Unix from [here](http://tigcc.ticalc.org/linux/) ([direct link](http://tigcc.ticalc.org/linux/tigcc_src.tar.bz2)) and read through the OS X install instructions, downloading GCC and Binutils as required. A few of the many caveats required to build it:
* The installation scripts require GNU Coreutils. If you're using Homebrew, install them, then go through all the scripts (in `scripts/`) and prefix all the Coreutils commands (`cp`, `mkdir`, `rm`, etc.) with "g".
* The sources will fail to compile with Clang. Install GCC (I used `apple-gcc42` from `homebrew/dupes/apple-gcc42`), and use this hack to make sure the install scripts use it:
```shell
$ sudo mv /usr/bin/gcc /usr/bin/gcc.bak # This is actually Clang
$ sudo ln -s "$(which gcc-4.2)" /usr/bin/gcc # "Move" our GCC
# Restore the original "GCC" once TIGCC is installed
$ sudo rm /usr/bin/gcc
$ sudo mv /usr/bin/gcc.bak /usr/bin/gcc
```
* If the install fails, delete everything and go through the install steps one by one (use `scripts/Install_step_1`, etc.) to figure out where it failed.

If I missed anything (which I probably did, since this took a lot of effort to build) please let me know and I'll add it.
