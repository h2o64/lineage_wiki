---
sidebar: home_sidebar
title: Install Lineage on tomato
folder: info
# name of the page (/{{permalink}}.html)
permalink: tomato_install.html
device: tomato
---

{% include warning.html content="To install LineageOS (cm-13.0/cm-14.1) build you must install 12.1-YOG4PAS8A4-tomato baseband, see bottom of the page for more details" %}
{% include templates/device_install.md %}

## Installing correct modem baseband

{%
{% include note.html content="The steps below only need to be run once per device." %}
{% include note.html content="To proceed, your bootloader must be unlocked" %}

1. Make sure your computer has working [fastboot and adb](adb_fastboot_guide.html).
2. Enable [USB debugging](adb_fastboot_guide.html#setting-up-adb) on your device.
{% unless site.data.devices[page.device].no_oem_unlock_switch %}
3. Enable OEM unlock in the Developer options settings on the device, if present.
{% endunless %}
4. Connect the device to your PC via USB.
5. Open a terminal on the PC and boot the device to fastboot mode by typing:

        adb reboot bootloader

    {% if site.data.devices[page.device].download_boot %}
    You can also boot into fastboot mode via a key combination:
    
    * {{ site.data.devices[page.device].download_boot }}
    {% endif %}
6. Once the device is in fastboot mode, verify your PC finds it by typing:

        fastboot devices

   If you see `no permissions fastboot` or `<waiting for device>`, try running `fastboot` as root/Administrator.
7. Download the give NON-HLOS.bin file from [here](https://www.androidfilehost.com/?fid=745425885120710873)
6. Enter the following command

        fastboot -i 0x1ebf flash modem NON-HLOS.bin

%}
