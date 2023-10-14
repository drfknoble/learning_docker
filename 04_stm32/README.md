# 04_stm32

## Introduction

In this tutorial, I will show you how to use a Docker Dev Container to develop a program for an STM32.

See here for documentation on how to use PlatformIO in a Docker container and via the command line: https://docs.platformio.org/en/stable/core/index.html. 

## Installation

Here, I have installed the PlatformIO Command Line (CLI). I used the recommended installation script, which created a virtual environment in `/home/vscode/.platformio/penv``.

To activate the virtual environment, type the following into a terminal:

```console
source /home/vscode/.platformio/penv/bin/activate
```

To deactivate the virtual environment, type the following into a terminal:

```console
deactivate
```

Once the virtual environment is activated, the PlatformIO CLI commands can be used.

## Get boards

Type the following into a terminal to get a list of available boards:

```console
pio boards stm32
```

Afterwards, a list of available boards will be displayed.

## Initialise project

Type the following into a terminal to create a new project in the current directory:

```console
pio project init --board stm32f446re
```

Afterwards, a new PlatformIO project will be created. Required build tools will be automatically downloaded.

## Install platforms

Type the following into the terminal to install the appropriate platforms for the board:

```console
pio pkg install --platform ststm32
```

Afterwards, the platforms for the STM32 will be installed. Required build tools will be automatically downloaded.

## Add a source file

Add a file `main.cpp` to the `src/` subdirectory. 

Type the following into `main.cpp`:

```c++
#include <Arduino>

void setup()
{
    Serial.begin(115200);
    delay(100);

    Serial.println("Hello World!");
}

void loop()
{

}
```

## Build project

Type the following into a terminal to build the project:

```console
pio run
```

Afterwards, something similar to the following will be displayed:

```console
...
Building in release mode
Checking size .pio/build/nucleo_f446re/firmware.elf
Advanced Memory Usage is available via "PlatformIO Home > Project Inspect"
RAM:   [          ]   0.9% (used 1124 bytes from 131072 bytes)
Flash: [          ]   1.8% (used 9656 bytes from 524288 bytes)
========================== [SUCCESS] Took 122.88 seconds ==========================
```

## Discussion

While it's relatively easy to build the application in the dev container from the command line, a slightly easier way is to use the PlatformIO extension for VS Code. It will open the project in a new window, but it will be running inside a the container. Either way works. 

## Credit

Dr Frazer K. Noble
@drfknoble
