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

        repo init -u https://github.com/hockeymikey/platform_manifest.git -b oreo

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="whatawurst/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-15.1" />
            <project name="whatawurst/android_device_sony_common-treble" path="device/sony/common-treble" remote="github" revision="lineage-15.1" />
            <project name="whatawurst/android_device_sony_yoshino" path="device/sony/yoshino" remote="github" revision="lineage-15.1" />
            <project name="hockeymikey/android_device_sony_lilac" path="device/sony/lilac" remote="github" revision="oreo" />
            <project name="hockeymikey/android_vendor_sony_lilac" path="vendor/sony/lilac" remote="github" revision="oreo" />
            <project name="hockeymikey/repo_update" path="device/sony/repo_update" remote="github" revision="oreo">
                <linkfile src="repo_update.sh" dest="repo_update.sh" />
            </project>
        </manifest>

* Sync the repo:

        ./repo_update.sh
        
        or
        
        repo sync -j8 -q -c --no-tags --force-sync

* Setup the environment

        source build/envsetup.sh
        lunch
        
     (for lunch make sure to pick the last one, lilac-userdebug. So you'd enter the number for it like 17 or whatever it is. lilac-eng works too but is for testing more so.)

* Build ResurrectionRemix

        make -j8 bacon
