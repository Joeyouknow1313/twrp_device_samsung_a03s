## Recovery Device Tree for the Samsung Galaxy A03s

## How-to compile it:

# Create dirs
$ mkdir tw; cd tw

# Init repo
$ repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12

# Clone a03s repo
$ git clone https://github.com/edward0181/android_device_samsung_a12 -b twrp-12.0 device/samsung/a03s

# Sync
$ repo sync --no-repo-verify -c --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune -j`nproc`

# Build
$ source build/envsetup.sh; export ALLOW_MISSING_DEPENDENCIES=true; lunch twrp_a03s-eng; mka recoveryimage

# Disable File Based Encryption (FBE) after installing TWRP.
$ Boot TWRP; format DATA partition; start TWRP SHELL; execute: multidisabler.
Your DATA partition will be secured against re-encryption.




