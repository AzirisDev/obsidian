I have used package managers for a while.
This week, I decided to learn the basics.

Notes desk:
1. Repositories are just places where packages live, and the system reads them from **/etc/apt/sources.list** and any files inside **sources.list.d**. Creating a new file there felt much cleaner than editing the main config.
2. I finally understood the categories. **main**, **restricted**, **contrib**, and **universe** tell you a lot about the software itself and how it is maintained.
3. Running `apt-get update` does not upgrade anything, it just refreshes the metadata stored inside **/var/cache/apt**. This helped me understand why updates sometimes seem fast and sometimes slow.
4. Commands like `apt-get -s`, `apt-get --download-only`, and `dpkg -l` showed me how much control the system actually gives you.
5. I also learned that `dpkg-reconfigure` can bring up the configuration interface again, which I completely missed before.

It felt like peeling back the curtain on something I used every day without noticing.

What was the moment when Debian’s package system finally made sense to you? I would love to hear it 👇

Follow me if you are learning Linux piece by piece too.

#Linux #Debian #DevOps #LearningInPublic #Engineering

![[Gemini_Generated_Image_i6832ui6832ui683.png]]