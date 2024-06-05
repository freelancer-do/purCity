# The JSON structure of the message sent from the server to the ESP
_version: 1_

```
{
    "gateway_id": 1,
    "message_id":1717616744045,
    "command": "set_output",
    "device_pack_outputs": [
        {
            "device_pack_id": 1,
            "output_1": true,
            "output_2": 50,
            "output_3": false
        },
        {
            "device_pack_id": 2,
            "output_1": false,
            "output_2": 75,
            "output_3": true 
        }
    ]
}
```

### gateway_id
- This is the unique integer ID that identifies the gateway device, which should match the `gateway_id` sent from the ESP to the server.
- The MQTT topic is constructed using the `gateway_id`, in the format `PurCity/server_to_esp/1`.
- The ESP should subscribe to this MQTT topic to listen for any commands or updates from the server.

### message_id
- Each message sent between the server and the ESP device includes a unique `message_id`.
- When the server sends a message to the ESP device, it expects the ESP device to return an "ACT" message, along with the original `message_id`. 
- This response from the ESP device indicates that the server's message was correctly received and processed by the ESP device.
- It is explained in more detail in the `delivey_messge_stracture` file.

### command
- In this case, the command is `"set_output"`, which means the server is sending new output values for the device packs.
- This is the initial version of the command. It may be necessary to adjust some additional parameters or introduce new commands in the future, based on the requirements.
- The ESP developer should provide more explanation regarding the adjustable parameters, so that a suitable JSON solution can be found.
- For example, there could be a `"get_output"` command to retrieve the status of the outputs, or a `"set_config"` command to set the interval for sending data to the server.
- These additional commands are just examples, and the document can be updated in the future if new requirements arise.

### device_pack_outputs
- This is an array that contains the output values for each device pack.
- Each element in the array corresponds to a `device_pack_id`, which should match the `device_pack_id` values sent from the ESP to the server.
- Under each `device_pack_id`, there are key-value pairs representing the output values. The keys (e.g., `output_1`, `output_2`, `output_3`) should be pre-defined and agreed upon by the server and ESP developers.
- The output values can be of any appropriate data type (e.g., boolean, integer) depending on the type of output.

The ESP should receive this message from the server, parse the JSON, and set the corresponding output values for each device pack. The ESP should then apply these new output values to the physical outputs or actuators connected to the device packs.
