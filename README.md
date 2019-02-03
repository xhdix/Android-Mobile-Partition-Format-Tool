# Mobile-Partition-Format-Tool
Format the partitions (system, data, cache) of mobile devices that have problems with their memory or write protected (loaded read only) data/cache partitions. (Using OTA Tools](https://source.android.com/devices/tech/ota/nonab/inside_packages))

**If you know the exact _"filesystem type"_ , _"flash device type"_ and _"filesystem address"_ for a device, please send it to me.**

## Released files

### * Huawei
1. Ascend D quad XL - U9510e
   - [update file for: format system, data, cache (ext4)](https://github.com/xhdix/Mobile-Partition-Format-Tool/releases/tag/U9510e)
2. Ascend Y300
   - update file for: format system, data, cache

### * Sony
1. Xpria Neo V - MT11i
   - [update file for: format system, data, cache (yaffs2)](https://github.com/xhdix/Mobile-Partition-Format-Tool/releases/tag/MT11i)
   - [update file for: format system(yaffs2)](https://github.com/xhdix/Mobile-Partition-Format-Tool/releases/tag/MT11i-system) (External reference)
   - [update file for: format data (f2fs)](https://github.com/xhdix/Mobile-Partition-Format-Tool/releases/tag/MT11i-data) (External reference)
2. Xpria Neo L - MT25i
   - update file for: format system, data, cache

### * HTC

### * ASUS

### * Lenovo

### * Samsung

## How to use this method on other devices?

Normally, device Recovery tools should be sensitive to `SHA1-Digest`, but not. So, you can change the content of the **[updater-script](https://github.com/xhdix/Mobile-Partition-Format-Tool/raw/master/META-INF/com/google/android/updater-script)** file at the following address:

[/META-INF/com/google/android/](https://github.com/xhdix/Mobile-Partition-Format-Tool/tree/master/META-INF/com/google/android)

There are three main lines in it: (Format, Mount, Unmount)
```
format([filesystem type], [flash device type], [filesystem address], "0", [partition address]);
mount([filesystem type], [flash device type], [filesystem address], [partition address], "");
unmount([partition address]);
```

- The supported [filesystem types](https://source.android.com/devices/tech/ota/nonab/device_code#partition-map) may be yaffs2, ext4, f2fs, vfat, etc.
- Each device may have a [flash device type](https://www.cnblogs.com/shangdawei/p/4514128.html) such as MMC, MTD, EMMC, etc.
- Also, the `filesystem` address may be different. For example, to access the `/system` partition filesystem:
  - `/dev/block/mtd/by-name/system`
  - `/dev/block/mmcblk0p15`
  - `/dev/block/mmcblk0p5`
  - `/dev/block/mtdblock0`
  - `/dev/block/platform/msm_sdcc.1/by-name/system`
  - `/dev/block/platform/msm_sdcc.4/by-num/p5`
  - `/dev/block/platform/s3c-sdhci.0/by-name/system`
  - etc
 
To find it, you can use [tutorials](https://android.stackexchange.com/a/102551) or [Search engines](https://www.google.com/search?q=mt11i++%2Fdev%2Fblock%2F+%2Fsystem) or ask questions at [xda-developers forums](https://forum.xda-developers.com).

## references
 - https://source.android.com/devices/tech/ota/tools
 - https://source.android.com/devices/tech/ota/nonab/inside_packages
 - https://android.googlesource.com/platform/build/+/master/tools/releasetools/ota_from_target_files.py
 - https://source.android.com/devices/tech/ota/nonab/block.html
 - https://source.android.com/devices/tech/ota/nonab/device_code#partition-map
 - https://www.cnblogs.com/shangdawei/p/4514128.html
 - https://android.stackexchange.com/a/102551
 - https://android.stackexchange.com/questions/5232/how-can-i-view-the-android-internal-partition-table
 - https://forum.xda-developers.com/android/general/info-android-device-partitions-basic-t3586565
 - https://forum.xda-developers.com/xperia-neo/development/rom-candy5-v2-0-2-haida-hallon-t3092668
 - https://github.com/LegacyXperia/local_manifests/issues/898
 
