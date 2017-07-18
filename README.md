# urxvt-solarized

[Solarized](http://ethanschoonover.com/solarized) dark and light color scheme for urxvt,
including easy toggling between them.

## Setup

Create a `urxvt` extension folder:

    $ mkdir -p ~/.urxvt/ext

Download the extension:

    $ wget -O ~/.urxvt/ext/solarized \
        https://raw.githubusercontent.com/BobuSumisu/urxvt-solarized/master/solarized

Or clone repository and link the file:

    $ git clone https://github.com/BobuSumisu/urxvt-solarized.git
    $ ln -s ${PWD}/urxvt-solarized/solarized ~/.urxvt/ext/solarized

Enable it in your `~/.Xresources` or equivalent:

    URxvt.perl-ext-common:      solarized
    URxvt.keysym.Mod4-c:        perl:solarized:toggle
    URxvt.solarized.default:    light

Here we also bound toggling to `Super+C` and sat the default scheme to Solarized light.

Now merge the changes:

    $ xrdb -merge ~/.Xresources

And open a new `urxvt` windows in beautiful Solarized colors!
