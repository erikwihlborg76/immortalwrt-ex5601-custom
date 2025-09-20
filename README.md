# Experimental ImmortalWrt Builds for Zyxel EX5601

## About the Build

This build targets **zyxel_ex5601-t0-ubootmod**, based on **OpenWrt 24.10 with kernel 6.6**.  

Key changes include:

- **Zero-Wait DFS** enabled  
- **SQM** support added  
- **WARP** acceleration kept (debug features removed)  
- **Toolchain optimizations** applied  

All essential **MediaTek Wi-Fi features** from the padavanonly build are retained.

## Using It

To enable DFS:  

- Set the Wi-Fi channel to **"auto"** on the 5 GHz band.  
- Ensure the Wi-Fi country code is set to either **SE (Sweden)** or **US (United States)**, DFS parameters are only applied for these regions.

## Changes Compared to padavanonly immortalwrt-mt798x-6.6

- Switched language to **English**, with default Wi-Fi country set to **Sweden (SE)**  
- Reduced from **multi-profile builds** (GL-MT6000, JDCloud, TP-Link, Xiaomi, …) to a **single target: zyxel_ex5601-t0-ubootmod**  
- Added **SQM stack**: `sqm-scripts`, `luci-app-sqm`, `kmod-sched-cake`, `kmod-sched-core`  
- Removed debug options: `WARP_DBG_SUPPORT`, `WARP_MEMORY_LEAK_DBG` (additional debugging features can be toggled at the end of the `.config`)  
- Enabled **DFS** and vendor-specific feature **DFS Zero-Wait**  
- Applied **target-specific optimizations**  
- Removed **BusyBox customizations**

## How It’s Built

The build is automated using **GitHub Actions**:  

- Sources are fetched from [padavanonly/immortalwrt-mt798x-24.10](https://github.com/padavanonly/immortalwrt-mt798x-24.10)  
- Patches from this repository and the device-specific `.config` in the `/configs` folder are applied before compilation.  
