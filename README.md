# The Chocolate Croissant

Yeah the name is stupid, I know.

This is a breakout board for when you want to fit a Raspberry Pi [34] B hat
onto a Raspberry Pi Pico or fit a Raspberry Pi Pico in something that expects a
full Raspberry Pi [34] B+.

The Raspberry Pi Pico W fits too of course.

## Pinout

The pinout might not be what you expect since the idea is to map function to
function rather than GPIO pin to pin.

By this I mean that the Pico I2C0 pins are mapped to the I<sup>2</sup>C pins of the
Raspberry Pi B+, SPI0 on the Pico is mapped to the SPI of the Raspberry Pi B+
and so on.

| Pin | Func             | Func             | Pin |
| :-- | :--------------- | :--------------- | --: |
| 1   | +3.3V            | +5V              | 2   |
| 3   | SDA0/GPIO4       | +5V              | 4   |
| 5   | SCL0/GPIO5       | GND              | 6   |
| 7   | GPIO6            | TX/GPIO0         | 8   |
| 9   | GND              | RX/GPIO1         | 10  |
| 11  | GPIO11           | SPI1_CS/GPIO13   | 12  |
| 13  | *TODO*           | GND              | 14  |
| 15  | GPIO20           | GPIO21           | 16  |
| 17  | +3.3V            | GPIO22           | 18  |
| 19  | SPI0_MOSI/GPIO19 | GND              | 20  |
| 21  | SPI0_MISO/GPIO16 | GPIO23           | 22  |
| 23  | SPI0_SCK/GPIO18  | SPI0_CS/GPIO17   | 24  |
| 25  | GND              | GPIO9            | 26  |
| 27  | SDA1/GPIO26      | SCL1/GPIO27      | 28  |
| 29  | GPIO7            | GND              | 30  |
| 31  | GPIO8            | PWM1A/GPIO2      | 32  |
| 33  | PWM1B/GPIO3      | GND              | 34  |
| 35  | SPI1_MISO/GPIO12 | GPIO10           | 36  |
| 37  | *TODO*           | SPI1_MOSI/GPIO12 | 38  |
| 39  | GND              | SPI1_SCK/GPIO14  | 40  |

There are two pins that are not currently connected to anything, these are
Raspberry Pi B+ pins `GPIO26` and `GPIO27`. They should obviously be connected,
the question is to what they should be connected. Maybe I need to rethink the
mapping of other stuff since I don't really have any more pins to connect from
the Pico.

### Special Breakouts

There are a couple of special breakouts avaiable:

- I<sup>2</sup>C - Four pin connector for general I<sup>2</sup>C devices
- SPI - Two SPI pin connectors:
  - Six pin SPI to fit SPI devices with six pins
  - Eight pin SPI to fit SPI devices with eight pins
- Qwiic/STEMMA QT - Two placements for Qwiic/STEMMA QT connectors:
  - I<sup>2</sup>C connected to I2C0 on the Pico
  - I<sup>2</sup>C connected to the debug pins

## Images

![Chocolate Croissant Perspective View](images/chocolate_croissant_perspective.png)

![Chocolate Croissant Front View](images/chocolate_croissant.png)

![Chocolate Croissant Back View](images/chocolate_croissant_back.png)

## TODO

- [ ] Connect Raspberry Pi B+ pins `GPIO26` and `GPIO27` (**NOTE:** To what??)
- [ ] Add a reset button somewhere and set it up to Pico pin `RUN` maybe(?)
- [x] Add some more "special" breakouts to enable attaching debug headers,
  displays, I<sup>2</sup>C/SPI stuff...
- [x] Describe any and all "special" breakouts, like the I<sup>2</sup>C mounting
  holes

## Future/Other Work

The `over_the_top` folder holds stuff related to the "over the top" version
which is basically a full blown RP2040 on a Raspberry Pi B+ board, it's based on
the KB2040 and the Raspberry Pi Pico datasheet and has a ton of tiny SMD
components that needs to be soldered to the board.

The idea is to use JLCPCB soldering services to have them all connected but that
requires some more research into which components they offer and such.

It's far from done and isn't really useful yet. Might finish it, might not. The
biggest hurdle is to get a wireless chip and antenna onto it, but I don't know
which chip that would be just yet. Could probably use the same as the Pico W,
but I think I would need to use a different antenna.

Anyway, there are some question marks regarding licenses for the chip and
antenna used on the Pico W that seems to indicate they are not quite free to use?
