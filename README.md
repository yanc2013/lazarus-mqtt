# Bond Keevil's MQTT Component Pack for Lazarus

Message Queue Telemetry Transport (MQTT) client and server component pack for Lazarus/FPC with demo applications.

## Project Goals: 

1. Implements the [MQTT protocol specification 3.1.1](http://docs.oasis-open.org/mqtt/mqtt/v3.1.1/mqtt-v3.1.1.html) completely and accurately
2. Implements all QoS levels
3. Is not dependent on a specific networking component or transport mechanism 
4. Has reasonable [documentation](https://github.com/bkeevil/mqtt/blob/master/doc/Main.MD)

For the client and server demo applications I have been using the LNet components because they seem to run well on both Windows and Linux.

There is a GUI client application and server application as well as a server command line application. These demonstrate the features of the component set and are useful for testing MQTT based applications.

MQTT Brokers are not implemented and there is no security authentication provided by this component. You must provide your own authentication methods by implementing appropriate event handlers

## Status Update November 2019

This project can be considered stable. I don't intend to do any more development work on this component set as I'm focused on developing version 2 in C++. Version 2 will support MQTT 3.1, 3.11 and 5.0 protocol versions for both client and server. It should be released by the end of the year.

## Installation

To build this package you will need to check out and install my "bkutils" package on which this package depends. This is my general utilities package. This package provides my TBuffer class which this component set uses extensively. 

Older versions of my bkUtils package also depend on my CryptoPKG package. The new version, which will be released shortly will depend on the DCPCrypt library. My CryptoPKG was a modified version of DCPCrypt but those modifications will be incorporated into my bkUtils package instead.

To build the demo applications you will also need to install LNet. For me, **the only version of LNet that works is the one available in the Lazarus online package manager, I am not sure why.**

## Documentation

The documentation is written in markdown and is [available in the docs directory](docs/Main.MD).

## License

This component is released under the GNU LGPL license agreement. You may share it, extend it, or use it for any commercial purposes provided you share any improvements you make to the code. It is not necessary to distribute this source code with your binaries.


## Build
1. Compile&Install bkutils 0.1 (third-party\bkutils\bkutils.lpk)
   - dcpcrypt 2.0.4.2          (third-party\DCPcrypt\dcpcrypt.lpk)
   - laz_synapse 40.1          (third-party\synapse40.1\laz_synapse.lpk)
2. Compile Inetvisual V0.6.5   (third-party\lnet-0.6.5\lazaruspackage\lnetvisual.lpk)
3. Compile&Install mqttcomponents V0.9.4.101 (src\mqttcomponents.lpk)
4. Clean up and Build Apps\MQTTServer\MQTTServerApp.lpr
5. Clean up and Build Apps\MQTTClient\MQTTClientApp.lpr
6. Clean up and Build Apps\MQTTServerCLI\MQTTServerCLI.lpr


## Run (Error List)
1. message: Unable to initialize OpenSSL library, please Check your OpenSSL installation.
   - On windows you should install OpenSSL librarys
   - http://www.openssl.org/related/binaries.html
   - If installer doesn't copy libeay32.dll and ssleay32.dll to Windows\System32 folder then you should do this manually


## Other Resouces
- lnet  https://github.com/almindor/lnet
- delphi-mqtt(ICS)  https://github.com/pjde/delphi-mqtt
