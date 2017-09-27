---
title: Tektelic
menu:
    main:
        parent: gateway
---

## Tektelic

### Tektelic Pico gateway

Tektelic Pico gateway is supplied with firmware designed to work with specific
network server. The "Semtech packet forwarder" variant will work with LoRaServer.

In order to configure the server parameters, create a configuration file and
upload it to the gateway using TFTP.

1. Create a JSON file named `customer_conf.json` with the following contents,
   substituting appropriate address and port values:

   ```javascript
   {
       "network_server": "example.com",
       "network_service_up_port": 1780,
       "network_service_down_port": 1780
   }
   ```
2. Connect the Pico gateway to the network and find out the IP address assigned
   to it. This may be easier to accomplish if the gateway is connected directly
   to a PC running a private DHCP server.
3. Upload the `customer_conf.json` file to the gateway. Note that the file name
   must match in order for the changes to take effect.

     * If using Linux, use the following command to upload the file:

```sh
        tftp <gw_ip_address> -c put customer_conf.json
```

     * If using Windows, Tftpd32 can be used as both a DHCP server and a TFTP client.
       Tftpd32 can be obtained from http://tftpd32.jounin.net. In order to upload
       the file, set the gateway IP address and ensure the remote file name is
       `customer_conf.json`, as shown in the figure below.

       ![Gateway Pieces and Connections](/lora-gateway-bridge/img/TektelicPicoTftpSettings.png)

4. Power-cycle the gateway for the new settings to take effect.

