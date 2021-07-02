Mull
==========

Overview
--------
Mull is kinda sorta Tor Browser Android, but without routing over Tor network and upstream Firefox.
It enables many features upstreamed by the Tor Uplift project through @arkenfox and @pyllyukko's user.js projects.
It was originally created as builds of the patchset from [bug 1419581](https://bugzilla.mozilla.org/show_bug.cgi?id=1419581).

[<img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png"
     alt="Get it on F-Droid"
     height="80">](https://f-droid.org/packages/us.spotco.fennec_dos/)

Deprecation Notice
------------------
Fennec (Firefox for Android) is completely deprecated and ESR 68.12 is the final version.
Fenix is the replacement and mull-fenix is available.

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
- awk -i inplace '!/docs/' python/mozboot/mozboot/android-packages.txt
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

Credits
-------
- Icon: Google/Android/AOSP, License: Apache 2.0, https://google.github.io/material-design-icons/

Notices
-------
- Mozilla Firefox is a trademark of The Mozilla Foundation
- Divested Computing Group is not affiliated with Mozilla
- Mull is not sponsored or endorsed by Mozilla
- Firefox source code is available at https://hg.mozilla.org
