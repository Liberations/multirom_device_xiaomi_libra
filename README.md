Device configuration for Xiaomi Mi-4c.
=====================================
# Needed packages (ubuntu 14.04+(mint17.3+))
sudo apt-get install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop maven openjdk-7-jdk openjdk-7-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev realpath

###Getting the Source

Making required directories
Obtaining the repo binary
Adding repo binary to your path
Giving the repo binary proper permissions
Initializing an empty repo
Syncing the repo
Alright, so now we’re getting there. I have outlined the basics of what we’re about to do and broke them down as I know them. This is all pretty much going to be copy/paste so it’ll be fairly difficult to screw this up :) Make directory for the repo binary

    $ mkdir ~/bin

Add directory for the repo binary to its path

    $ PATH=~/bin:$PATH

Downloading repo binary and placing it in the proper directory

    $ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

Giving the repo binary the proper permissions

    $ chmod a+x ~/bin/repo

Creating directory for where the SudaMod repo will be stored and synced

    $ mkdir ~/SudaMod $ cd ~/SudaMod

Initializing the SudaMod repo and downloading the manifest

    $ repo init -u git://github.com/SudaMod/android.git -b sm-2.0
    
Syncing the source

[Hint: This might take a long time as the source is about 13GB+]

    $  repo sync -c -f -j8 --force-sync --no-clone-bundle


# Copy device/xiaomi/libra/local_manifests/libra.xml to $ANDROID_BUILD_TOP/.repo/local_manifests/
cp ./device/xiaomi/libra/local_manifests/libra.xml $ANDROID_BUILD_TOP/.repo/local_manifests/

# Sync
repo sync -j4 

###Setting Up CCache

CCache is a method of utilizing a specified storage space to speed up building. It can be referred to as the same caching your android device does to speed up application and system boot times. In this case, CCache will help build SudaMod faster than standard build times (Able to cut-down 50% of time taken to build).

To set up CCache, follow the following:

    $ echo "export USE_CCACHE=1" >> ~/.bashrc

    $ ~/SudaMod/prebuilts/misc/linux-x86/ccache/ccache -M 50G

-M 50G The number before the letter G at the end specifies the amount of space CCache can use in your storage unit. As such, ensure that not too much of space is specified as this might result in unexpected errors although, the more storage you have, its recommended to have more CCache as it will increase the build times. Most efficient build systems are able to utilize CCache to about 120G or more.

# Build
lunch sm_libra-userdebug
brunch sm_libra-userdebug


Copyright 2015 - The CyanogenMod Project

thanks to thune-xiaobai

Device configuration for Xiaomi Mi-4c.
=====================================

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Dual-core 1.8 GHz ARM® Cortex™ A57 and quad-core 1.5 GHz ARM® Cortex™ A53
CHIPSET | Qualcomm MSM8992 Snapdragon 808
GPU     | Adreno 418
Memory  | 3 GB(2 GB)
Shipped Android Version | 5.1.1
Storage | 32 GB(16 GB)
Battery | 3080 mAh (non-removable)
Dimensions | 138.1 x 69.6 x 7.8 mm 
Display | 1080 x 1920 pixels, 5.0"
Rear Camera  | 13.0 MP, LED flash
Front Camera | 5.0 MP
Release Date | Sep. 2015

![Xiaomi Mi-4c](http://igao7.qiniudn.com/uploads/new/article/600_600/201509/56013886e1d4b.png "Xiaomi Mi-4c")
