# :material-usb: Accessing via USB

!!! danger "Do not use MTP while the device is busy"

    You should **never** modify the files on your device via MTP while the device is busy (e.g., while playing a game, while scraping, etc.). The file system on your device should **not** be manipulated on-device and via MTP at the same time to make sure it will not be corrupted.

KNULLI supports two different methods of USB transfer: **MTP** and **ADB**. To enable a USB mode,

* press ++"Start"++ to bring up the main menu
* go to *Device Settings*
* find *USB Mode*
* set it to
    * *MTP* for Media Transfer Protocol (recommended)
    * *ADB* for Android Debug Bridge (for advanced users)
    * *Off* to disable USB access (default)

!!! info "Don't forget to update your gamelists!"

    Once your data is completely transferred, make sure to update your gamelists to make the data available. You can do so by pressing ++"Start"++ to open the main menu, then open *Game settings* and select *Update gamelists*. KNULLI will rescan all game folders and identify all the games you added to make them available in EmulationStation.

## MTP (Media Transfer Protocol)

!!! warning "exFAT formatting required to use MTP from a Windows computer"

    If you want to access your SD card via MTP, make sure the SD card is formatted with exFAT (it is by default).

Using MTP is pretty straight forward: After enabling MTP as explained above, simply plug your device to your computer. Your [userdata folder](../game-storage) should appear automatically in *My PC* like every other thumbdrive or external hard disk drive. You may now copy your files. Just do **not** forget to **properly eject**. It is never a good idea to unplug a USB data storage without ejecting it first!

## ADB (Android Debug Bridge)

If [network transfer](../network-transfer) is not an option for you, but you still want to rely on the ext4 file system, you can set up Android Debug Bridge (ADB) to access your KNULLI device via USB connection. However, this is a bit more challenging than going through MTP as you need third-party software to establish the ADB connection.

### Install ADB

To access your device via USB, you will need two download and install

* the [ADB SDK Platform tools](https://developer.android.com/tools/releases/platform-tools?hl=de#downloads) (**Memorize** the location where you installed it!)
* an ADB browser, e.g. [ADB Explorer for Windows](https://apps.microsoft.com/detail/9ppgn2wm50qb)

#### Configure ADB Explorer

After installing *ADB SDK Platform tools* and *ADB Explorer*, you need to point *ADB Explorer* to the `adb.exe` file inside the folder where you installed the *ADB SDK Platform tools*. Next, make sure to select *Disk Usage Only* as your *Progress Method*.

<table>
  <tr>
    <td>
      <img src="/_inc/images/play/add-games/add-games-adb-001.png">
      <p><strong>Step 1: </strong>Open <em>ADB Explorer</em> and click the <em>Change</em> button to select the path to your ADB installation. Point to the <code>adb.exe</code> file of your <em>ADB SDK Platform tools</em> installation.<p>
    </td>
    <td>
      <img src="/_inc/images/play/add-games/add-games-adb-002.png">
        <p><strong>Step 2: </strong>Select <em>Disk Usage Only</em> as your <em>Progress Method</em>.</p>
    </td>
  </tr>
</table>

### Transfer your data

Now that you have set up your *ADB Explorer*, you may use it to

* add files to your device (**push**).
* get files from your device (**pull**).
* delete files from your device.

#### Browsing your device with ADB Explorer

Before you start adding or removing files, take a moment to understand how to navigate. In your *ADB Explorer*, your KNULLI device will present itself as *Nexus 4* at the top-left of the *ADB Explorer* window.

* Click *Nexus 4* to expand and then *Browse*.
* In the next menu, make sure to double-click *Root*, which will take you to the root folder of your KNULLI device.
* From here, scroll down and double-click `userdata` to enter your [userdata folder](../game-storage).
* You can use the *Up* symbol or the *Back* arrow in the address bar to return to the previous folder.

<table>
  <tr>
    <td>
      <img src="/_inc/images/play/add-games/add-games-adb-003.png">
      <p><strong>Step 1: </strong>Click <em>Nexus 4</em> to expand the device and click <em>Browse</em> to start browsing.<p>
    </td>
    <td>
      <img src="/_inc/images/play/add-games/add-games-adb-004.png">
        <p><strong>Step 2: </strong>Double-click <em>Root</em> to enter the root folder of your KNULLI device.</p>
    </td>
  </tr>
  <tr>
    <td>
      <img src="/_inc/images/play/add-games/add-games-adb-005.png">
      <p><strong>Step 3: </strong>Scroll down and double-click <code>userdata</code> to enter the <code>userdata</code> folder.<p>
    </td>
    <td>
      <img src="/_inc/images/play/add-games/add-games-adb-006.png">
        <p><strong>Step 4: </strong>You have reached the <code>userdata</code> folder.</p>
    </td>
  </tr>
</table>


#### Adding/retrieving/deleting files to/from your device

In ADB, **adding** something to a device is called **push** while **retrieving** something from a device is called **pull**.

If you want to push or pull a device to/from a folder, navigate to said folder and right-click it to bring up the context menu. Here, you will find options to push, pull, and even delete files.

<img src="/_inc/images/play/add-games/add-games-adb-007.png">

### Establish a command line connection

ADB doesn't only enable file transfers but also allows command line access to your KNULLI device. The ADB command line is very limited in comparison to an SSH shell, however, when SSH is not an option, ADB can still be a handy tool to access your device.

To establish an ADB shell connection from a Windows computer, simply locate the folder of your *ADB SDK Platform tools* installation and run

```
adb.exe shell
```

from a Windows Terminal (PowerShell or CMD) to get command line access to your KNULLI device.
