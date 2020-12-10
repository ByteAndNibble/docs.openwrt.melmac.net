<!-- markdownlint-disable MD030 -->

# Alternative Partition Reboot Web UI (luci-mod-alt-reboot)

## Description

This package allows you to reboot to alternative partition on supported (dual-partition) routers. This package overwrites default Reboot (System --> Reboot) page.

## Supported Devices

Currently supported devices include:

-   Linksys WRT1200AC
-   Linksys WRT1900AC
-   Linksys WRT1900ACv2
-   Linksys WRT1900ACS
-   Linksys WRT3200ACM
-   Linksys E4200v2
-   Linksys EA4500
-   Linksys EA8500

If you're interested in having your device supported, please check [OpenWrt Forum Support Thread](https://forum.openwrt.org/t/web-ui-to-reboot-to-another-partition-dual-partition-routers/3423).

## How to install

Install `luci-mod-alt-reboot` package from Web UI or run the following in the command line:

```sh
opkg update
opkg --force-overwrite install luci-mod-alt-reboot
```

If the `luci-mod-alt-reboot` package is not found in the official feed/repo for your version of OpenWrt/LEDE Project, you will need to add a custom repo to your router following instructions on [GitHub](https://docs.openwrt.melmac.net/#on-your-router)/[jsDelivr](https://cdn.jsdelivr.net/gh/stangri/docs.openwrt.melmac.net/README.md#on-your-router) first.

## How to uninstall

Run the following commands in ssh session to your router:

```sh
cp /rom/usr/lib/lua/luci/controller/admin/system.lua /usr/lib/lua/luci/controller/admin/system.lua
cp /rom/usr/lib/lua/luci/view/admin_system/reboot.htm /usr/lib/lua/luci/view/admin_system/reboot.htm
rm -rf /var/luci-modulecache/; rm -f /var/luci-indexcache;
```

## Notes/Known Issues

-   When you reboot to a different partition, your current settings (Wireless, etc.) will not apply to a different partition. Different partitions might have completely different settings and firmware.
-   If you reboot to a partition which doesn't allow you to switch boot partitions (like stock Linksys firmware), you might not be able to boot back to OpenWrt/LEDE Project unless you reflash it, loosing all the settings.
-   Some devices allow you to trigger reboot to alternative partition by interrupting boot 3 times in a row (by resetting/switching off the device or pulling power). As these methods might be different for different devices, do your own homework.

## Thanks

I'd like to thank everyone who helped create, test and troubleshoot this package. Without contributions from [@hnyman](https://github.com/hnyman), [@jpstyves](https://github.com/jpstyves) it wouldn't have been possible.

<!-- markdownlint-disable MD033 -->
<script defer src='https://static.cloudflareinsights.com/beacon.min.js' data-cf-beacon='{"token": "911798f2c34b45338f8f8182830a3eb6"}'></script>
