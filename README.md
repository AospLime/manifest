# AospLime 2.X
AospLime is a custom ROM with additional features and UI/UX improvement to give user good experience when using it.

## Compilation of AospLime

### 1. Requirements
Before get started to compile AospLime for your own device, you need to complete some requirements as explained bellow:
```
- AMD64{64bit} based Linux system.
- 250GiB Free disk space(Recommended to use SSD).
- Quad-core processor.
- 16GiB RAM(Swap also can help).
- Fast and helpful internet connection.
```

### 2. Preparation
We have completed the requirements. Now, let's start to prepare compilation environtment. Cause all people isn't use same Linux distribution. So, let's make more simple with @akhilnarang 's script.
```
git clone https://github.com/akhilnarang/scripts
cd scripts
. setup/*sh
```

### 3. Downloading AospLime Source
Now, let's download AospLime Source

- First, make directory for AospLime Source, and then enter to the directory.
```
mkdir -p ~/lime
cd /lime
```

- Second, initialize AospLime Source manifest in the directory
```
If you want to download full AospLime Source, type:
repo init --depth=1 -u https://github.com/AospLime/manifest.git -b ten
But, if you want to do shallow download, type:
repo init -u https://github.com/AospLime/manifest.git -b ten

NOTES: Shallow download will not include full commits history.
```

- Third, start downloading the AospLime Source.
```
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

### 4. Download device sources
After syncing source completed, let's start downloading your target device source code. If your device need some extra configurtaion, you should apply the configuration before start.

### 5. Start compilation
Now, let's start compilation

- Call building environtment setup script.
```
. build/envsetup.sh
```

- Pick target device.
```
lunch aosp_DEVICE_NAME-userdebug
```

- Start the compilation.
```
mka bacon -j$(nproc --all)
```

## Notes
- Whenever you see "-jX" the, you need to change "X" with number of your complier machine's thread number.
- For maintainership infomation, please ask on our [Telegram group](http://t.me/AospLime).