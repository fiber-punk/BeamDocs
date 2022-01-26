#### 1.Run the BeamNexus hint "MSVCP140. dll not found" "VCRUNTIME140. dll not found # # # #

Some Windows systems will prompt the above errors. If they appear, please refer to the following links:

https://docs.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170

Download the latest C + + Redistributable installation package.

- [ARM64](https://aka.ms/vs/17/release/vc_redist.arm64.exe)
- [X86](https://aka.ms/vs/17/release/vc_redist.x86.exe)
- [X64](https://aka.ms/vs/17/release/vc_redist.x64.exe)

#### 2. My BeamNode can't connect to WiFi. What is the reason?

Possible reasons:

- SD card distribution failed, BeamNexus was not running with administrator privileges, resulting in SD card writing failure
- BeamNode only supports 2.4 G networks
- Too far from the router, the wifi signal is too weak

#### 3. What models does BeamNode support?

This depends on how the USB to serial port of your printer's motherboard is realized. At present, the serial port to USB mode supported by BeamNode includes the following:
- CH340/CH341
- FT232
- CP2102
- STM32 CDC USB Device

It should be noted that. BeamNode is currently testing only Marlin firmware, Pursa firmware has not been tested. In addition, you need to determine what the USB serial port baud rate of your printer is, and you need to set the corresponding baud rate value on the upper computer.

#### 4. What sensors can BeamNode connect to?

BeamNode provides two GPIO ports, one I2C port and one serial port. At present, the only officially supported sensor is the cut-off sensor. Various sensors such as sound and gyroscope will be added later. You can pay attention to our github source code for more information.

#### 5. Why can't I find my Beam device on my LAN?

Make sure your PC is on the same LAN as the Beam device. If it is not the same LAN, you need to manually specify the IP of the Beam device. Refer to QuickStart for instructions on connecting to a network.

In addition, if your computer uses VPN, it may also affect BeamNexus search devices

#### 6. Why can't BeamNexus send mail?

There are two reasons:
- Please check whether the Google Mail account has the unauthenticated device login license enabled. Refer to the instructions in QuickStart
- Using VPN may also cause BeamNexus to fail to send mail
- Your firewall has BeamNexus set up and cannot send mail.

#### 7. BeamNuxus' native reasoning capability causes crash? If you choose Openvino for local reasoning, but your PC is not Intel and predates the 6th generation processor, then an exception will occur. At this point, it is recommended that you use pure CPU instructions for reasoning.




