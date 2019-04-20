This file is included in the Windows 64bit binary package. 
# The original README.txt file is a part of cpuminer-3.8.8.1 distribution.
# This file is modified



cpuminer is a console program that is executed from a DOS command prompt.

There is no GUI and no mouse support.



Miner programs are often flagged as malware by antivirus programs. This is 
a false positive, they are flagged simply because they are cryptocurrency 
miners.

The source code is open for anyone to inspect. If you don't trust
 the software, don't use it.

The base source code by wo01(KotoDev) is ditributed on GitHub: https://github.com/KotoDevelopers/cpuminer-yescrypt
I modified it to add some algorithms(hash calculation method) as below:

algorithm option : supported algorithm and coin name
----------------------------------------------------
-a yescryptR8G   : yescrypt-0.5_GlobalBoost-Y [Koto]
-a yescryptR8    : yescrypt-0.5 [BitZeny]
-a yescryptR16   : yescrypt-0.5_R16 [Yenten]
-a yescryptR24   : yescrypt-0.5_R24 [JagariCoinR]
-a yescryptR32   : yescrypt-0.5_R32 [Wavi]
-a yespowerR8G   : yespower-0.5_GlobalBoost-Y [Koto]
-a yespowerR8    : yespower-0.5 [BitZeny]
-a yespowerR16   : yespower-0.5_R16 [Yenten]
-a yespowerR24   : yespower-0.5_R24 [JagaricoinR]
-a yespowerR32   : yespower-0.5_R32 [Wavi]
-a yespower      : yespower [Cryply]

I don't know the technical details, but yespower-0.5 seems YesPoWer's "yecrypt-0.5 compatible mode".
In my several tests, yespower gives hash-rate increase, if memory band-width is enough.


Default algorithm is yespowerR16, and this program says not "yay!!!" but "ypa!!!".
"ypa" is a substituon for Cyrillic scripts "ура", a Russian word;)





Choose the exe that best matches you CPU's features or use trial and
 error to find the fastest one that doesn't crash.

AMD CPUs older than Piledriver, including Athlon x2 and Phenom II x4, are not
 supported by cpuminer-opt due to an incompatible implementation of SSE2 on
 these CPUs.


Exe name                Compile flags            Arch name


minerd-sse2.exe      "-msse2"                  Core2, Nehalem

minerd-aes-sse42.exe "-march=westmere"         Westmere, Sandy-Ivybridge

minerd-avx.exe       "-march=corei7-avx"       Sandy-Ivybridge

minerd-avx2.exe      "-march=core-avx2"        Haswell, Sky-Kaby-Coffeelake

minerd-avx2-sha.exe  "-march=core-avx2 -msha"  Ryzen


I made these Windows x64 static binaries on Ubuntu 16.04 system, by following the instruction below...
just changed -m option as described above and used not "-O3 -funroll-loops -fomit-frame-pointer" but "-O2 -funroll-loops":

        cd deps
        ./build_win_x64_deps.sh
        cd ..
        autoreconf -fi -I./deps/x86_64-w64-mingw32/share/aclocal
        LDFLAGS="-L./deps/x86_64-w64-mingw32/lib -static" CFLAGS="-O3 -msse4.1 -funroll-loops -fomit-frame-pointer -I./deps/x86_64-w64-mingw32/include -std=c99 -DWIN32 -DCURL_STATICLIB -DPTW32_STATIC_LIB" ./configure --host=x86_64-w64-mingw32 --with-libcurl=deps/x86_64-w64-mingw32
        make


I'm not a professional programmer at all, just only enjoying programming as a "puzzle",
so don't ask me technical details:)

Thanks to wo(KotoDev) and many predecessors!



*** History ***
2018 Aug. 13th : First release
2018 Aug. 25th : fixed --coinbase-addr option (now it accepts 35 characters address(Koto) and 34 characters address(BitZeny, Yenten, JagariCoinR, Wavi and Cryply)


2018 Aug. 25th : OHASHI, as known as "ohashi3d" on bitcointalk and "kyosen" on Discord