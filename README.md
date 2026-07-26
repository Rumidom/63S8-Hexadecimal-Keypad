# 63S8-Hexadecimal-Keypad
63S8 Hexadecimal Keypad Is a 6x3 serial/parallel Keypad with Cherry MX style switches, and interfaces for 8-bit computers using only 7400 logic chips.
<p align="center">
  <img src="https://github.com/Rumidom/53S8-Hexadecimal-Keypad/blob/main/PCB%20Layout%202026-07-23.png" />
</p>

## Features:
- UART interface on a IDC 3x2 connector.
- RS232 interface on a DB9 connector.
- Parallel interface on a IDC 6x2 connector.
- 6x3 hexadecimal keypad, pressing two keys will load the 8 bit register with a single byte.
- Two extra keys for carrige return and backspace, pressing CR or CLR will fill the 8bit register with ```0x0D``` or ```0x08``` respectively.  
- Once the register is full the keypad will set the ```BYTE_RDY``` pin to ```HIGH``` and wait for the register to be read.
- 3.3V or 5v operation.

## Writing on the keypad:
- The keypad should load the most significant hexadecimal digit first then the least significant digit.  
- Once the register is loaded the byte-ready LED will light up. if using in serial mode it should blink and reset automatically.
 
## Reading the keypad:
- The register can be read via the parallel port by:  
  1 - Reading the 8 parallel bits when the pin ```BYTE_RDY``` is ```HIGH```  
  2 - Then reseting the register by setting ```KEYPAD_RST``` to ```HIGH```  

- The register can be read on the serial ports via RS232 or UART by:  
  1 - Setting ```#SERIAL_EN``` ```LOW```.   
  2 - Reading the Serial output.
    
  (boundrate can be set using a jumper)  
  (boundrate Clock pin is also available on UART port)  
  (serial uses no parity, 8 data bits, 1 stop bit ```HIGH```, 1 init bit ```LOW```)  

### This circuit hasn't been tested yet.

## TODO:
- [X] Add a reset button to reset the keypad in parallel/manual mode
- [X] Reduce footprint if possible.
- [ ] Test.

## License:
This project is MIT licensed.

## Support
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/M4M41NQV7I)
