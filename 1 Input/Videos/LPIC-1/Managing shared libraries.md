We have two types of libraries: static and dynamic
- static - this library is large and contain each necessary library in itself
- dynamic - it only contains references to necessary libraries

They located in /lib and /lib64 (system-wide utilities) and usr/lib and usr/lib64 (user software).
They can have major name like `libudev.so.1` and minor like `libudev.so.1.7.2`. Also, there can be `libudev.so.1` as symbolic links to other versions.

- ldd `command` - shows depending libs from the exact lib
- ldconfig - checks all libraries and creates cache of available libraries
	- it goes through `/etc/ld.so.conf` and files in `/etc/ld.so.conf.d/`, checks library references and creates cache.
	- ldconfig -p - prints the contents.

####  Library search order
- **LD_LIBRARY_PATH** environment variable - we can set it manually
- **PATH** environment variable
- **/etc/ld.so.conf** **and** **ld.so.conf.d/**
- **/lib, /lib64, /usr/lib, /usr/lib64**

#### ld-linux
Dynamic linker - invoked by the kernel to load required shared libraries.
- /lib64/ld-linux.so /path/to/executable


Links: [[Package Manager in Linux]]

202509101010

