---
description: Running the IoTeX SDK in Linux
---

# Linux

## Get the source code

```bash
git clone https://github.com/iotexproject/arduino-sdk
cd arduino-sdk
```

## Building the library

Requires cmake 3.1.0 or higher.

Refer to [https://cmake.org/install/](https://cmake.org/install/) for instrutions on how to install cmake.

```bash
mkdir build && cd build
cmake ..
make
```

If successful, build files are placed in the `build` directory.

## Building and running the tests

### Building the tests

```bash
mkdir build && cd build
cmake -DUNIT_TEST=ON ..
make
```

Unit tests build files are placed in `build/tests.`

### Running the tests

```bash
cd build
./tests/iotex_unit_tests
```

## Using the library in your application

Include the IoTeX-Client main header in your program as below:

`#include <IoTeXClient.h>`

Create the `Connection` object, passing the connection details:

```cpp
const char ip[] = "gateway.iotexlab.io";
const char baseUrl[] = "iotexapi.APIService";
const int port = 10000;
Connection<Api> connection(ip, port, baseUrl);
```

Now you are ready to call any of the API methods.

You can find examples of most of the library methods under the [examples](https://github.com/iotexproject/arduino-sdk/tree/main/examples) directory.

## Debug logs

Debug logs are disabled by default. They can be enabled at runtime or at compile time.

Follow the instructions below in order to enable them and set the log level.

The log level can be set per module, and also globally. A log statement is printed if it's level is higher than the log level configured for it's module, and higher than the global log level.

The library prints logs to stdout using `printf().`

### Setting debug log level at compile time

This can be done by setting the `LOG_LEVEL` cmake variable before building. Eg:

`cmake -DUNIT_TEST=ON -DLOG_LEVEL=DEBUG ..`

The possible values for `LOG_LEVEL` are:

* NONE (default)
* ERROR
* WARNING
* INFO
* DEBUG
* TRACE

### Setting debug log level at run time

The log level can also be set at runtime using the `IotexHelpers` global object.

#### Setting per module log level

You can set the log level for a specific module. The existent log modules are:

* "GENERAL"
* "HTTP"
* "CONTRACT"

Simply call the following method on the `IotexHelpers` global object:\
`void setModuleLogLevel(const std::string& module, IotexLogLevel level)`

Eg. This will set the HTTP log level to `DEBUG`:\
`IotexHelpers.setModuleLogLevel("HTTP", IotexLogLevel::DEBUG);`

#### Setting the log level globally

You can also set the log level globally for all modules.

Simply call the following method on the `IotexHelpers` global object:\
`void setGlobalLogLevel(IotexLogLevel level)`

Eg. This will set the log level globally to `DEBUG`:\
`IotexHelpers.setGlobalLogLevel(IotexLogLevel::DEBUG);`

