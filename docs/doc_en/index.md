## 1. Introduction to the Beam Project

<div align=center>
<img src="./images/BeamNexcus-ui.png"  />
</div>

Beam series products are dedicated to making 3D printing more intelligent, and realize the intelligent transformation of 3D printing through IOT technology and machine learning technology. Make the whole 3D printing system more intelligent through sensors such as image, sound and acceleration. Core hardware products include Beam Node and Beam Sentry. With Beam Nexus control software, software and hardware are combined to realize a complete set of intelligent process.


## 2. Introduction to Beam Node Module

<div align=center>
<img src="./images/module-1.jpg" />
</div>

Beam Node is a module developed for FDM, which solves the problem that most FDM devices have WiFi transfer files and WiFi control printing. Unlike the strawberry pie, the beam module uses a simpler microprocessor to handle these tasks.

- OLED display screen
- WiFi transfer file
- WiFi controlled printing
- Easy access to printer without disassembly and wiring
- Rich extension interface, which can extend other sensors
- Mail print notification


Basic Parameter Specifications for Beam:

| 参数名称   |Specification| 描述          |
|--------|----------------|-------------|
| 模块尺寸   |7.4 x3.5 cm|             |
| 显示     |OLED (128X32)|             |
| 存储     |SD card|             |
| 供电     |Type-C 5V|             |
| 与打印机连接 |USB + SD card sharing| USB和SD卡同时连接 |
| 外壳     |3D printing| 提供开源模型     |
| 对外扩展接口 |Serial port, I2C, 2 GPIO|             |



## 3. Introduction to the Beam Sentry Module

<div align=center>
<img src="./images/sentry/1-1-1.jpg" />
</div>

- WiFi image transmission
- Serial port controlled printer
- Visual inspection printing failed
- Visual detection of smoke and flame
- Mail shooting notification regularly, event triggering mail notification

Beam Sentry is a WiFi camera specially used in the field of 3D printing. With the use of Beam Nexus, it can realize WiFi serial port control and printing failure detection. Beam Sentry currently provides UART, I2C and IO ports, on which users can expand a series of peripherals and sensors such as broken material detection, temperature sensors and relay switches.


## 4. Introduction of Beam Nexus Software

<div align=center>
<img src="./images/beam-main.png" />
</div>

Beam Nexus is an application software for managing Beam series hardware. It can manage multiple Beam modules at the same time, which means it can manage multiple printers. In addition to WiFi management, Beam Nexus also realizes email notification, machine learning reasoning and other functions. He is the control center of Beam series products.

The following figure shows print failure detection using BeamNexcus:

<div align=center>
<img src="./images/sentry/1-2-1.jpg" />
</div>

<div align=center>
<img src="./images/sentry/1-3-1.jpg" />
</div>
