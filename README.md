# net2o-snap

net2o as a Snap package.

## From snapstore

```
$ snap search net2o
Name   Version         Publisher  Notes  Summary
net2o  0.9.7-20200224  forthy     -      net2o snap

$ snap info net2o
name:      net2o
summary:   net2o snap
publisher: Bernd Paysan (forthy)
store-url: https://snapcraft.io/net2o
contact:   bernd@net2o.de
license:   AGPL-3.0+
description: |
  This is the weekly development snapshot of net2o in snap format.
snap-id: YDwsyKosAdepTnlQstILtoDq3LPpSVVV
channels:
  stable:    0.9.7-20200224 2020-02-25 (2) 72MB -
  candidate: ↑
  beta:      ↑
  edge:      ↑
```

## Run net2o

Install the snap with sudo

```
$ sudo snap install net2o
net2o 0.9.7-20200224 from Bernd Paysan (forthy) installed

$ snap list
Name             Version         Rev   Tracking  Publisher   Notes
core18           20200124        1668  stable    canonical✓  base
net2o            0.9.7-20200224  2     stable    forthy      -
```

net2o needs the netlink connector, which is not auto-connecting, i.e. you need
to do that manually.

```
$ sudo snap connect net2o:netlink-connector :netlink-connector
$ snap connections
Interface          Plug                     Slot                Notes
home               net2o:home               :home               -
netlink-connector  net2o:netlink-connector  :netlink-connector  manual
network            net2o:network            :network            -
opengl             net2o:opengl             :opengl             -
unity7             net2o:unity7             :unity7             -
x11                net2o:x11                :x11                -
```

Tested with Ubuntu 18.04 (bionic).

```
$ /snap/bin/net2o.n2o gui 
```

This snap has the right to access the network and the files within HOME.

## Building

you'll have to be me for that ;). If you want to build you own version,
make sure to replace the string forthy with your name.

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
