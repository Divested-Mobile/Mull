Mull
==========

Overview
--------
Mull is kinda sorta Tor Browser Android, but without routing over Tor network and upstream Firefox.
It enables many features upstreamed by the Tor Uplift project through @ghacksuserjs and @pyllyukko's user.js projects.
It was originally created as builds of the patchset from [bug 1419581](https://bugzilla.mozilla.org/show_bug.cgi?id=1419581).

Deprecation Notice
------------------
Fennec (Firefox for Android) is in strict maintenance mode and only supported on the ESR68 branch.
Fenix is the future replacement, but is currently under heavy development.
Being said, Mull most likely doesn't have long to live.

Faster builds
-------------
Use of ccache is extremely recomended as it will greatly speedup future builds.
Read [here](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Build_Instructions/ccache)


Basic steps to build Mull (first build)
---------------------------------------------
- mkdir Mull && cd Mull
- git clone |THIS REPO| Mull-Build
- git clone https://github.com/mozilla/gecko-dev.git
- cd gecko-dev
- git checkout esr68
- awk -i '!/docs/' python/mozboot/mozboot/android-packages.txt
- ./mach bootstrap #Choose Android non-artifact
- cat ../Mull-Build/Preferences/*.js >> mobile/android/app/mobile.js
- cp -r ../Mull-Build/Branding/divestos mobile/android/branding/
- cp ../Mull-Build/MOZCONFIG .mozconfig
- nano .mozconfig #Update paths
- git revert --no-edit 7163fd7d989bcf114b43cba342f48639024d1141 4d64699b7d664a70793431effc2f4e054ebf9230 85ea33e04732a1cab648af06ef9fcbe90bce2b90 61544ef9f3c99d5679ce4c26a5b1ae36dc075ae9 85041c84b9fd0a5c3b392f97d577a35f3bdf0d5b 704ef886ef0af3475b3120519c61cabcb0413afe
- ./mach build && ./mach package
An apk will be outputted into obj-arm-linux-androideabi/dist/

Basic steps to clean workspace and build (future builds)
--------------------------------------------------------
- git add -A && git reset --hard
- git pull
- cat ../Mull-Build/Preferences/*.js >> mobile/android/app/mobile.js
- cp -r ../Mull-Build/Branding/divestos mobile/android/branding/
- rm -rf obj-*
- ./mach build && ./mach package
An apk will be outputted into obj-arm-linux-androideabi/dist/

TODO
----
- Default Settings
- Default Search
- Default top sites
- Further pilfer patches from Tor Browser Android
