# XWin packages: MSVC-compatible fork of MSYS2 packages

Unlike the original MINGW packages, XWin packages are built using Clang for `x86_64-pc-windows-msvc` target, meaning that their C++ name mangling is directly compatible with binaries compiled using Microsoft Visual Studio.

This repository contains package scripts for MinGW-w64 targets to build under MSYS2.


## Building

From within a [clang-xwin](https://github.com/dmikushin/clang-xwin) Docker continaer, navigate into the package folder of choice and do:

```
MSYSTEM=xwin makepkg-xwin -sCLf
```

## Documentation
See the [MSYS2 website](https://www.msys2.org/).

## Using packages
The common way to use these packages are **pre-built** binary packages from the MSYS2 MINGW64 repo (which includes the binaries, libraries, headers, man pages), and install it on your machine, and build against those packages/libraries as you are porting/writing your software.

Details about this, including information about how to find the correct package, are found in the [MSYS2 documentation](https://www.msys2.org/docs/package-management/).  
Short summary:
 
Assuming you have a properly installed MSYS2 environment, you can install the pre-built binary package by using the following command from the bash prompt:
 ```
    pacman -S ${package-name}
 ```

Please note: Not all the packages in this repository are built and accessible from the MSYS2 MINGW64 repo right away. After merging changes to the git repository it can take a few days until compiled and built packages are accessible in the repo. Also for some packages you can find older versions in the repo if you need older version, for some packages you have only the most recent version.

---------------------------------------------

As an alternative you can download or clone the package folder with the scripts to your machine and you **build it for yourself**, in whatever version you like. 

 Assuming you have a properly installed MSYS2 environment and build tools, you can build any package using the following command:
 ```
    cd ${package-name}
    MINGW_ARCH=mingw64 makepkg-mingw -sLf
 ```
 After that you can install the freshly built package(s) with the following command:
 ```
    pacman -U ${package-name}*.pkg.tar.xz
 ```

## License

This work is licensed under BSD 3-Clause "New" or "Revised" License.
A full copy of the license is provided in [LICENSE](LICENSE).
