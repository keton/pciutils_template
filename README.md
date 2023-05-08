# pcilib-template

A template project for using [pciutils](https://github.com/pciutils/pciutils) under Windows. Compared to current implementation it gives access to full PCIe config space without the need of putting whole OS into debug mode, which is not convenient in daily usage.

To that end it uses [DirectIO](https://github.com/allenyllee/directio) driver instead of other methods. All dependencies are bundled in single .exe via resource library.

## Building

Install Visual Studio 2022 command line tools with C++ toolchain and meson. After that standard `meson setup builddir && meson compile -C builddir` produces the .exe.

## Debugging

Usage of directio driver requires Administrator privileges. Executable itself has correct manifest to trigger UAC. However in order for debugging to work you need to run VSCode as admin.

## Word about security

For the time between opening and closing pciilib handle DirectIO installs system driver. This driver allows any user to peek/poke i386 ports. This is not optimal for security. __If you are not ok with that don't use it.__ 

Normally it would be trivial to fix but with the price of EV Authenticode certificate and recent requirement that it should be kept in FIPS compliant key storage device cost of signing resulting driver binary is out of scope for this project.
