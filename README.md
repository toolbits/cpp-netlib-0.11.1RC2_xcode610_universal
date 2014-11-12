cpp-netlib-0.11.1RC2_xcode610_universal
=======================================

Patch files to enable you to compile universal binary (32bits + 64bits) libraries with clang under xcode 6.1.0.<br/>

### development environment:

o MacOS X 10.10<br/>
o MacOS X 10.9.5<br/>
o Xcode 6.1.0<br/>
o clang = Apple LLVM version 6.0 (clang-600.0.54) (based on LLVM 3.5svn)<br/>
o boost_1_56_0<br/>



### apply patches
### from http://github.com/toolbits/cpp-netlib-0.11.1RC2_xcode610_universal
mv [_uri.ipp] cpp-netlib-0.11.1RC2/.<br/>

cd cpp-netlib-0.11.1RC2<br/>

mv _uri.ipp boost/network/uri/uri.ipp<br/>



### cpp-netlib with clang (libc++ with C++11)
sudo rm -rf /usr/local/cpp-netlib_libc++11<br/>

BOOST_INCLUDEDIR=/usr/local/boost_libc++11/include; export BOOST_INCLUDEDIR<br/>
BOOST_LIBRARYDIR=/usr/local/boost_libc++11/lib/a; export BOOST_LIBRARYDIR<br/>

cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_C_FLAGS="-std=c11 -stdlib=libc++ -arch i386 -arch x86_64" -DCMAKE_CXX_FLAGS="-std=c++11 -stdlib=libc++ -arch i386 -arch x86_64" -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ .<br/>
make<br/>

sudo mkdir -p /usr/local/cpp-netlib_libc++11/include<br/>
sudo mkdir -p /usr/local/cpp-netlib_libc++11/lib/a<br/>
sudo cp -R boost /usr/local/cpp-netlib_libc++11/include/.<br/>
sudo cp libs/network/src/*.a /usr/local/cpp-netlib_libc++11/lib/a/.<br/>
