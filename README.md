# cyanogenmod
Cyanogenmod build for Letv x600

## Getting started

Install the repo binary once on your machine:

	sudo apt-get install git phablet-tools
	
Prepare your local work dir:

	git clone git@github.com:tomdegryse/cyanogenmod.git

Initialize your local repository using the CyanogenMod trees:

	mkdir android; cd android
	repo init -u git://github.com/CyanogenMod/android.git -b cm-12.1

Add device specific files to your local repository:

	mkdir .repo/local_manifests	
	ln -s "$(pwd)/../cyanogenmod/manifests/xiaomi_hermes.xml" .repo/local_manifests

Synchronize your local repository:

	repo sync
