# My-minimal-Arduino-Nano-board
I made this development board to use in prototypes which I want for a long time. This will save me a lot of money and equal compatibility.
![op2](https://user-images.githubusercontent.com/97245507/224400651-359f8973-029a-4e58-9aeb-083d9bc8fe90.png)

Sometimes I must prototype my projects to kept them working for a long time. And most of the work is Around Arduino specially atmega328p microcontroller. It is an 8-bit microcontroller which can work up to 20Mhz frequency. On the Arduino hub there are a lot of sensor interfacing tutorial and free sketches you can access and repeat the projects. So that you can get familiar with the working and coding and design your own embedded system in future. But sometimes I need those prototype projects for a long run and in that case having only one Arduino shield and program it in different ways is so irritating. Arduino boards costs much than the microcontroller unit.
![mini_IMG_5356](https://user-images.githubusercontent.com/97245507/224400868-9961c6c0-7584-44a3-b278-810f8c523dc0.png)

That’s why the idea of minimal Arduino board comes into my mind. And to keep it simple and fully compatible I removed all the protection, programming electronics stuff. And this time I want to go with the DIP version of microcontroller which costs less than SMT. The reason to make the Arduino board minimal is to reduce the overall cost and pin compatibility with Arduino Nano. In this way it can directly replace the Arduino Nano board.
<img width="973" alt="ice_screenshot_20230310-204529" src="https://user-images.githubusercontent.com/97245507/224400919-78a92a59-55c1-4327-bf5d-7726824294f2.png">

JLCPCB is not just a leading PCB prototype and assembly service provider, but they are also committed to promoting education and innovation in the field of electronics. They offer various initiatives and programs to support the maker and engineering communities. They also offer a Community Support Program that provides resources and technical support to makers and engineers.

Components required:
![mini_IMG_5357](https://user-images.githubusercontent.com/97245507/224400986-4b563158-d72a-48fe-92a5-1d239faf6f4c.png)

Atmega328P DIP
16MHz crystal
AMS1117 5V
100nf capacitor
SMD LED
10k,1k resistor
Custom PCB from JLCPCB

Circuit diagram:

Eliminating the serial programmer, power and protection circuit. We only need a very few things to assemble. So first I complete the microcontroller section with 10k pull up resistor on reset pin. Eliminating the power section can’t be the solution that why I kept a bridge of protection and power with Ams1117 5v regulator IC.
<img width="497" alt="ice_screenshot_20230308-231851" src="https://user-images.githubusercontent.com/97245507/224401076-12878b62-33ad-4617-ba4a-f1659026d537.png">

I also added only one LED with 1k resistor to the D13 pin which helps to troubleshoot if there is any fault in the PCB or microcontroller. 100nf capacitor are used to reduce the power lines noise. And finally I added the programming headers for the external universal programmer.

PCB and Gerber files:
<img width="726" alt="op" src="https://user-images.githubusercontent.com/97245507/224401207-8f99ae84-adf8-4f25-81ae-9fb99b44c2fd.png">

I designed the PCB keeping the pin compatibility and form factor of Arduino nano in mind. I placed the USB type C to provide power to the whole unit.
I made this schematic in EasyEDA and converted the PCB into Gerber file. You can upload this Gerber file to JLCPCB to order the same PCB. If you wan to use the same designs then the links to Gerber file including BOM and CPL is here.
![mini_IMG_5360](https://user-images.githubusercontent.com/97245507/224401372-30bceef0-4dd7-4c80-95ea-2dd09c3e158f.png)

JLCPCB is the only PCB manufacturer providing 5pcs of 2layer PCB in just $2. You can also try SMT service all the required files are shared above. Sign-up now and get new user coupons of worth $54.

Burning bootloader:

To burn the bootloader the SPI pins of Arduino are used which is different from the programming serial pins. New Arduino microcontroller do not come with pre-burned bootloader. So to specify the input/output, booting menu and subroutines we have to burn the chip with any working and compatible board bootloader.
<img width="353" alt="Untitled" src="https://user-images.githubusercontent.com/97245507/224401512-5a0c4d21-4086-4e57-b219-db15f7c9f921.png">

Just wire the two boards as shown in the figure above and burn the bootloader from Arduino IDE. It will take few seconds and after successful attempt give a notification.

Programming the Arduino:
![mini_IMG_5369](https://user-images.githubusercontent.com/97245507/224401792-9a8fba8d-16b3-4590-a919-4f3765846b0f.png)

Now to program the board I designed a separate universal programmer which directly plug into the programming headers and uploads the sketch without any external circuit. To know more about the programmer, follow this article: Universal USB to Serial programmer for Arduino.

Testing with Arduino:

Plug the Programmer into the headers and then select the COM and board settings in Arduino IDE. Hit simply on upload and get you Arduino programmed within seconds. This minimal board may save you a lot of money and it is fully working development board. Just build the universal programmer once and program the different boards with same.
