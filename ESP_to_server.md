
# The JSON  structure of the message sent from ESP to the server
_version: 1_

```
{
    "gateway_id": 1,
    "message_id": 1717616744045,
    "device_pack_info": [
        {
            "device_pack_id": 1,
            "sensor_1": 22.2,
            "sensor_2": true,
            "sensor_3": false,
            "sensor_4": 18,
            "Timestamp": 1717491848
        },
        {
            "device_pack_id": 2,
            "sensor_1": 22.8,
            "sensor_2": true,
            "sensor_3": false,
            "sensor_4": 19,
            "Timestamp": 1717491848
        }
    ]
}
```




### gateway_id
- This is a unique integer ID that identifies the gateway device.
- 
- Each project should have a unique gateway ID, which is used to create the MQTT topic for sending data to the server. For example, if the gateway_id is 1, the MQTT topic would be PurCity/ESP_to_server/1.

### message_id

- The `message_id` is a unique identifier assigned to each message sent to the server. This unique ID helps the server track and manage the messages it receives.
- After receiving a message, the server responds with a message containing the word `"success"` and an ID similar to the original `message_id`. This indicates that the original message was successfully received by the server.
- The `message_id` can be a nanosecond-precision Unix timestamp, which provides a highly unique and time-based identifier for each message.
- It is explained in more detail in the `delivey_messge_stracture` file.

### device_pack_info
- This is an array that contains information about the various device packs connected to the gateway.
- Each element in the array represents a unique device_pack_id, which is an integer that identifies the device pack.
- Under each device_pack_id, there is information about the sensors and their corresponding values, as well as a timestamp indicating when the data was collected.

### Sensor Data
- The sensor data is stored as key-value pairs, where the key represents the sensor ID (e.g., sensor_1, sensor_2, etc.) and the value represents the sensor reading.
- The sensor IDs should be pre-defined and agreed upon, so that the server knows which sensor corresponds to each ID. For example, sensor_1 could be the humidity sensor, - sensor_2 could be the temperature sensor, and so on.
- The sensor values can be of any appropriate data type (e.g., string, number, boolean) depending on the sensor type and the data format.

### Timestamp
- The timestamp field represents the time at which the sensor data was collected, in Unix timestamp format (seconds since the Unix epoch).
- This timestamp can be used by the server to organize and analyze the data correctly.


  Here is a plain English explanation of the JSON structure with some improvements:

The JSON structure represents the data sent from an ESP (Embedded System Platform) device to a server. The structure has the following key components:

1. `gateway_id`:
   - This is a unique integer ID that identifies the gateway device.
   - Each project should have a unique gateway ID, which is used to create the MQTT topic for sending data to the server. For example, if the `gateway_id` is 1, the MQTT topic would be `PurCity/ESP_to_server/1`.

2. `device_pack_info`:
   - This is an array that contains information about the various device packs connected to the gateway.
   - Each element in the array represents a unique `device_pack_id`, which is an integer that identifies the device pack.
   - Under each `device_pack_id`, there is information about the sensors and their corresponding values, as well as a timestamp indicating when the data was collected.

3. Sensor Data:
   - The sensor data is stored as key-value pairs, where the key represents the sensor ID (e.g., `sensor_1`, `sensor_2`, etc.) and the value represents the sensor reading.
   - The sensor IDs should be pre-defined and agreed upon, so that the server knows which sensor corresponds to each ID. For example, `sensor_1` could be the humidity sensor, `sensor_2` could be the temperature sensor, and so on.
   - The sensor values can be of any appropriate data type (e.g., string, number, boolean) depending on the sensor type and the data format.

4. Timestamp:
   - The `Timestamp` field represents the time at which the sensor data was collected, in Unix timestamp format (seconds since the Unix epoch).
   - This timestamp can be used by the server to organize and analyze the data correctly.

Overall, this JSON structure provides a standardized way to transmit sensor data from an ESP device to a server, with the ability to identify the gateway, the device packs, and the individual sensor readings, along with the timestamp when the data was collected.
Currently, according to the above theory, we intend to send information to the server in time intervals


