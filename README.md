Device configuration for Sony Xperia XZ1 dual sim variant (poplar_dsds)
========================================================

Description
-----------

This repository is for TWRP on Sony Xperia XZ1 dual sim variant (poplar_dsds).

How to build TWRP
----------------------

* Make a workspace:

        mkdir -p ~/twrp
        cd ~/twrp

* Initialize the minimal repo:

        repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <project name="whatawurst/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="android-9.0" />
            <project name="whatawurst/android_device_sony_poplar_dsds" path="device/sony/poplar_dsds" remote="github" revision="android-9.0" />
        </manifest>

* Sync the repo:

        repo sync

* Setup the environment

        export ALLOW_MISSING_DEPENDENCIES=true

        source build/envsetup.sh
        lunch omni_poplar_dsds-userdebug

* Build TWRP

        make -j7 recoveryimage
