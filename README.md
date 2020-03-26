1. I have built the project in cygwin (x86_64, windows 10 professional). Version
details:
$ g++ -v
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-pc-cygwin/9.2.0/lto-wrapper.exe
Target: x86_64-pc-cygwin
Configured with: /cygdrive/i/szsz/tmpp/gcc/gcc-9.2.0-3.x86_64/src/gcc-9.2.0/configure --srcdir=/cygdrive/i/szsz/tmpp/gcc/gcc-9.2.0-3.x86_64/src/gcc-9.2.0 --prefix=/usr --exec-prefix=/usr --localstatedir=/var --sysconfdir=/etc --docdir=/usr/share/doc/gcc --htmldir=/usr/share/doc/gcc/html -C --build=x86_64-pc-cygwin --host=x86_64-pc-cygwin --target=x86_64-pc-cygwin --without-libiconv-prefix --without-libintl-prefix --libexecdir=/usr/lib --enable-shared --enable-shared-libgcc --enable-static --enable-version-specific-runtime-libs --enable-bootstrap --enable-__cxa_atexit --with-dwarf2 --with-tune=generic --enable-languages=c,c++,fortran,lto,objc,obj-c++ --enable-graphite --enable-threads=posix --enable-libatomic --enable-libgomp --enable-libquadmath --enable-libquadmath-support --disable-libssp --enable-libada --disable-symvers --with-gnu-ld --with-gnu-as --with-cloog-include=/usr/include/cloog-isl --without-libiconv-prefix --without-libintl-prefix --with-system-zlib --enable-linker-build-id --with-default-libstdcxx-abi=gcc4-compatible --enable-libstdcxx-filesystem-ts
Thread model: posix
gcc version 9.2.0 (GCC)
 
2. Command line to build is used:
  $ g++ -std=c++1z  InputFileReader.cpp TradeStat.cpp main.cpp -o trade_stat

3. Command used to run: command input_file output_file
   - 1st arument is the command
   - 2nd argument is the input file
   - 3rd argument is the output file

  (a) Using given input from Quantlab:
     $ trade_stat Quantlab.csv output.csv

  (b) Using my sample input file to test 
      (i) line validation logic in the input file, eg. blank symbol or 
          less than equal to 0 timestamp/volume/price
      (ii) whether number items in the line is 4 (A valid input line
           should have 4 items: timestamp, symbol, voulme, price)
      (iii) Whether current time stamp less than previous time stamp

    Example error sample while processing sample_input.csv:
        ERROR: Share price is <= 0!, Input Line =52900024703,aax,9,0, Line Num=4
        ERROR: Current time stamp is less than previous time stamp!, Input Line =52900027780,aac,21,638, Line Num=9
        ERROR: Invalid symbol!, Input Line =52900033455,,9,756, Line Num=11
        ERROR: Share value <= 0!, Input Line =52900033456,aap,0,756, Line Num=12
        ERROR: Share price is <= 0!, Input Line =52900033457,aaq,9,0, Line Num=13
        ERROR: Time stamp value <= 0!, Input Line =0,aar,9,759, Line Num=14

    $ trade_stat.exe sample_input.csv sample_output.csv

4. The following files will be included

  (a) README (This file)
  (b) TradeStatClassDiagram.pdf (UML diagram)
  (c) StockInfo.h - Symbol info from input line
  (d) InputFileReader.h - Class to read input file
  (e) TradeStat.h - Stat for symbol
  (f) InputFileReader.cpp
  (g) TradeStat.cpp
  (h) main.cpp - Driver
  (i) output.csv (Generated from Quantlab provided input file)
  (j) sample_input.csv (My sample input file to test validation 
      logic input line)
  (k) sample_output.csv (Generated from sample_input.csv)

5. Any issue with building project or unzipping or any other issue please contact me.
   Thanks.
