nRF52832 HCI/UART DFU Bootloader - From nRF5 SDK v11.0.0
======================================================

Device firmware update (DFU) bootloader which allows the nRF52832's firmware and/or SoftDevice to be updated serially.

[nrfutil v0.5.2](https://github.com/NordicSemiconductor/pc-nrfutil/releases/tag/v0.5.2) can be used to transfer a firmware image from computer to nRF52832.

To enter the bootloader, pin 6 -- attached to a button on the SparkFun nRF52832 Breakout -- must be held low on startup or reset. The LED on pin 7 will blink in a "timebomb" pattern to indicate the board is in the bootloader state.

For more information on the Nordic BLE & HCI/UART Bootloader/DFU, check out their [SDK Reference Page](http://infocenter.nordicsemi.com/topic/com.nordic.infocenter.sdk5.v11.0.0/examples_ble_dfu.html).

### Contents

* **/config** -- Platform-specific configurations.
* **/hex** -- Compiled hex files for the SoftDevice (S132) and bootloader.
* **main.c** -- Main source file for bootloader application

### Toolchain Requirements

### Using the Bootloader
