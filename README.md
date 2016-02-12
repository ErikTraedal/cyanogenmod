# cyanogenmod
Cyanogenmod build for Letv x600

## Getting started

### Setup your local repository

Install the repo binary once on your machine:

	sudo apt-get install git phablet-tools
	
Prepare your local work dir:

	git clone git@github.com:tomdegryse/cyanogenmod.git -b cm-12.1

Initialize your local repository using the CyanogenMod trees:

	mkdir android; cd android
	repo init -u git://github.com/CyanogenMod/android.git -b cm-12.1

Add device specific files to your local repository:

	mkdir .repo/local_manifests	
	ln -s "$(pwd)/../cyanogenmod/manifests/xiaomi_hermes.xml" .repo/local_manifests

Synchronize your local repository:

	repo sync

### Setup build environment

Install the SDK:

	wget http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz
	tar zxvf android-sdk_r24.4.1-linux.tgz
	
Add the SDK packages (Android SDK Tools, Android SDK Platform-tools, Android SDK Build-tools (highest version)
and SDK Platform Android 5.1.1): 

	cd android-sdk-linux/tools
	./android list sdk --all
	./android update sdk -u -a -t 1,3,4,27

Install the build packages:

	sudo apt-get install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-7-jdk openjdk-7-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev

### Run the build

Prepare the device-specific code:

	source build/envsetup.sh
	breakfast hermes

Start the build:

	croot
	brunch hermes
