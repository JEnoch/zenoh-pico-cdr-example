# CDR encoding/decoding for zenoh-pico

This example is showing how to leverage the CDR encoding/decoding library from CycloneDDS in a zenoh-pico application.
This allows a zenoh-pico application to publish or subscribe to a DDS application, using the [zenoh-bridge-dds](https://github.com/eclipse-zenoh/zenoh-plugin-dds) as an intermediate.

## Prerequisite:

 - CycloneDDS' `idlc` code generator must be installed and accessible in the `${PATH}`
 - CMake 2.14+

## How to build:

```bash
mkdir build
cd build
cmake ..
make
```

## Result of build:

 - **`z_sub_cdr`**: an example of zenoh-pico subscriber that decodes the received payloads from CDR as a `HelloWorldData_Msg` (see definition in `idl/HelloWorldData.idl` file).  
   Options:

     - `-k <keyexpr>`: the key expression to subscribe (equal to the DDS topic when routed by `zenoh-bridge-dds`). Default: `HelloWorldData_Msg`
     - `-e <endpoint>`: a Zenoh endpoint to establish the connection with (e.g.: `tcp/192.168.2.3:7447`). Default: zenoh-pico tries to discover a Zenoh router via UDP multicast.
     - `-m <client|peer>`: the mode in which zenoh-pico is running. Default: `client`

 - **`z_pub_cdr`**: an example of zenoh-pico publisher that encodes the payloads to CDR from a `HelloWorldData_Msg` (see definition in `idl/HelloWorldData.idl` file).  
   Options:

     - `-k <keyexpr>`: the key expression to subscribe (equal to the DDS topic when routed by `zenoh-bridge-dds`). Default: `HelloWorldData_Msg`
     - `-e <endpoint>`: a Zenoh endpoint to establish the connection with (e.g.: `tcp/192.168.2.3:7447`). Default: zenoh-pico tries to discover a Zenoh router via UDP multicast.
     - `-m <client|peer>`: the mode in which zenoh-pico is running. Default: `client`





