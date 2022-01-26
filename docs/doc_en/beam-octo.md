## 1. API interface description

This document is used to describe the API design of BeamNode module.

---

### 1.Looking for device API

** Brief description **

- Provides an http API, lets the client scan sends, if ESP32 receives this API, will return own device name
- If it has been connected before, it will return the status of the current device

** Request URL **
- ` http://192.168.1.133:88/find `

** Request mode **
- GET 

** Parameter **

- None

** Return to the sample **

```
 Beam-ESP32-Name:192.168.1.133:PRINTING
```
Note: If it is in print, it will return the following PRINTING. For the first connection, it will not return the change string

---

### 2. Get file directory information

** Brief description **

- Get all the file directory information in SD card

** Request URL **
- ` http://192.168.1.133:88/list?dir=/ `
  
** Request mode **
- GET

** Parameter **
- None
** Return to the sample **


```
[
    {"type":"dir","name":"/System Volume Information"},
    {"type":"file","name":"/castle.zip"},
    {"type":"file","name":"/config.txt"}
]
```

** Returns parameter description **

|Parameter name|类型|说明|
|:-----:  |:-----:|-----                           |
|type |字符串   |The type, file or directory of the current name|
|name |字符串   |File or directory name|

** Remarks **

- The current ESP32 file system does not support folder access, so all printed files should be placed under the root directory of the sd card

---

### 3. Upload a file

** Brief description **

- User uploads files

** Request URL **
- ` http://192.168.1.133:88/edit `
  
** Request mode **
- POST

** Parameter **

- Upload a file as a form

** Return to the sample **

- Upload complete, return ok

** Returns parameter description **

- None

** Remarks **

- None

---

### 4. Delete a file

** Brief description **

- User deletes files in sd card

** Request URL **
- ` http://192.168.1.133:88/remove?path=/xxx.gcode `

** Request mode **
- DELETE

** Parameter **

- Specify path=/xxx.gcode in the url, which is the file to delete

** Return to the sample **
- Delete complete, return ok

** Returns parameter description **
- None

** Remarks **
- None

---

### 5. Send the PC address to ESP32, set up the socket and connect to BeamNexcus

** Brief description **

- Send the IP address of PC to ESP32, ESP32 will create a socket to connect with the socket of PC, so that a long connection can be established, ESP32 can actively send information to PC, notify him to do something

** Request URL **
- ` http://192.168.1.133:88/pcsocket?ip=192.168.1.1 `

** Request mode **
- GET

** Parameter **
- Specify the PC's own IP address in the url

** Return to the sample **
- Create complete, return ok

** Returns parameter description **
- None

** Remarks **
- None

---

### 6. Send Gcode control instructions

** Brief description **

- Use url to send a Gcode instruction to ESP32, which will send it to the printer as soon as it receives it

** Request URL **
- ` http://192.168.1.133:88/gcode?gc=G28 X Y `

** Request mode **
- GET

** Parameter **
- Specify the Gcode instruction to send in the url

** Return to the sample **
- Create complete, return ok

** Returns parameter description **
- None

** Remarks **
- None

---

### 7. Start printing ** Brief Description**

- Specify a file contained in an sd card in the url and notify esp32 to print

** Request URL **
- ` http://192.168.1.133:88/print?filename=/xxx.gcode `

** Request mode **
- GET

** Parameter **
- Specify the Gcode instruction to send in the url

** Return to the sample **
- Execution is complete and returns ok

** Returns parameter description **
- None

** Remarks **
- The printed files are all selected from the list of sd card files obtained earlier

---

### 8. Control Print Pause, Resume, Cancel** Brief Description**

- Control printer printing, pause, cancel and resume through url

** Request URL **
- ` http://192.168.1.133:88/operate?op=PAUSE `

** Request mode **
- GET

** Parameter **
- PAUSE 
- RECOVER
- CANCLE

** Return to the sample **
- Execution is complete and returns ok

** Returns parameter description **
- None

** Remarks **
- None

---

### 9. Gets the status of the printer

** Brief description **

- Gets some status strings of the printer, including: nozzle temperature, hot bed temperature, total number of layers, and current number of printed layers

** Request URL **
- ` http://192.168.1.133:88/status`

** Request mode **
- GET

** Parameter **
- None

** Return to the sample **
- Execution is complete and returns ok

** Returns parameter description **
- Returns some column strings. After the front end gets these data, it needs to use regularity to get the information it wants. A typical return string is as follows:


```
;LAYER_COUNT:90,;LAYER:4,
B: 23.4 /40  T: 100.3/210

```

** Remarks **
- What is returned here is the content directly returned by the printer, which belongs to direct forwarding. This url can be sent every few seconds to update the display status of the front end



## 2. Introduction to OctoBeam Python Library

![img alt ><](./images/final-framwork.png)

The OctoBeam Python library provides a Python interface to implement the BeamNode control interface mentioned in the previous chapter. Through OctoBeam, users can talk directly with BeamNode and get various key information. OctoBeam github address:https://github.com/fiberpunk1/OctoBeam