# Parrot OS for Huawei MediaPad T3 10 (agassi)

A Linux port built using the postmarketOS kernel (v7.1.x), with custom patches for the **Huawei MediaPad T3 10 (agassi)**.

> [!NOTE]
> I am not an official developer working on this kind of project. I am only 15 years old, so please keep that in mind if something does not work as expected. If you encounter any issues, feel free to report them on XDA. However, please understand that I also have school and other responsibilities — this is just a hobby project!

---

<img width="4377" height="3347" alt="parrot_" src="https://github.com/user-attachments/assets/96acfcf9-a23f-4e4c-962b-9aef4000a7eb" />

## 🛠️ Features & Status

- **Audio:** Sound is working (not perfectly, but it works). Check `/usr/local/bin` for audio scripts if you want to improve it.
- **Volume Issues:** FreeTube audio can sometimes sound strange, with crackling similar to a radio. Use **VacuumTube** instead, which comes pre-installed.
- **Kernel & USB:** Uses the same postmarketOS kernel 7.1 as the Kali Linux port, with Ralink modules and added support for **RTL8812AU**. The `.dtb` is configured for USB host mode, so USB adapters should work.
- **USB Networking:** Due to the USB host mode modifications, USB networking does not work.
- **Wi-Fi:** If Wi-Fi does not start, check the `cust` partition on your tablet to locate the necessary `.ko.zst` files.
- **Compatibility:** Tested exclusively on **AGS-W09** (2 GB RAM / 16 GB storage). **Not tested** on AGS-L09.
- **Touchscreen:** Sometimes, the touchscreen module may fail to load properly during the first boot. After reaching the desktop, if the touchscreen is not working, perform a hard reboot by holding **Volume Down + Power**. This usually fixes the issue. It does not happen every time, but it is something to keep in mind.
- **Screen Rotation:** In the top-right corner of the panel, you will find an icon named **Rotate**. It rotates both the screen and the touchscreen axes simultaneously.
- **Gestures:** `touchegg` is configured as a background service. Touching the screen with two fingers acts as a right-click.
- **On-Screen Keyboard:** Sometimes, the on-screen keyboard may appear twice. This is a known issue.
- **Swap:** Uses a 1 GB swap file (`/swapfile`). It is recommended to leave it enabled, although you can delete it if storage space becomes critically low. The system may run less smoothly without it.

---

## ⚠️ Important Warnings & Partitioning

- **EDL Backup (Mandatory Precaution):** Before making any changes or flashing, always create a full EDL backup using:

  ```bash
  edl rl . --loader=firehose.mbn
  ```

- **Storage Optimization (Risky / Optional):** A potentially useful but risky tweak is to shrink the system partition to free up space (setting it to 1 MB and mapping its starting point correctly in the partition layout). Only attempt this if you know exactly what you are doing!

---

## 📥 Download & Installation

- **USER PASSWORD:** `parrot`
- **DOWNLOAD:** [Download userdata_parrot.zip from MEGA](https://mega.nz/file/rS4V3BwJ#ydxd3YqGNtUgTfQMXwU15J-cHpr2E3Gk-cuJJFEwSd4)
- **USERDATA IMAGE:** `userdata.img` (inside `userdata_parrot.zip`)

### Flash Instructions

1. Download `userdata_parrot.zip` from the link above and extract it. Inside the archive, you will find `userdata.img`.

2. Flash `userdata.img` via fastboot to the `userdata` partition so `lk2nd` can recognize it:

   ```bash
   fastboot flash userdata userdata.img
   ```

3. Flash the boot image (**this only works after flashing lk2nd**):

   ```bash
   fastboot flash boot lk2nd_agassi.img
   ```

   *(Note: If the tablet fails to boot, try flashing `lk2nd_agassi.img` into the recovery partition as well.)*

---

*Sorry for my bad English. I am from Romania, and I am still learning. Thanks for understanding and for supporting this little hobby project!*
