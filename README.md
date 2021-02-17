CPUMiner-Multi(1.3.5) in Raspberry Pi
==============

[![Build Status](https://travis-ci.org/tpruvot/cpuminer-multi.svg)](https://travis-ci.org/tpruvot/cpuminer-multi)

This is a multi-threaded CPU miner,
owners [pooler](//github.com/pooler)'s and [tpruvot](//github.com/tpruvot)'s cpuminer (see AUTHORS for list of contributors).

#### Table of contents

* [How to build in Raspberry Pi 3/4](#How-to-build-in-Raspberry-Pi-3/4)
* [Algorithms](#algorithms)
* [Dependencies](#dependencies)
* [Usage instructions](#usage-instructions)
* [Donations](#donations)
* [Credits](#credits)
* [License](#license)

# How to build in Raspberry Pi 3/4

#### it's very simple !

```
sudo apt-get install automake autoconf pkg-config libcurl4-openssl-dev libjansson-dev libssl-dev libgmp-dev zlib1g-dev make g++ git
```

Clone with `git clone https://github.com/tpruvot/cpuminer-multi.git`

```
 cd cpuminer-multi
 git checkout tags/v1.3.5-multi
 ./build.sh
```

#### command for tests:
```
sudo ./cpuminer -a yescrypt -o stratum+tcp://yescrypt.na.mine.zpool.ca:6233 -u DR7Pu6htPLtfq1kJHpEWgCp3qMUHStFRu5 -p c=DOGE
```

Algorithms
==========
#### Currently supported
 * ✓ __scrypt__ (Litecoin, Dogecoin, Feathercoin, ...)
 * ✓ __scrypt:N__
 * ✓ __scrypt-jane:N__
 * ✓ __sha256d__ (Bitcoin, Freicoin, Peercoin/PPCoin, Terracoin, ...)
 * ✓ __axiom__ (Axiom Shabal-256 based MemoHash)
 * ✓ __bastion__ (Joincoin [J])
 * ✓ __bitcore__ Permuted serie of 10 algos (BitCore)
 * ✓ __blake__ (Saffron [SFR] Blake-256)
 * ✓ __blake2s__ (NevaCoin Blake2-S 256)
 * ✓ __bmw__ (Midnight [MDT] BMW-256)
 * ✓ __cryptonight__ (Bytecoin [BCN], Monero [XMR])
 * ✓ __cryptonight-light__ (Aeon)
 * ✓ __decred__ (Blake256-14 [DCR])
 * ✓ __dmd-gr__ (Diamond-Groestl)
 * ✓ __fresh__ (FreshCoin)
 * ✓ __groestl__ (Groestlcoin)
 * ✓ __jha__ (JackpotCoin, SweepStake)
 * ✓ __lbry__ (LBRY Credits [LBC])
 * ✓ __lyra2RE__ (Cryptocoin)
 * ✓ __lyra2REv2__ (VertCoin [VTC])
 * ✓ __myr-gr__ Myriad-Groestl (MyriadCoin [MYR])
 * ✓ __neoscrypt__ (Feathercoin)
 * ✓ __nist5__ (MistCoin [MIC], TalkCoin [TAC], ...)
 * ✓ __pentablake__ (Joincoin)
 * ✓ __pluck__ (Supcoin [SUP])
 * ✓ __quark__ (Quarkcoin)
 * ✓ __qubit__ (GeoCoin)
 * ✓ __skein__ (Skeincoin, Myriadcoin, Xedoscoin, ...)
 * ✓ __skein2__ (Woodcoin)
 * ✓ __s3__ (OneCoin)
 * ✓ __sia__ (Reversed Blake2B for SIA [SC])
 * ✓ __sib__ X11 + gost streebog (SibCoin)
 * ✓ __timetravel__ Permuted serie of 8 algos (MachineCoin [MAC])
 * ✓ __tribus__ 3 of the top NIST5 algos (Denarius [DNR])
 * ✓ __vanilla__ (Blake-256 8-rounds - double sha256 [VNL])
 * ✓ __veltor__ (Veltor [VLT])
 * ✓ __xevan__ x17 x 2 on bigger header (BitSend [BSD])
 * ✓ __x11evo__ (Revolver [XRE])
 * ✓ __x11__ (Darkcoin [DRK], Hirocoin, Limecoin, ...)
 * ✓ __x12__ (GalaxyCash [GCH])
 * ✓ __x13__ (Sherlockcoin, [ACE], [B2B], [GRC], [XHC], ...)
 * ✓ __x14__ (X14, Webcoin [WEB])
 * ✓ __x15__ (RadianceCoin [RCE])
 * ✓ __x16r__ (Ravencoin [RVN])
 * ✓ __x16s__ (Pigeoncoin [PGN])
 * ✓ __x17__ (Verge [XVG])
 * ✓ __yescrypt__ (GlobalBoostY [BSTY], Unitus [UIS], MyriadCoin [MYR])
 * ✓ __zr5__ (Ziftrcoin [ZRC])

#### Implemented, but untested
 * ? hefty1 (Heavycoin)
 * ? keccak (Maxcoin  HelixCoin, CryptoMeth, Galleon, 365coin, Slothcoin, BitcointalkCoin)
 * ? keccakc (Creativecoin)
 * ? luffa (Joincoin, Doomcoin)
 * ? shavite3 (INKcoin)

#### Planned support for
 * *scrypt-jane* (YaCoin, CopperBars, Pennies, Tickets, etc..)
 
Dependencies
============
 * libcurl http://curl.haxx.se/libcurl/
 * jansson http://www.digip.org/jansson/ (jansson source is included in-tree)
 * openssl libcrypto https://www.openssl.org/
 * pthreads
 * zlib (for curl/ssl)

#### Architecture-specific notes:
 * ARM:
   * No runtime CPU detection. The miner can take advantage of some instructions specific to ARMv5E and later processors, but the decision whether to use them is made at compile time, based on compiler-defined macros.
   * To use NEON instructions, add `"-mfpu=neon"` to CFLAGS.

Usage instructions
==================
Run "cpuminer --help" to see options.

### Connecting through a proxy

Use the --proxy option.

To use a SOCKS proxy, add a socks4:// or socks5:// prefix to the proxy host  
Protocols socks4a and socks5h, allowing remote name resolving, are also available since libcurl 7.18.0.

If no protocol is specified, the proxy is assumed to be a HTTP proxy.  
When the --proxy option is not used, the program honors the http_proxy and all_proxy environment variables.

Donations
=========
Donations for the work done in this fork are accepted :

Tanguy Pruvot :
* BTC: `1FhDPLPpw18X4srecguG3MxJYe4a1JsZnd`

Lucas Jones :
* MRO: `472haywQKoxFzf7asaQ4XKBc2foAY4ezk8HiN63ifW4iAbJiLnfmJfhHSR9XmVKw2WYPnszJV9MEHj9Z5WMK9VCNHaGLDmJ`
* BTC: `139QWoktddChHsZMWZFxmBva4FM96X2dhE`

Credits
=======
CPUMiner-multi was forked from pooler's CPUMiner, and has been started by Lucas Jones.
* [tpruvot](https://github.com/tpruvot) added all the recent features and newer algorythmns
* [Wolf9466](https://github.com/wolf9466) helped with Intel AES-NI support for CryptoNight

License
=======
GPLv2.  See COPYING for details.
