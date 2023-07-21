# superbinary-parser

Provides a few tools to manipulate a [SuperBinary](https://github.com/hack-different/apple-knowledge/blob/main/_docs/UARP_and_FOTA.md#uarp---universal-accessory-restore-protocol).

This tool permits you to extract the various UARP (Universal Accessory Restore Protocol) payload types within SuperBinaries.
On Beats Studio Buds, it can also extract the [FOTA](https://github.com/hack-different/apple-knowledge/blob/main/_docs/UARP_and_FOTA.md#fota---firmware-over-the-air) (MediaTek OTA)
in a [SuperBinary](https://github.com/hack-different/apple-knowledge/blob/main/_docs/UARP_and_FOTA.md#uarp---universal-accessory-restore-protocol) container.

This tool is confirmed to work on the following device firmwares that have the SuperBinary container:
- [AirPods Pro (2nd generation)](https://appledb.dev/device/AirPods-Pro-(2nd-generation).html)
- [Beats Studio Buds](https://appledb.dev/device/Beats-Studio-Buds.html)
- [MagSafe Charger](https://appledb.dev/device/MagSafe-Charger.html)
- MagSafe Charger with MFi module, both [A2463](https://mesu.apple.com/assets/com_apple_MobileAsset_UARP_A2463/com_apple_MobileAsset_UARP_A2463.xml), and [A2728](https://mesu.apple.com/assets/com_apple_MobileAsset_UARP_A2728/com_apple_MobileAsset_UARP_A2728.xml).
- [MagSafe Battery Pack](https://appledb.dev/device/MagSafe-Battery-Pack.html)
- [USB-C to MagSafe 3 Cable (2 m)](https://appledb.dev/device/USB-C-to-MagSafe-3-Cable-(2-m).html)
- [35W Dual USB-C Port Compact Power Adapter](https://appledb.dev/device/35W-Dual-USB-C-Port-Compact-Power-Adapter.html)
- [35W Dual USB-C Port Power Adapter](https://appledb.dev/device/35W-Dual-USB-C-Port-Power-Adapter.html)
- [Apple Watch Magnetic Fast Charger to USB-C Cable](https://appledb.dev/device/Apple-Watch-Magnetic-Fast-Charger-to-USB-C-Cable.html)

> **Note**
> This tool aims to maintain compatability with the latest version of SuperBinary available.
>
> For example, with AirPods Pro (2nd generation), the version of SuperBinary increased from 2 to 3
> in version 6.0. If parsing fails with a version 3 SuperBinary in the future, please file an issue!

## Installation
As this package depends on a secondary repository ([LZMAAlone](https://github.com/spotlightishere/LZMAAlone)) for custom LZMA decoding,
it's recommended to install this package within a virtual environment.

You'll need appropriate build tools for your system.
If you are installing on a Windows system, first download [Microsoft Visual C++ 14.0](https://visualstudio.microsoft.com/visual-cpp-build-tools/) or greater.

Assuming a UNIX operating system, execute similar to the following:
```
git clone https://github.com/spotlightishere/superbinary-parser
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
```
If you are installing on a Windows system, first download Microsoft Visual C++ 14.0 or greater through this [link](https://visualstudio.microsoft.com/visual-cpp-build-tools/).

You can then `python3 main.py`:
```
> python3 main.py
usage: main.py [-h] [--extract-payloads | --no-extract-payloads] [--decompress-fota | --no-decompress-fota] [--extract-rofs EXTRACT_ROFS] source output_dir
main.py: error: the following arguments are required: source, output_dir
```

On Beats Studio Buds, it is also possible to extract the firmware sounds from the Read Only File System (ROFS) using this syntax:
``` 
> python3 main.py --extract-payloads --decompress-fota --extract-rofs FirmwareUpdate.uarp output_dir
```
The script will then extract the sounds to the output direction.
