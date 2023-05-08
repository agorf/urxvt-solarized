# urxvt-solarized

Perl extension for [rxvt-unicode][] to apply the [Solarized][] color palette
based on whether it is day (light mode) or night (dark mode) at a given
location.

[rxvt-unicode]: https://wiki.archlinux.org/title/rxvt-unicode
[Solarized]: http://ethanschoonover.com/solarized

## Setup

Create an extension directory:

    $ mkdir -p ~/.urxvt/ext

Download the extension:

    $ wget -O ~/.urxvt/ext/solarized \
        https://raw.githubusercontent.com/agorf/urxvt-solarized/master/solarized

Or clone the repository and symlink the file:

    $ git clone https://github.com/agorf/urxvt-solarized.git
    $ ln -s $PWD/urxvt-solarized/solarized ~/.urxvt/ext/solarized

Install the [DateTime::Event::Sunrise][module] Perl module used by the extension
to calculate sunrise/sunset times. For Debian:

[module]: https://metacpan.org/pod/DateTime::Event::Sunrise

    $ sudo apt install libdatetime-event-sunrise-perl

Enable it in your `~/.Xresources` or equivalent:

    URxvt.perl-ext-common:     solarized
    URxvt.keysym.Mod4-c:       perl:solarized:toggle
    URxvt.solarized.latitude:  37.9838
    URxvt.solarized.longitude: 23.7275
    URxvt.solarized.altitude:  -0.833

Things to note:

- `Super+C` can be used to temporarily switch between dark and light mode in the
  context of the current terminal
- The latitude and longitude of Athens, Greece, is used to determine sunrise and
  sunset times (necessary for the automatic switching)
- The default altitude of `-0.833` is used (can be omitted). From the
  [module][]'s documentation:
  > This is the height of the Sun at sunrise or sunset. In astronomical context,
  > the altitude or height is the angle between the Sun and the local horizon.
  > It is expressed as degrees, usually with a negative number, since the Sun is
  > below the horizon.
  > Default value is -0.833, that is when the sun's upper limb touches the
  > horizon, while taking in account the light refraction.
  > Positive altitude are allowed, in case the location is near a mountain range
  > behind which the sun rises or sets.

Now merge the changes:

    $ xrdb -merge ~/.Xresources

You are ready to use Solarized!

## Author

Based on the work of [BobuSumisu/urxvt-solarized][BobuSumisu] and
[carlhals/toggle-colorscheme][carlhals]

Automatic light (day) and dark (night) mode switching implemented by
[Angelos Orfanakos][agorf]

[agorf]: https://angelos.dev
[BobuSumisu]: https://github.com/BobuSumisu/urxvt-solarized
[carlhals]: https://github.com/carlhals/toggle-colorscheme
