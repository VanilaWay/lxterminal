### Based on 0.4.0-1 from Debian 11, i just clean-up right-click menu, no more patches

# LXTerminal

LXTerminal is a VTE-based terminal emulator with support for multiple tabs.  It
is completely desktop-independent and does not have any unnecessary
dependencies. In order to reduce memory usage and increase the performance all
instances of the terminal are sharing a single process.

### How to repeat:

```
sudo apt install devscripts --no-install-recommends
apt source lxterminal
apt build-dep lxterminal
cd lxterminal

your-favorite-text-editor ./src/lxterminal.c
```
rename any string that you want

and build:
```
dch -l local '99.build6'
dpkg-source --commit
debuild -us -uc

sudo dpkg -i ../lxterminal_*local*.deb
```

Yes, you shuldn't trust random guy from the internet
