I always used shared libraries without thinking much about how they actually worked.  
This week, I finally sat down and tried to understand them properly.

Here is what I learned so far:
1. There are two types of libraries, static and dynamic. Static libraries are huge because they carry everything inside. Dynamic ones are much lighter, since they only point to the code that gets loaded at runtime.
2. I found out that libraries live in folders like **/lib**, **/lib64**, **/usr/lib**, and **/usr/lib64**, and they often have major and minor versions with symbolic links connecting them.
3. When I ran `ldd` on different executables, I could finally see which libraries each program depends on. Then `ldconfig`made sense to me, especially when I learned that it scans the configs in **/etc/ld.so.conf** and **ld.so.conf.d**.
4. The search order surprised me. **LD_LIBRARY_PATH** takes priority, then **PATH**, then the configuration files, and only after that the system folders.
5. The dynamic linker, usually **ld-linux**, suddenly clicked in my mind as the thing that loads everything before a program even starts running.

It felt great to finally understand what has been happening behind the scenes all this time.

If you ever struggled with library paths or linker errors, what helped you make sense of it? I am curious to hear your experience 👇

Follow me if you enjoy learning Linux together.

#Linux #DevOps #CloudNative #LearningJourney #Engineering

![[Gemini_Generated_Image_ild5d4ild5d4ild5.png]]