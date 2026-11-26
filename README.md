# D4RK OS - manifest (V3-END)

Source manifest for **D4RK OS V3-END** (Android 13), based on Havoc-OS, LineageOS and AOSP.
Only the repositories we changed are hosted in this organization; everything else is fetched from
the upstream projects, exactly like Havoc-OS and LineageOS do.

## Get the source

```bash
mkdir d4rk && cd d4rk
repo init -u https://github.com/D4RK-Os/android_manifest -b V3-END
repo sync -c -j8 --no-tags
```

`snippets/d4rk.xml` lists the projects that come from this organization (branch `V3-END`).

## Devices

| Device | Codename | Status |
|---|---|---|
| Samsung Galaxy J7 Prime | on7xelte | Reference device |
| Redmi Note 12 Pro 4G | sweet_k6a | Experimental, needs own trees and extra fixes |

Device, vendor and kernel trees are not part of this manifest yet. Add yours with a local manifest
in `.repo/local_manifests/`.

The default wallpaper in this tree is **1080x1920** (J7 Prime). Devices with other resolutions
(e.g. 1080x2400) should override `default_wallpaper.png` in their device overlay.

## Build notes

* Host compiler: the `system/tools/aidl` fix (uninitialized member) is included.
* If the build fails with a missing `clang-r450784d/bin/ld`, create the symlink:
  `ln -s lld prebuilts/clang/host/linux-x86/clang-r450784d/bin/ld`
* Disable RBE if you do not have a remote build service configured.

## Known issues

* Bluetooth SCO calls and screen recording have problems.
* Three crashes are still being investigated on the J7 Prime.

## Credits and licenses

Based on Havoc-OS, LineageOS and the Android Open Source Project. Original licenses of each
repository apply (Apache-2.0 for most of the platform, GPL-2.0 for the kernel).
