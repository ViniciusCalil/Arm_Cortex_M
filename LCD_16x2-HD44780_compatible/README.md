# LCD 16x2 library.

The zip file "LCD_16x2-HD44780_compatible.zip" has a simple library to allow a microcontroller from STM32F4 and STM32F7 families to drive a LCD with 2 lines and 16 characters.

With this library, the LCD board (driven by a HD44780 compatible controller) operates in 4 bit mode. It means that only four data pins and the three control pins (WR, EN, and RS) require connections to the microcontroller GPIO pins.

The LCD also requires voltage source connections for backlight LED and contrast potentiometer.

The library is indeed only the files "HD44780_16x2.c" and "HD44780_16x2.h". But the zip file has also a "Sample_application" subdirectory, with two files (main.c and main.h) that shows how to use the library.

To enable any project to use this library:

    - the "HD44780_16x2.c" file must be included in the project (in the "./Core/Src/" subdirectory, if you whish);

    - the "HD44780_16x2.h" file must be included in the project (in the "./Core/Inc/" subdirectory, if you whish).

------------------------------------------------------------------------
Usage:
------

The FIRST step is to call function "HD44780_GPIO_ConfigOUT_4bit()". This function configures the STM32F microcontroller GPIO pins that will be connected to the LCD module. The arguments of this function are seven sets of "GPIO_PORT" followed by a "GPIO_PIN". The first pair (of "port, pin") must identify the microcontroller pin connected to the "RS" pin of the LCD module. The second pair identifies the microcontroller pin connected to the "RW" pin of the LCD module. Third pair is connected to "En" pin; fourth pair to D4, fifth pair to D5, six pair to D6, and seventh pair to D7.

The SECOND step is to call function "HD44780_init()". This function initializes the LCD module to operate with: four bit data mode, 2 lines of 16 characters, 5x8 dot matrix per character.

After those two steps, you can write in the LCD using the follow functions:

"HD44780_SetCursorPosition()"  to set the position where the next character will be displayed;

"HD44780_SendChar()" to display a character at the actual cursor position;

"HD44780_SendString()" to display a complete string starting by the actual cursor position;

"HD44780_Clear()" to clear all the display contents.

------------------------------------------------------------------------
The Sample Application:
------

In the "Sample_application" subdirectory there is a "README.txt" file with instructions.

When using the sample application (main.c and main.h files) with a microcontroller of the STM32F7 family:

    - in the "main.h" file, the preprocessor directive ' #include "stm32f4xx_hal.h" ' must be changed to ' #include "stm32f7xx_hal.h" '.

------------------------------------------------------------------------
Circuit Mounting:
------

In the "README.txt" file of the "Sample_application" subdirectory, there is a section ("Pins connections...") that explains how to interface the microcontroller pins with the LCD module pins. A possible mounting configuration is presented in the "main.c" file (and showed in README.txt). 



Vinicius Calil, 2022/07/25
