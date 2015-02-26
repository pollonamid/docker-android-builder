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
git clone https://github.com/pollonamid/docker-android5-builder.git
cd docker-android5-builder
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
* [CarbonRom](https://carbonrom.org)
* [OmniRom](http://omnirom.org)
* [Dirty Unicorns](http://dirtyunicorns.com/dusite)

---

### TODO
* Test more builds.
* Add local user permission mapping. [Dependent on Docker update](https://github.com/docker/docker/pull/5910)
* Add basic documentation for different OS's and helpful tools like [Android-Kitchen](https://github.com/dsixda/Android-Kitchen)

### FAQ
**Q:** Do I need Oracle Java?  
**A:** In most cases, no.  However, there have been instances where functionality that only exist in Oracle Java has been committed to AOSP projects ([Example](https://github.com/CyanogenMod/android_external_bouncycastle/commit/57c3bb556ef873a72010d6022edddc14e6bba9be)).  

**Q:** Using *adb devices*, on the host system I can see my USB connected device.  Why is it not listed through Docker?  
**A:** The USB port needs to be exposed to Docker.  [See this Stack Overflow post](http://stackoverflow.com/questions/17792161/is-it-possible-to-expose-a-usb-device-to-a-lxc-docker-container)

### More information

* [Discussion thread @ XDA developers](http://forum.xda-developers.com/showthread.php?t=2650345) - Started for [docker-cyanogenmod](https://github.com/stucki/docker-cyanogenmod)

