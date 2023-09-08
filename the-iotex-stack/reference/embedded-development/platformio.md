# PlatformIO

The library has been published in [PlatformIO library registry](https://platformio.org/lib/show/13239/IoTeX-blockchain-client)

In order to use it with your program, simply add `IoTeX-blockchain-client` to the `lib_deps` of your `platformio.ini` and include the main header file `#include "IoTeX-blockchain-client.h"` in your sketch

You can check the [examples](https://github.com/iotexproject/arduino-sdk/tree/main/examples) for more information

**Note:**  Due to a bug in PlatformIO, dependencies in`library.json`are not detected unless they are also provided in `platformio.ini`. For Nano33 or other SAMD boards, the `WiFiNINA`and  `FlashStorage`libraries also need to be added to your `lib_deps`

