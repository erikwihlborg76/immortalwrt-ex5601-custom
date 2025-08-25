# Extra Packages in Custom ImmortalWrt Config

Compared to stock OpenWrt, your build adds:

- **SQM** CAKE, sqm-scripts, LuCI sqm app (not enabled).
- **MTK proprietary Wi-Fi + acceleration stack** mt_wifi, warp, hnat, conninfra, mtk-smp, hqos utils, mtwifi-cfg, turboacc-mtk.
- **Convenience utilities** ca-certificates, nano, iperf3.
- **LuCI extensions** for bandwidth, turboacc, MTK Wi-Fi, eqos.
- **Wireless regulatory tools** regdb + legacy wireless-tools

---

## Extra packages enabled

### Base / utilities

- **ca-certificates** System CA root bundle (for HTTPS, TLS verification).
- **datconf / datconf-lua** MediaTek proprietary configuration utilities.
- **iw** Modern Wi-Fi CLI tool.
- **iwinfo** -- OpenWrt Wi-Fi info library/CLI.
- **kvcedit** -- MediaTek configuration editor.
- **lua-cjson** Fast JSON support in Lua (used by LuCI, mtwifi-cfg, etc).
- **nano** Text editor.
- **iperf3** Network performance testing tool.

### 🔹 Networking / acceleration

- **iptables-mod-ipopt** -- iptables "ipopt" extension.\
- **kmod-ipt-ipopt** -- kernel module for iptables "ipopt" matching.\
- **kmod-ipt-nat** -- kernel NAT support (separate from base
    "iptables").\
- **kmod-ipt-offload** -- flow offloading for iptables.\
- **kmod-nf-flow** -- netfilter flow table support.\
- **kmod-sched-cake** -- CAKE Smart Queue Management.\
- **kmod-sched-core** -- core kernel scheduler for traffic shaping.\
- **sqm-scripts** -- userspace scripts to configure CAKE/SQM.

### 🔹 MediaTek proprietary drivers / support

- **kmod-conninfra** -- MediaTek connectivity infrastructure.\
- **kmod-mediatek_hnat** -- MediaTek hardware NAT driver.\
- **kmod-mt_wifi** -- proprietary MediaTek Wi-Fi driver.\
- **kmod-warp** -- WARP acceleration driver.\
- **mtk-smp** -- SMP helper utilities for MTK.\
- **mtkhqos_util** -- HQoS utilities for MediaTek chips.\
- **mtwifi-cfg** -- MediaTek Wi-Fi config backend.\
- **wifi-dats / wifi-scripts** -- MediaTek Wi-Fi dats/scripts support.

### 🔹 LuCI web UI packages

- **luci-app-eqos-mtk** MTK eQoS management app.\
- **luci-app-mtwifi-cfg** LuCI frontend for MTK Wi-Fi config.\
- **luci-app-sqm** LuCI frontend for SQM.\
- **luci-app-turboacc-mtk** TurboACC MTK acceleration control.\
- **luci-app-wrtbwmon** Bandwidth monitor.

### 🔹 TurboACC specifics

- **TURBOACC_INCLUDE_NO_FASTPATH** Disables fastpath inside TurboACC, while keeping other acceleration.

## ⚙️ Toolchain / optimization toggles

- `CONFIG_USE_GC_SECTIONS=y` Remove unused sections during link.
- `CONFIG_USE_LTO=y` Enable link-time optimization.
- `CONFIG_TARGET_OPTIMIZATION="-O2 -pipe -mcpu=cortex-a53+crc+crypto"` tuned compiler flags for MT7986 (Filogic).
