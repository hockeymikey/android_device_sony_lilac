Device configuration for Sony Xperia XZ1 Compact (lilac)
========================================================

Description
-----------

This repository is for ResurrectionRemix Oreo on Sony Xperia XZ1 Compact (lilac).

How to build ResurrectionRemix Oreo
-----------------------------------

* Make a workspace:

        mkdir -p ~/ResurrectionRemix/repo
        cd ~/ResurrectionRemix/repo

* Initialize the repo:

        repo init -u https://github.com/ResurrectionRemix/platform_manifest.git -b oreo

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="cryptomilk/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-15.1" />
            <project name="russel5/android_device_sony_common-treble" path="device/sony/common-treble" remote="github" revision="oreo" />
            <project name="russel5/android_device_sony_yoshino" path="device/sony/yoshino" remote="github" revision="oreo" />
            <project name="russel5/android_device_sony_lilac" path="device/sony/lilac" remote="github" revision="oreo" />
        </manifest>

* Sync the repo:

        repo sync -j8 -c

* Setup the environment

        source build/envsetup.sh
        lunch

* Build ResurrectionRemix

        make -j8 bacon
