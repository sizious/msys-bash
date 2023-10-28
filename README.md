# GNU Bash for MSYS (msys-bash)

This repository contains the unofficial **GNU Bash (bash) 3.1.23-2** release
for **MinGW/MSYS**. This package is intended to be used on **MSYS** only, and
was created to replace the bugged **3.1.23-1** which is the only one
officially provided in the **MinGW/MSYS** repository.

Indeed, while trying to create a [heredoc](https://en.wikipedia.org/wiki/Here_document),
you may have the following issue on some Windows 10/11 editions (tested on
Windows 10 Home 22H2):

```
bash: cannot create temp file for here document: Permission denied
```

This issue was identified in the past by the [Cygwin](https://www.cygwin.com/)
team but for some reason, the fix was removed by the
[MinGW](https://osdn.net/projects/mingw/) team. This patch restore this.

**Note:** the temporary files created by the heredoc creation process are not
removed from the `%TEMP%` directory, due to a `Permission denied` (`Errno 13`)
issue - this could be explained as in *nix system, it's allowed to unlink a file
even if you have opened it, which isn't the case on Windows.

## Installation

1. Download the `bash-3.1.23-2-msys-1.0.19-bin.tar.xz`.
2. Extract the package file in your `%MINGW_ROOT%\msys\1.0\` directory, where
   `%MINGW_ROOT%` is the **MinGW** installation directory (typically `C:\MinGW`).

## Compile

If you want to recompile this source, you will need to have a working 
[MSYS Toolchain](http://www.mingw.org/wiki/HOWTO_Create_an_MSYS_Build_Environment).
Then, follow the instructions in the `src/msys-bash.RELEASE_NOTES` file.
