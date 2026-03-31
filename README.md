# Custom NVIDIA JetPack R38.4 BSP


## Aachitecture

* `Linux_for_Tegra/`：
* `Linux_for_Tegra/bootloader/`：Bootloader related
* `Linux_for_Tegra/kernel/`：Kernel source
* `Linux_for_Tegra/rootfs/`：Rootfs related

---

## (How to Sync)

1. Necessary Tools

```$sudo apt update```

```$sudo apt install git repo```

2. Init & Sync BSP

```$mkdir jetpack_workspace```

```$cd jetpack_workspace```

Init repo:

```$repo init -u git@github.com:CheYuT/jetpack-r38_4-manifest.git -b main```

Start to Sync:

```$repo sync -j4```

3. Prapare Rootfs $ Necessary NV files:

a. Download sample rootfs and pre-build files from NV.

```$cd ~/Download```

```$wget https://developer.nvidia.com/downloads/embedded/L4T/r38_Release_v4.0/release/Tegra_Linux_Sample-Root-Filesystem_R38.4.0_aarch64.tbz2```

```$wget https://developer.nvidia.com/downloads/embedded/L4T/r38_Release_v4.0/release/Jetson_Linux_R38.4.0_aarch64.tbz2```

b.
Note: ${SAMPLE_FS_PACKAGE} means the sample roots tbz2 file you downloaded.

${L4T_RELEASE_PACKAGE} means whole premium packages.

```$tar xf ${L4T_RELEASE_PACKAGE}```

```$mv ./Linux_for_Tegra/nv_tegra jetpack_workspace/Linux_for_Tegra```

```$sudo tar xpf ${SAMPLE_FS_PACKAGE} -C jetpack_workspace/Linux_for_Tegra/rootfs/```

```$cd jetpack_workspace/Linux_for_Tegra/```

```$sudo ./tools/l4t_flash_prerequisites.sh```

c. Apply the binaries based on the platform:

For Jetson Thor devices:

```$sudo ./apply_binaries.sh --openrm```

For Jetson Orin Series:

```$sudo ./apply_binaries.sh```
