---
layout: post
title: "Wi-Fi development board and Marauder"
excerpt: The Marauder firmware is a popular firmware for Wi-Fi-enabled microcontrollers. It provides a robust set of features for Wi-Fi connectivity, including network scanning, connection management, and data transmission.
date: 2023-02-11
categories: IoT Wireless_Communication Security_Research
---


## Introduction

The Marauder firmware is a popular firmware for Wi-Fi-enabled microcontrollers. It provides a robust set of features for Wi-Fi connectivity, including network scanning, connection management, and data transmission.

## Requirements

Before you begin, make sure you have the following items:

* A Flipper Wi-Fi Dev Board
* A USB cable
* A computer with a terminal emulator installed
* The Marauder firmware

## Step 1: Connect the Flipper Wi-Fi Dev Board to Your Computer

Connect the Flipper Wi-Fi Dev Board to your computer using a USB cable. The board should appear as a serial port in your computer's device manager.

## Step 2: Install Dependencies

To flash the Marauder firmware, you need to install several dependencies. These dependencies include:

* Python 3
* esptool.py
* pyserial

You can install these dependencies using pip, the Python package manager, by running the following commands in a terminal:
pip install esptool pyserial


## Step 3: Erase the Flash Memory

Before flashing the Marauder firmware, you need to erase the flash memory of the Flipper Wi-Fi Dev Board. To do this, run the following command in your terminal:
esptool.py --port /dev/ttyUSB0 erase_flash


Replace /dev/ttyUSB0 with the serial port of the Flipper Wi-Fi Dev Board on your computer.

## Step 4: Flash the Marauder Firmware

To flash the Marauder firmware, run the following command in your terminal:
esptool.py --port /dev/ttyUSB0 write_flash 0x0 marauder.bin


Replace /dev/ttyUSB0 with the serial port of the Flipper Wi-Fi Dev Board on your computer, and marauder.bin with the path to the Marauder firmware file on your computer.

## Step 5: Verify the Firmware

Once the Marauder firmware is flashed, you can verify that it was successful by checking the serial output from the Flipper Wi-Fi Dev Board. Open a terminal emulator and connect to the serial port of the Flipper Wi-Fi Dev Board using the following settings:

* Baud rate: 115200
* Data bits: 8
* Stop bits: 1
* Parity: None

Once connected, you should see the Marauder firmware output in the terminal emulator.

## Conclusion

In this tutorial, we walked you through the steps to flash the Marauder firmware on the Flipper Wi-Fi Dev Board. By following these steps, you should be able to successfully flash the Marauder firmware and begin using its robust set of features for Wi-Fi connectivity.