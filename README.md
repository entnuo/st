### Simple Terminal with patches applied (using [st-flexipatch](https://github.com/bakkeby/st-flexipatch) by [bakkeby](https://github.com/bakkeby); Thank you very much bakkeby.)

#### Patches applied (20 total):

- Blinking cursor
- Bold is not bright
- Boxdraw
- Clipboard
- Columns
- Dynamic cursor colour
- External pipe
- External pipe in
- Fix keyboard input
- Font 2
- Keyboard select
- Open copied
- Open URL on click
- Right click to plumb
- Scrollback
- Scrollback mouse
- Scrollback mouse altscreen
- Sixel
- Universal scroll
- Vertcenter

#### St crashes when rendering emojis:

In `config.def.h` Noto Color Emoji font is setted as a fallback font in case you need emojis. If st crashes, you might have an outdated version of `libXft` as noted in [FAQ](https://git.suckless.org/st/file/FAQ.html#l252). Make sure you have at least version `2.3.5`.

If your distro's repository have an outdated version, you'll have to compile from source, here's how to:

First, `libXft` need some dependencies, let's compile them as well:

- FreeType
    1. You can access its releases in [freetype.org](https://freetype.org/).
    2. Download the latest release, extract it and cd into it.
    3. Then run `./autogen.sh && make && sudo make install`. \*
- Fontconfig
    1. Releases are available in [fontconfig.org](http://fontconfig.org/release).
    2. Download the latest release, extract it and cd into it.
    3. Then run `./configure && make && sudo make install`. \*
- libX11, libXext, & libXrender:
    - These you probably already have them installed. If not, use your package manager to do so.

Then finally for `libXft`:

 1. Clone its repository with `git clone https://gitlab.freedesktop.org/xorg/lib/libxft`. Cd into it after finishing.
 2. Run `./autogen.sh && make && sudo make install`.
 3. Done :)

\*You might be prompt with an error saying you're missing a dependency; search in your distro repository and install it.
