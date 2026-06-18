# UART-Driver
Description:
This repository contains a bare-metal UART driver specifically developed for the STM32F411 and HC-06 Bluetooth module.

I have used this reference sheet to build this project
This[STM32 Reference Manual.pdf](https://github.com/user-attachments/files/29073828/STM32.Reference.Manual.pdf)

This photo shows how my system works
<img width="921" height="2048" alt="WhatsApp Image 2026-06-18 at 05 00 42" src="https://github.com/user-attachments/assets/9d3c9539-49ca-488b-9678-5e31cc88cde1" />

## Specifications:

I have built this project with PA9 and PA10. 
PA9 --> TX
PA10 --> RX
Clock Speed : 16MHZ (Default)
Baud Rate --> 9600

### Electrical Noise Prevention (Pull-Up Resistors):
In UART communication, pins must generally stay at a steady `HIGH` (3.3V) state when idle. Floating lines are highly susceptible to ambient electromagnetic interference, which can cause false start bits and garbage characters. To enforce a robust signal state and filter out cross-talk noise, the internal weak **Pull-Up resistors** were explicitly enabled on `PA9` and `PA10` via the `PUPDR` register.
Buffer Overrun Protection & Multi-Byte Reception
The character reception module handles data safely by filtering out the carriage return (`\r`) character and interpreting only the line feed (`\n`) as the true end-of-packet delimiter. This prevents the driver from getting stuck on unexpected double newline sequences commonly transmitted by various third-party mobile Bluetooth terminals.

### About UART Communication:
In UART communication there are 2 main pins thats called RX and TX. TX is kinda transmitter (sender) pin. RX is kinda receiver pin.
In this communication pins generally stays at 3v voltage.
UART does not contain bus architecture.So many more devices are unconnectable in this communication protocol.



