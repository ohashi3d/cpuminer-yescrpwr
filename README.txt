This file is included in the Windows binary package. 
# The original README.txt file is a part of cpuminer-3.8.8.1 distribution.
# This file is modified



cpuminer is a console program that is executed from a DOS command prompt.

There is no GUI and no mouse support.



Miner programs are often flagged as malware by antivirus programs. This is 
a false positive, they are flagged simply because they are cryptocurrency 
miners.

The source code is open for anyone to inspect. If you don't trust
 the software, don't use it.

The original source code by wo01(KotoDev) was ditributed on GitHub: https://github.com/KotoDevelopers/cpuminer-yescrypt
I modified the old code (before Sapling) to add some algorithms(hash calculation method) as below:

algorithm option : supported algorithm and coin name
----------------------------------------------------
-a yescryptR8G     : yescrypt-0.5_GlobalBoost-Y [old Koto (before Sapling)]
-a yescryptR8      : yescrypt-0.5 [BitZeny]
-a yescryptR16     : yescrypt-0.5_R16 [Elicoin]
-a yescryptR24     : yescrypt-0.5_R24 [JagariCoinR]
-a yescryptR32     : yescrypt-0.5_R32 [Wavi]
-a yespower05R8G   : yespower-0.5_GlobalBoost-Y [old Koto (before Sapling)]
-a yespower05R8    : yespower-0.5 [BitZeny]
-a yespower05R16   : yespower-0.5_R16 [Elicoin]
-a yespower05R24   : yespower-0.5_R24 [JagaricoinR]
-a yespower05R32   : yespower-0.5_R32 [Wavi]
-a yespower        : yespower [CranePay]
-a yespowerR16     : yespowerR16 [Yenten]

yespower has 2 modes... one is yespower-0.5 for yescrypt comatible mode and another is yespower-1.0 for REAL yespower.
In my several tests, yespower-0.5 is a bit faster than yescrypt, if memory band-width is enough.


Default algorithm is yespowerR16, and this program says not "yay!!!" but "ypa!!!".
"ypa" is a substituon for Cyrillic scripts "ура", a Russian word;)





Choose the exe that best matches you CPU's features or use trial and
 error to find the fastest one that doesn't crash.

AMD CPUs older than Piledriver, including Athlon x2 and Phenom II x4, are not
 supported by cpuminer-opt due to an incompatible implementation of SSE2 on
 these CPUs.


Exe name                Compile flags            Arch name


cpuminer-sse2.exe      "-msse2"                  Core2, Nehalem

cpuminer-aes-sse42.exe "-march=westmere"         Westmere, Sandy-Ivybridge

cpuminer-avx.exe       "-march=corei7-avx"       Ivybridge

cpuminer-avx2.exe      "-march=core-avx2"        Haswell, Sky-Kaby-Coffeelake

cpuminer-avx2-sha.exe  "-march=core-avx2 -msha"  Ryzen


I made these Windows x64 static binaries on Ubuntu 16.04 system, by following the instruction below...
just changed -m option as described above and used not "-O3 -funroll-loops -fomit-frame-pointer" but "-O2 -unroll-loops":

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
2018 Aug. 13 : First release
2018 Aug. 25 : fixed --coinbase-addr option (now it accepts 35 characters address(Koto) and 34 characters address(BitZeny, Yenten, JagariCoinR, Wavi and Cryply)
2019 Apr. 21 : Renamed yespower-0.5 options like yespowerR8 -> yespower05R8 and added yespowerR16(yespower-1.0 mode)

2019 Apr. 21 : OHASHI, as known as "ohashi3d" on bitcointalk and Discord
