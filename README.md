###### Barebones-ATmega328P-Pu
Documentation for a basic barebones Arduino microcontroller circuit.  

###### Parts List
- Arduino Uno Board
- ATmega328P-PU
- LM7805C Voltage Regulator 
  - .33 uF, .1uF Electrolytic Capacitors  
- 16 MHz Crystal Oscillator *(2 or 4 pins)*
  - (2) 22uF Ceramic Capacitors
- Pushbutton 

###### Connections
| Arduino Pins   |  ATmega328P-PU  | Misc. Connections | 
| :------------: | :-------------: | :---------------: | 
|  DIG 10        |  Pin 1 (Reset)  | 
|  DIG 11        |  Pin 17         |
|  DIG 12        |  Pin 18         | 
|  DIG 13        |  Pin 19         |
|                |  Pin 1          | Pushbutton -> Gnd | 
|                |  Pin 7          | Vcc               |
|                |  Pin 8          | Gnd               |
|                |  Pin 9          | 22uF,16Mhz -> Gnd | 
|                |  Pin 10         | 22uF,16Mhz -> Gnd | 
|                |  Pin 20         | AVcc (Vcc)        |
|                |  Pin 21         | AREF (Vcc)        |
|                |  Pin 22         | Gnd               |

Note: 
- If you're using a 4 pin 16Mhz C. Oscillator, connect the output pin of the oscillator to Pin 9. (See Acknowledgement 2)

##### Acknowledgements
[1. Indepth Explanation](https://www.arduino.cc/en/Main/Standalone)  
[2. 4-Pin C. Oscillator](http://forum.arduino.cc/index.php?topic=368237.msg2538317#msg2538317)

