# 1. Beam Node Quick Start

## 1. Instructions before use

It is strongly recommended that after purchasing our modules, download our shell and print out a shell using your printer. Pay attention to adding support when printing. The model shell is shown in the following figure:[外壳下载链接](https://github.com/fiberpunk1/Beam-ESP32/releases/download/Beta-v0.1.8/shell-stl.zip)

![img](./images/shell.png)

> The beta version of Beam Node will send a G28 command to the printer when it is just powered up. If you test it, please be careful not to let the platform have anything. Or update our official version.

## 2. Get started quickly

### 2.1 assembly module

- Print housing
- Install OLED and SD card slot
- Introduction of interface line

### 2.2 Install BeamNexcus and set mailbox

1. Software installation and operation
Please start from this[链接](https://github.com/fiberpunk1/Beam-ESP32/releases)Download the installation package for our BeamNexus software:

![img](./images/download.png)

> Note: BeamNexus currently only supports windows versions
> Note: When running BeamNexus, run with administrator privileges (because SD card write permissions are required).

2. Set up a mailbox
First of all, we should choose Google Mailbox, which only supports Google Mailbox at present.![img alt ><](./images/sentry/1-4.png)

Then log in to your Google Browser on your browser. From this website, https://myaccount.google.com/lesssecureapps authorizes external software to log in to your Google mailbox. We suggest that you apply for a special prompt mailbox to perform this task.

![img alt ><](./images/sentry/1-5.png)

After setting up, finally click send test to send a test email to check whether you can receive the email normally. If you can, it means the setup is successful.

> Note: After setting the email prompt, there will be more emails. You'd better set up a separate email group for this kind of information. For information security, we also suggest that you apply for a special email to receive this kind of notification information.

The following figure shows setting the email sending strategy. You can set how often to take a picture and send an email, or set a print failure threshold. When this threshold is detected to be higher than a certain value, you can send an email to remind you (the premise of turning on the change function is that you turn on the Detector function).



###  2.3 Configure BeamNode Wifi + SD Card

First, plug your SD card and card reader into your computer:

![img](./images/sd-card.png)

After inserting the SD card, open BeamNexus and click the Setting button shown in the following figure:

![img](./images/beam-main.png)

After clicking, the window shown in the figure below pops up, where we want to fill in the Wifi name and password, and give your Beam Node module a device name (don't reuse the same device name on the LAN). The specific filling contents are shown in the following figure:

![image alt ><](./images/sd-wifi-2.png)

> Note 1: Sentry's distribution network mode is the same as the above steps, and it also uses the function SD card for distribution network.

> Note 2: If your computer does not have a wifi module, Scan Wifi will fail and prompt you to manually enter the ssid name of your router. If your wired network and wifi are on the same router, Beam Node can still be accessed.

After filling in the above, click Save To SD to save the relevant configuration file to the SD card. Pull out the SD card, insert the SD card into the Beam Node module as shown in the following figure, push it a little hard, and feel the spring rebound, indicating that the SD card is tightly inserted.

###  2.4 Install BeamNode module to 3D printer


As shown in the above figure, insert the SD card extension card of Beam into the card slot of 3D printing. The USB-A port of Beam is equivalent to the USB-A port of the computer and connected to the micro-usb port of the printer. In addition, the Type-C port on the left side of the Beam is used to supply power to the Beam module. Use a 5V Type-C adapter to power the Beam.

If it is just powered on, a red light will light up at first. If the red light flashes, it means that the SD card has not been found. After the distribution network is successful, the status display light will turn green. If the printer is also connected to the Beam module, the words Printer Connected will appear on the OLED of the Beam.


###  2.5 WiFi printing using BeamNexus

- Search Beam Node devices on the computer side
- WiFi controls 3D printer movement
- Upload files to SD card
- Sentry test (optional))

When using BeamNexus for the first time, if your computer does not have Wifi function (for example, you are using a desktop computer), you need the user to manually enter a target IP (the target IP can be the IP address displayed on any Beam Node module), and then BeamNexus will search all devices in the LAN where this IP is located. Manual input enables you to search for all devices when your PC and Beam Node module are on different network segments. For specific operation details, refer to the interface shown in the following figure:

![image alt ><](./images/set-ip.png)
<center>
<p>Image-2-5-1 set ip manually</p>
</center>

After completing the above setup, we click Search Device. After a period of time, the Beam Node module existing in the LAN will be listed in the following device list. Select an option and double-click to open the control panel of the corresponding module. In this control panel, we can realize file transfer, print management, progress and temperature monitoring. Please refer to the following animation:

![image alt ><](./images/scan.gif)
<center>
<p>Image-2-5-2 scan devices</p>
</center>

After searching for the device, select the name of the device you need to operate, and then double-click to pop up the following operation interface:

![image alt ><](./images/BeamNexcus-ui.png)
<center>
<p>Image-2-5-3 beam node control panel</p>
</center>

The operation panel above includes control area (upper left), file management area (lower left), monitoring area (upper right) and information display area (lower right). In the information display area (lower right area), you can click Update to get the Sentry devices you have searched for before (if you want to use Sentry here, please do not open the Sentry control interface in the main list). Once you've got the Sentry list, you can see some real-time printers in the Camera tab.

If the control command you send in the control panel does not control the printer, it is likely that the USB baud rate of Beam Node is different from that of your printer. Please refer to the description of serial baud rate in this document below.

### 2.6 Common Device Settings

#### 1. Serial port baud rate setting

Beam Node's factory default USB host baud rate is 115200. If your printer supports another baud rate, you may need to modify the baud rate.

First, according to the previous steps, search for the device, and then enter the control interface of the device, as shown in the following figure:

![image alt ><](./images/set-baudrate.png)
<center>
<p>Image-2-6-1 set baudrate</p>
</center>
Select the baud rate supported by your printer, and then click Set Baudrate to complete the setup. This setting only needs to be configured once, and Beam Node stores the serial baud rate you set. If you switch devices, remember that the corresponding baud rate should also be switched.

#### 2. Manual Switch SD Card Ownership Beam Node switches SD card ownership between esp32 and 3D printer through a switch circuit. After Beam Node initializes, it releases the SD card and lets the printer manipulate the SD card. Beam Node only takes up SD card when uploading, reading and deleting files, and SD card is controlled by printer at other times. In the picture interface of baud rate setting above (Imag-2-6-1), click ReleaseSD, the SD card will be manually released from Beam Node, and GetSD will be executed, and Beam Node will take over the usage rights of SD card from 3D printer.

#### 3. Send Gcode and view serial port return. First open the serial port printing terminal:![image alt ><](./images/wifi-serial.png)

This terminal will display the string returned by the printer. When there are multiple devices, you can listen by selecting a specific printer device in the drop-down box below the WifiSerialLog.

Once you open this window, you can send Gcode commands in a separate device control interface and view the printer's return.


### 2.7 Access the material cutting sensor

![image alt ><](./images/filament-sensor.png)
<center>
<p>Image-2-7-1 film sensor</p>
</center>

- Hardware access
- Software setup

As shown in the following figure, plug the socket terminal of the cutting material sensor into the GPIO port of BeamNode, and then fix the cutting material sensor on your 3D printer. Different 3D printers have different fixing methods, which can be fixed freely according to your needs.![image alt ><](./images/filament-install.png)
<center>
<p>Image-2-7-1 film sensor connect to beam node</p>
</center>


After fixing, we need to reconfigure the parameters of BeamNode. If you have selected "Enable Filament Detector" when you set up WiFi before, there is no need to do anything in this step.![image alt ><](./images/sd-wifi-2.png)

BeamNode will send the "M600 X0 Y0" command to the printer when it detects the broken material. If your printer does not support the M600 command, cut-off detection may not work properly (M600 is basically supported in Marlin 1.8 +).

## 3. Separate use of Sentry

If you only have one Sentry module, you can use it alone. Sentry provides serial pins that you can connect to the printer's motherboard if you have enough hands-on skills.

When Sentry is used as a separate module, you can also implement various print detections. This section describes how to use Sentry alone.

If you have already used BeamNode, Sentry is also very simple to use, and his distribution network is exactly the same as BeamNode's distribution network. But Sentry doesn't have an OLED, and after the network is configured, his IP address can only be known through BeamNexcus. The main operation steps are as follows:

1. Install and power up
2. Configure SD + WiFi
3. Configure mailbox
4. BeamNexcus search device
5. Use function Sentry for monitoring and management

First open the software and click Search Devices (please make sure the distribution network is complete). After searching for a while, the device will be displayed as follows:![img alt ><](./images/sentry/1-6.png)

Double-click the sentry you want to open, and the following interface will pop up:![img alt ><](./images/sentry/1-7-1.jpg)

Clicking capture test will take a picture and display it on the right side of the window. In the Gcode input field, enter the command you want the serial port to send, and sentry will send the corresponding command to the printer through the serial port. The Toggle Detector triggers detection and turns on print failure detection.


## 4. Update BeamNode firmware

To update BeamNode firmware, you need to download BeamFlash and BeamNode firmware respectively. The download link is as follows:

- [BeamFlash](https://github.com/fiberpunk1/Beam-ESP32/releases/download/Beta-v0.1.0/BeamFlash-Installer.exe)
- [ BeamNode firmware ](https://github.com/fiberpunk1/Beam-ESP32/releases)

After downloading and installing BeamFlash, link your BeamNode to your PC with the Type-C cable, open BeamFlash, and burn the latest downloaded BeamNode firmware as shown in the figure below.

![img alt ><](./images/update-bin.png)

> Note: If you update BeamNode's firmware, be sure to use BeamNexcus with the same version number