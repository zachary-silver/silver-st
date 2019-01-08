# silver-st
This is my customized clone of [suckless.org](https://suckless.org)'s simple terminal implementation for Xorg.
This version of st is patched with alpha, clipboard, hidecursor, keyboardselect, and
scrollback and uses my preferred color scheme. Must be running a window compositor like
compton in order to enable transparency.

# Screen

![Screenshot](https://github.com/ZmanSilver/silver-st/blob/master/screen.png)

## Dependencies

st requires the libxft libxext and xorg-fonts-misc packages.
The font I use in my customized version is DejaVu Sans Mono from the ttf-dejavu package.

## Installation

	sudo make install

## Uninstalling

	sudo make clean uninstall
