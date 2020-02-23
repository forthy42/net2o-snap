# gforth-snap

Gforth as a Snap package.

## From snapstore

```
$ snap search gforth
Name           Version         Publisher  Notes  Summary
gforth-forthy  0.7.9-20200220  forthy     -      Gforth development snap
gforth-mtrute  0.7.9-20190627  mtrute     -      gforth snap

$ snap info gforth-forthy
name:      gforth-forthy
summary:   gforth snap
publisher: –
store-url: https://snapcraft.io/gforth-forthy
license:   GPL-3.0+
description: |
  This is the weekly development snapshot of Gforth in snap format. Building
  for snap has made considerable progress, all SWIG-generated libraries load,
  OpenGL via GLX works.
commands:
  - gforth-forthy.gforth
  - gforth-forthy.gforth-ditc
  - gforth-forthy.gforth-fast
  - gforth-forthy.gforth-itc
refresh-date: today at 22:46 CET
channels:
  stable:    0.7.9-20200220 2020-02-23   (3) 56MB -
  candidate: ↑
  beta:      ↑
  edge:      ↑
```

## Run gforth

  Install the snap with sudo

```
$ sudo snap install gforth-forthy
gforth-forthy 0.7.9-20200220 from Bernd Paysan (forthy) installed

$ snap list
Name             Version         Rev   Tracking  Publisher   Notes
core18           20200124        1668  stable    canonical✓  base
gforth-forthy    0.7.9-20200220  4     stable    forthy      -
```

Tested with Ubuntu 18.04 (bionic).

```
$ /snap/bin/gforth-forthy.gforth 
Gforth 0.7.9_20200220
Authors: Anton Ertl, Bernd Paysan, Jens Wilke et al., for more type `authors'
Copyright © 2019 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
Gforth comes with ABSOLUTELY NO WARRANTY; for details type `license'
Type `help' for basic help
bye 
$
```

This snap has the right to access the network and the files within HOME.

## Building

you'll have to be me for that ;). If you want to build you own version,
make sure to replace the string mtrute with your name.

```
$ snapcraft status gforth-forthy
Track    Arch    Channel    Version         Revision
latest   amd64   stable     0.7.9-20200220  4
                 candidate  ^               ^
                 beta       ^               ^
                 edge       ^               ^
```

I run snapcraft in the project directory while being logged in.

```
  $ snap whoami 
  E-Mail: m_trute@yahoo.de
  $ snapcraft 
  Using 'snapcraft.yaml': Project assets will be searched for from the 'snap' directory.
  Launching a VM.
  Launched: snapcraft-gforth-mtrute                                                      
  2019-05-02T15:46:56Z INFO Waiting for restart...
  core 16-2.38.1 from Canonical✓ installed
  snapcraft 3.4 from Canonical✓ installed
  core18 20190409 from Canonical✓ installed

  ...

  ============= INSTALL SUCCEEDED =============
  Bash users: type 'hash -r' to empty the cache
  Staging gforth 
  Priming gforth 
  Snapping 'gforth-mtrute' \                                              
  Snapped gforth-mtrute_0.7.9-20190501_amd64.snap
  $ snapcraft push --release=edge gforth-mtrute_0.7.9-20190501_amd64.snap
  Preparing to push 'gforth-mtrute_0.7.9-20190501_amd64.snap'.
  After pushing, an attempt will be made to release to 'edge'
  Pushing 'gforth-mtrute_0.7.9-20190501_amd64.snap' [=======================] 100%
  Processing...|                                                                  
  Ready to release!
  Revision 1 of 'gforth-mtrute' created.
  Track    Arch    Channel    Version         Revision
  latest   amd64   stable     -               -
                   candidate  -               -
                   beta       -               -
                   edge       0.7.9-20190501  1
  The 'edge' channel is now open.
  $
```

The revision number increases with every snapcraft upload, so expect higer
numbers. 
