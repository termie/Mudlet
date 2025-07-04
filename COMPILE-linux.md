# Compiling on Linux

Mudlet tries to maintain wide and long-lived build support but instructions
will be for fairly recent versions of operating systems with older information
in the archives >>LINK<<.

## Understanding the build

We hope everything works right the first time, but if not you should know
some things outline below.

Mudlet:
 - is a [Qt6](https://doc.qt.io/qt-6/) application with a few remaining
   Qt5 components.
 - provides a [Lua 5.1](https://www.lua.org/manual/5.1/) environment including
   - [luautf8](https://luarocks.org/modules/xavier-wang/luautf8) for UTF8
   - [luafilesystem](https://luarocks.org/modules/hisham/luafilesystem) for
     interacting with the filesystem
   - [lrexlib-pcre](https://luarocks.org/modules/rrt/lrexlib-pcre) to support
     PCRE regex
   - [luasql-sqlite3](https://lunarmodules.github.io/luasql/) for on-disk
     database support
   - [lua-yajl](https://luarocks.org/modules/brimworks/lua-yajl) for parsing
     yaml and json
   - [luazip](https://luarocks.org/modules/mpeterv/luazip) to read files
     stored inside zip files
 - includes some significant third party libraries:
   - [communi](https://communi.github.io/doc/3.7/) for irc connectivity
   - [dblsqd](https://github.com/Mudlet/dblsqd-sdk-qt) (optional) for managing
     auto-updates
   - [discord](https://github.com/discord/discord-rpc) (optional) for
     integration with the discord client
   - [edbee](https://www.edbee.net/) for the code editor
   - [lcf](https://github.com/martin-eden/lua_code_formatter) for making the
     the lua in triggers and scripts valid
   - [qtkeychain](https://github.com/frankosterfeld/qtkeychain) (optional)
     for storing passwords and secrets using your system keychains
   - [vcpkg](https://github.com/microsoft/vcpkg) to provide additional
     development tools 
 - supports multiple translations
 - supports screen reader interfaces
 - supports multimedia and 3d rendering

Mudlet's build:
 - uses [CMake](https://cmake.org/cmake/help/latest/) > 3.5, 4+ is current, for
   generating the build
 - uses [git](https://git-scm.com/doc) for some dependency handling
 - probably uses [ninja](https://ninja-build.org/) for the build, instructions
   for various IDEs available >>LINK<<

Mudlet's build instructions:
 - depend on libraries provided by [luarocks](https://luarocks.org/) 
 - depend on your system package manager (apt, dnf, pacman)
 - can be run via [docker](https://docs.docker.com/get-started/get-docker/) for
   increased isolation and reproducibility
 - work on quite a few flavors of operating system, hopefully this information
   helps sort out any of the ones not covered


## Dependencies: system

### Arch

### ChromeOS

### Debian

### Fedora

### Ubuntu

apt-based big list to test on Ubuntu, Debian, ChromeOS (no way to test)
```
sudo apt install 
# build tools
  build-essential
  ccache
  cmake
  git
  ninja-build
  ubuntu-restricted-extras

#  core deps
  libboost-all-dev
  libboost-dev
  libglib2.0-dev
  libhunspell-dev
  libpcre3-dev
  libpugixml-dev
  libpulse-dev
  libyajl-dev
  libzip-dev
  zlib1g-dev

# graphics, audio, multimedia, security
  libglu1-mesa-dev
  libgstreamer1.0-dev
  libsecret-1-dev
  mesa-common-dev

# qt6 / qt5
  libqt5opengl5-dev
  libqt6core5compat6
  libqt6core5compat6-dev
  qt6-l10n-tools
  qt6-multimedia-dev
  qt6-speech-dev
  qt6-tools-dev
  qt6-tools-dev-tools
  qtkeychain-qt6-dev
  qtmultimedia5-dev
  qttools5-dev

# lua
  liblua5.1.0-dev
  lua5.1
  luarocks


```

  ubuntu-restricted-extras qtcreator build-essential git zlib1g-dev libhunspell-dev \
  libpcre3-dev libzip-dev libboost-dev libboost-all-dev libyajl-dev libpulse-dev libpugixml-dev \
  liblua5.1-0-dev lua-filesystem lua-zip lua-sql-sqlite3 luarocks ccache lua5.1 libsecret-1-dev \
  libglu1-mesa-dev mesa-common-dev libglib2.0-dev libgstreamer1.0-dev libqt5opengl5-dev cmake \
  qt6-multimedia-dev libqt6core5compat6 qt6-tools-dev qtkeychain-qt6-dev qt6-l10n-tools ninja-build \
  qt6-tools-dev-tools libqt6core5compat6-dev qttools5-dev qtmultimedia5-dev qt6-speech-dev


## Dependencies: luarocks

Luarocks was installed above, they have [helpful documentation](https://github.com/luarocks/luarocks/blob/main/docs/using_luarocks.md).

You may have multiple versions of Lua on your system, but Mudlet uses Lua 5.1
and we'll be specifying that version whenever we interact with `luarocks`.

We'll be preferring luarocks installations of lua packages over the system
package manager,
