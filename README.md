# The YCM Extra Configuration

## Introduction

[YouCompleteMe][1] (most often abbreviated as ‘YCM’) is a revolutionary
Vim plugin, but its configuration is a bit … elusive. Luckily I have
found [l3nkz/ycmconf][2], which makes my life much easier, especially
because I use [CMake][3] and [clang_complete][4] too. With this plugin,
the CMake output or a *.clang_complete* file will suffice (I prefer the
latter), and I do not need to put any *.ycm_extra_conf.py* files in my
code projects any longer. I also do not need to click on the YCM
confirmation prompt every time, or configure which *.ycm_extra_conf.py*
files should be considered secure in my *.vimrc*.

The major problem of l3nkz/ycmconf was that it had not been updated
since April 2015, and it stopped working with the latest clangd-based
YCM. However, fixing it proved not difficult. I have made it work again
(with both an old version and the most recent version of YCM) after
making only minor changes. And the result is here.

## Installation

### Manual installation on Vim 8+

Do something like (commands and directories may require changes under
Windows):

```bash
mkdir -p ~/.vim/pack/my/start
cd ~/.vim/pack/my/start
git clone https://github.com/adah1972/ycmconf.git
```

### With minpac

Add the following line to your *.vimrc* (or *\_vimrc* under Windows),
after other `minpac#add` statements:

```vim
call minpac#add('adah1972/ycmconf')
```

If you have defined the `PackUpdate` command, it is now the time to
execute it. Otherwise, manually restart Vim and execute
`call minpac#update()`.

### With Vundle

Add the following line to your *.vimrc* (or *\_vimrc* under Windows),
after other `Plugin` statements:

```vim
Plugin 'adah1972/ycmconf'
```

Then restart Vim and run `:PluginInstall`.

## Configuration

Do one of the following:

- Put a *compile_commands.json* file (output by a
  `set(CMAKE_EXPORT_COMPILE_COMMANDS 1)` line in *CMakeLists.txt*) in
  the source code directory, or one of its parent directories.
- Put a *.clang_complete* file in the source directory, or one of its
  parent directories.

The first method is more precise, but it does not work if the code
directories are shared (absolute paths are used in
*compile_commands.json*).

A sample *.clang_complete* file can be found in [geek_time_cpp][5]. It
is quite trivial to maintain.

[1]: https://github.com/Valloric/YouCompleteMe
[2]: https://github.com/l3nkz/ycmconf
[3]: https://cmake.org
[4]: https://github.com/xavierd/clang_complete
[5]: https://github.com/adah1972/geek_time_cpp/blob/master/.clang_complete
