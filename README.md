# xmrig-cuda
This repository contains the CUDA plugin for the XMRig miner, which provides support for NVIDIA GPUs.

This plugin is a separate project because of the main reasons listed below:
1. Not all users need CUDA support, and it is an optional feature.
2. CUDA has strict compiler version requirements that may be difficult to meet, unlike CPU mining code, which is generally very flexible.

## CUDA 13 Support and Requirements

**Minimum Requirements:**
- CUDA Toolkit 13.0 or later
- NVIDIA Driver 580 or later
- GPU with Compute Capability 7.5 or higher (Turing architecture or newer)

**Supported GPU Architectures:**
- Turing (CC 7.5): GeForce RTX 20xx series, GTX 16xx series, Tesla T4
- Ampere (CC 8.0, 8.6, 8.7): GeForce RTX 30xx series, Tesla A100, A10
- Ada Lovelace (CC 8.9, 9.0): GeForce RTX 40xx series, L40, L4
- Blackwell (CC 9.x): Future GPU support

**Dropped GPU Support (as of CUDA 13):**
- Maxwell (CC 5.0): GTX 750 Ti, GTX 9xx series - No longer supported
- Pascal (CC 6.0, 6.1): GTX 10xx series, Tesla P100 - No longer supported
- Volta (CC 7.0): Titan V, Tesla V100 - No longer supported

If you have an older GPU (Maxwell, Pascal, or Volta), you must use CUDA 12 or earlier versions of this plugin.


## Windows

* To [download](https://github.com/xmrig/xmrig-cuda/releases) the plugin, you must choose the appropriate CUDA version based on your GPU:
  - **CUDA 13**: For Turing, Ampere, Ada, and newer GPUs (RTX 20xx/30xx/40xx, GTX 16xx series)
  - **CUDA 12 or earlier**: For older GPUs (Maxwell GTX 9xx/10xx, Pascal GTX 10xx, Volta)
* Windows builds are available for every major CUDA release. Alternatively, you can [build](https://xmrig.com/docs/miner/build/windows) the plugin from the source.
* Place **`xmrig-cuda.dll`** and other dll files near to **`xmrig.exe`**.
* Edit **`config.json`** enable the plugin.
```
{
   ...
   "cuda": {
      "enabled": true,
      ...
   }
   ...
}
```
### Advanced
You can specify the path to the plugin using the `loader` option.
```
{
   ...
   "cuda": {
      "enabled": true,
      "loader": "c:/some/path/xmrig-cuda.dll",
      ...
   }
   ...
}
```
Due to JSON format restrictions, the directory separator must be written in Linux style `/` or escaped `\\`.

## Linux
Linux usage is almost the same as Windows except we don't provide binaries and you must build the plugin from the source and the name of the plugin is different **`libxmrig-cuda.so`**.

## macOS
CUDA no longer supports macOS, which means that the plugin also does not support it.
