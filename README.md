# j4-dmenu-desktop

j4-dmenu-desktop is a replacement for i3-dmenu-desktop. It's purpose is to find .desktop files
and offer you a menu to start an application using dmenu.

## Build requirements

* Compiler with basic C++11 support (GCC 4.6 is probably just fine)
* CMake

Building is the usual cmake/make thingy:

    cmake .
    make
    sudo make install

## Invocation

If you specifify arguments to j4-dmenu they will be concatenated and used as the
command to start dmenu.

    j4-dmenu-desktop

would use `dmenu` executed with your standard shell (`$SHELL` if set, `/bin/sh` otherwise)
to start dmenu.

    j4-dmenu-desktop --dmenu="dmenu -fn 'DejaVu Sans-10' -l 20"

would start dmenu with the -fn and -l arguments to create a vertical menu.

### Options

* --dmenu [command] or -d [command], default is "dmenu -i" (-i for case insensitive matching)


## FAQ

### Case insensitivity?

Add the `-i` option to the dmenu command

### How much faster is it?

    % time i3-dmenu-desktop --dmenu="cat"
    [{"success":true}]
    i3-dmenu-desktop --dmenu="cat"  0.37s user 0.02s system 96% cpu 0.404 total
    % time ./j4-dmenu-desktop --dmenu=cat
    [{"success":true}]
    ./j4-dmenu-desktop --dmenu=cat  0.01s user 0.00s system 95% cpu 0.017 total

More than twenty times faster :)

