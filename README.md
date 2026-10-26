# STM32 UART LED Controller

An embedded systems project developed in C using the STM32 Hardware Abstraction Layer (HAL). The project demonstrates UART serial communication, GPIO control, and command processing on an STM32 microcontroller using the Wokwi simulator.

## Live Simulation

**[Click here to run the STM32 UART LED Controller in Wokwi](https://wokwi.com/projects/478540786550746113)**

The complete source code and hardware configuration are available directly in the Wokwi project.

## Features

- **UART Communication:** Transmits and receives serial data at 115200 baud.
- **Command Processing:** Interprets text commands received through the UART serial interface.
- **GPIO Control:** Controls an LED connected to GPIO pin PA5.
- **Configurable LED Blinking:** Converts user-supplied numeric input into an integer to determine the number of LED blinks.
- **Serial Echo:** Echoes received commands back to the serial monitor.
- **STM32 HAL:** Uses STM32 HAL functions for UART communication, GPIO configuration, and timing.

## Supported Commands

| Command | Description |
|---|---|
| `LED ON` | Turns the LED on |
| `LED OFF` | Turns the LED off |
| `LED BLINK 5` | Blinks the LED 5 times |
| `LED BLINK 10` | Blinks the LED 10 times |

Each blink consists of 500 milliseconds ON and 500 milliseconds OFF.

## How to Run

1. Click the Wokwi simulation link above.
2. Click the green **Start Simulation** button.
3. Open the Serial Monitor.
4. Enter one of the supported commands and press Enter.
5. Observe the LED responding to your command.

## Technologies Used

- **Language:** C
- **Microcontroller:** STM32 Nucleo-C031C6
- **Framework:** STM32 HAL
- **Simulation:** Wokwi
- **Interfaces:** UART (USART2), GPIO

## Technical Implementation

The project uses USART2 configured for 115200 baud, 8 data bits, no parity, and 1 stop bit (8N1).

UART reception uses `HAL_UART_Receive()` to receive one byte at a time. Incoming characters are stored in a buffer until a newline character is received.

The program compares the received command against supported instructions using `memcmp()`. For blinking commands, `atoi()` converts the numeric portion into an integer.

LED control is implemented using `HAL_GPIO_WritePin()`, while `HAL_Delay()` determines the blinking interval.

The current implementation uses blocking UART reception and delays.
