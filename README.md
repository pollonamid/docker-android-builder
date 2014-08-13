docker-android-builder
==================

Create a [Docker](https://www.docker.io) based environment for [Android Open Source Project](https://source.android.com/index.html) (AOSP) based building

This Dockerfile will create a docker container which is based on Trusted Docker Ubuntu 14.04 build.
It will install the "repo" utility and any other build dependencies which are required to compile your flavor of Android.

**NOTE:** Remember that Android is a huge project. It will consume a large amount of disk space (~80 GB) and it can easily take hours to build.

---

### How to run/build 

* You will need to [install Docker](https://www.docker.io/gettingstarted) to proceed!
* If an image does not exist, ```docker build``` is executed first

1. Clone the repo
```
git clone https://github.com/thrilleratplay/docker-android-builder.git
cd docker-android-builder
```

2. Update the build variables located in "config/android-build-vars.sh"
  * **Optional** Update "config/build-android.sh" with the commands needed to build Android.  The steps for building Android vary between devices and distributions.  **If you are new to this, you probably want to run the commands manually before using the automated build file**

3. Start up Docker
```
./run.sh
```

**ADDITIONAL NOTES:**  
* The container uses a text-based window manager and terminal multiplexer called [Byobu](http://byobu.co/) to run the shell.

* Once in the container, begin the build process your desired Android distribution.  ONLY If you have updated the build-android script, simply run:
```
build-android
```
---

### Tested Android builds  
<table>
  <tr>
   <th>Distribution</th>
   <th>Requires Oracle Java</th>
 </tr>
 <tr>
   <td><a href="https://carbonrom.org" target="_blank">CarbonRom</a></td>
   <td>Yes</td>
 </tr>
</table>
---

### More information

* [Discussion thread @ XDA developers](http://forum.xda-developers.com/showthread.php?t=2650345) - Started for [docker-cyanogenmod](https://github.com/stucki/docker-cyanogenmod)

