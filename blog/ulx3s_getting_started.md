---
layout: default
---
# ULX3S Development board: getting started

Now that winter is coming back again, I am trying to order the projects I would like to develop in the following months. Is always hard to find time to tinker and write this blog entries, but, at the same time, it is really satisfying.

I would like to continue exploring new ideas using FPGAs and, at some point, I would like to design one using KiCAD. I also feel tempted to get a development board such as the Ultra96v2 or the new Kria SoM to play with ROS2 and hardware acceleration, which I think is one of the coolest thing to do out there. But I will save some money for now.

It's been a while since I purchased a Radiona [ULX3S](https://radiona.org/ulx3s/) board and still haven't used it. So this blog entry shows the first steps I have made with this board.
There are several reasons why I purchased it:

- It contains an ECP5 Lattice FPGA, much more powerful that iCE40 family. (Check the comparison I [did](../fpga-boards))
- It contains an ESP32 with bluetooth connectivity. That means Ii is possible to build a mobile robot and control it through the laptop.
- I can synthesize RISC-V cores, so I can start exploring hybrid computing architectures.
- It has been designed in KiCAD.
- It's open source.
- It has many exposed GPIOs and interfaces
- And last but not least, the design is really neat and small.

## Updating the toolchain

As it has been a while since I lastly used FuseSoC, Yosys and Nextpnr, the first step has been to update all the tool-chain. In addition I had to install the Project Trellis NexPnr tooling, as is not the same as the iCE40.

For updating Yosys, I just have updated from `apt`: `$ sudo apt-get install yosys`


For downloading the bitstream flasher fujprog, you can go to its [GitHub page](https://github.com/kost/fujprog/releases) and download the precompiled binary and place it under `/usr/bin`

## Loading the precompiled Blinky

## FuseSoC Blinky to believe

First of all, update FuseSoC: `$ fusesoc library update`. Then compile the blinky example: `$ fusesoc run --target=ulx3s_85 fusesoc:utils:blinky`. Thne you can use `fujprog` to upload the bitstream, for doing so, go to be build folder and upload the bitstream: `$ build/fusesoc_utils_blinky_1.0/ulx3s_85-trellis` and `$ fujprog fusesoc_utils_blinky_1.0.bit`. Now you should see something like:

![](img/fujprog_blinky.png)

And a red light should be blinking!

## Next Steps

Now that I got my hands dirty again, one of the following steps I want to do is to understand the hardware design of the board, so I will print the schematics and review how everything is connected. Afterwards, I might refresh the use of FuseSoC and Verilog, making some simple examples using LEDs and buttons.
