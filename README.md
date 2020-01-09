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
- ./mach bootstrap #Choose Android non-artifact
- cat ../Mull-Build/Preferences/*.js >> mobile/android/app/mobile.js
- cp -r ../Mull-Build/Branding/divestos mobile/android/branding/
- cp ../Mull-Build/MOZCONFIG .mozconfig
- nano .mozconfig #Update paths
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
