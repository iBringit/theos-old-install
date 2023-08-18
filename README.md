# theos-old-install

Installation macOS

This guide will help you install Theos on your macOS device.

Supports jailbroken devices and simulators, where applicable.

Platform	Minimum OS version	Targets supported
macOS	Mavericks (10.9)	macOS, iOS, watchOS, tvOS
All the commands shown on the following instructions are meant to be run as the "user" user, not root. Similarly, Theos is also meant to be run as a normal user, not root.

Install the following prerequisites:

Homebrew
Xcode1 is mandatory. The Command Line Tools package isn’t sufficient for Theos to work. Xcode includes toolchains for all Apple platforms.
1 Xcode 5.0 or newer. Xcode 4.4 supported, but only when building for ARMv6 (1st/2nd generation iPhone/iPod touch).
 brew install ldid xz
Set up the THEOS environment variable:

 echo "export THEOS=~/theos" >> ~/.profile
For this change to take effect, you must restart your shell. Open a new tab and do echo $THEOS on your shell to check if this is working.

Clone Theos to your device:

 git clone --recursive https://github.com/theos/theos.git $THEOS
Get the toolchain:

Xcode contains the toolchain.

Get an iOS SDK:

Xcode always provides the latest iOS SDK, but as of Xcode 7.3, it no longer includes private frameworks you can link against. This may be an issue when developing tweaks. You can get patched SDKs from our SDKs repo.

 curl -LO https://github.com/theos/sdks/archive/master.zip
 TMP=$(mktemp -d)
 unzip master.zip -d $TMP
 mv $TMP/sdks-master/*.sdk $THEOS/sdks
 rm -r master.zip $TMP
Set up ghostbin script (optional):

 curl https://ghostbin.com/ghost.sh -o $THEOS/bin/ghost
 chmod +x $THEOS/bin/ghost
