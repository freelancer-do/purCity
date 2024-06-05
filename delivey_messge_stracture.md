# The JSON Structure of Delivery Message

_version: 1_

```
{
    "gateway_id": 1,
    "message_id": 1717616744045,
    "status": "success"
}
```

The delivery message structure is a JSON format that is used to report the successful receipt of a message by either the ESP device or the server.

- **gateway_id**: This field identifies the specific gateway or device that is sending the delivery report.
- **message_id**: The `message_id` field contains the unique identifier of the message that was successfully received. This `message_id` must match the `message_id` of the original message.
- **status**: The `status` field is set to the value `"success"` to indicate that the message was received without any issues.

Both the ESP device and the server are required to send a delivery report message after receiving a message from the other party. This report confirms that the original message was successfully received and processed.

_In the future, additional status values may be introduced to provide more detailed information about the delivery status, but for now, the "success" status is the only one defined._

The provided example demonstrates the JSON structure of a delivery report message, with sample values for the fields.
