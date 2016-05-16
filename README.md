### Preface
This documents tracks my progress as I learn about the ATmega328P-PU microcontroller (aka. 328PPU). The "Barebones" aspect of this project involves breadboarding the 328PPU and slowly adding peripherals to it as required by different projects. By doing this, I hope to gain understanding of the architecture of the chip and hope to catch a glimpse of the process of designing a microcontroller. 

### Barebones 328PPU Build 
###### Parts List
- Arduino Uno Board (328PPU's AVRISP)
- ATmega328P-PU (Target uC)
- LM7805C Voltage Regulator
  - .33 uF, .1uF Electrolytic Capacitors  
- 16 MHz Crystal Oscillator (2 or 4 pins) 
  - (2) 22uF Ceramic Capacitors
- Pushbutton 

###### Instructions
1. Use the LM7805C, .33uF, .1uF to make a typical voltage regulator circuit. The regulator's 5V output will power the breadboarded 328PPU.  
2. Make the following connections: 

| Arduino Pins   |  ATmega328P-PU  | Misc. Connections | Notes |
| :------------: | :-------------: | :---------------: |:------|
|  DIG 10        |  Pin 1 (Reset)  | 
|  DIG 11        |  Pin 17         |
|  DIG 12        |  Pin 18         | 
|  DIG 13        |  Pin 19         |
|                |  Pin 1          | Pushbutton -> Gnd | 
|                |  Pin 7          | Vcc               |
|                |  Pin 8          | Gnd               |
|                |  Pin 9          | 22uF,16Mhz -> Gnd | See Note 3
|                |  Pin 10         | 22uF,16Mhz -> Gnd | 
|                |  Pin 20         | AVcc (Vcc)        |
|                |  Pin 21         | AREF (Vcc)        |
|                |  Pin 22         | Gnd               |


3. We now need to prepare the Arduino to upload the bootloader onto our blank 328PPU chip. Open and upload the "ArduinoISP" example sketch onto the Arduino Uno. Check again that the "board" under "tools" is Arduino Uno. Check again that "Port" corresponds to the port to which your arduino is connected. We're now ready to burn the bootloader onto the blank 328PPU. 
4. While the ArduinoISP sketch is running on the Uno, go to "Tools" -> "Burn Bootloader" on the Arduino IDE and wait until the IDE finishes burning the bootloader onto the 328PPU. After receiving a success/confirmation status, your blank 328PPU should contain the bootloader. This enables the 328PPU chip to be programed via the Arduino.  
5. **How to Upload a Program Onto 328PPU via "Arduino as ISP"**  
Make sure the connections in step 2 are made. We will upload a program to the breadboarded 328PPU by using the Arduino as an intermediary programmer (hence "Arduino as ISP"). Make sure the Arduino Uno is running the "ArduinoISP" sketch, then open the sketch that you wish to upload onto the 328PPU. To command the Arduino to upload the sketch onto the breadboarded 328PPU, hold ***shift** and click on the upload button (while holding shift, the button status display should toggle from "Upload" to "Upload Using Programmer"). 
After uploading is complete, the 328PPU should be programmed with the desired sketch. 


### Notes 
1. [Indepth Explanation of Barebones Arduino Build](https://www.arduino.cc/en/Main/Standalone)  
2. [4-Pin C. Oscillator](http://forum.arduino.cc/index.php?topic=368237.msg2538317#msg2538317)
3. If you're using a 4 pin 16Mhz crystal oscillator (as I did), connect the output pin of the oscillator to Pin 9. Otherwise connect a 2-pin 16Mhz oscillator across pin 9 and pin 10 of the 328PPU. See Note 2.
