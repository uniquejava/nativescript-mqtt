# NativeScript MQTT 3.1.1 Module

This nativescript-mqtt module is a cross-platofrm javascript implementation leveraging native socket support and the open source [MQTT 3.1.1 PAHO library link](http://www.eclipse.org/paho). Currently the library only supports the websocket protocol for cross-platform on port 80 or 443 for SSL.

## Usage Sample
### Connection Options
```text
host: string
port: int - default 80 | useSSL 443
path: string - default empty
useSSL: bool - default false
clientId: string - default UUID
retryOnDisconnect: bool - default false
```
### Connection Events
```text
ConnectionSuccess(): void
ConnectionFailure(): string
ConnectionLost(): string
MessageArrived(): Message
```
### Message Object
```javascript
Message {
  payload: string
  bytes: ArrayBuffer
  topic: string
  qos: number
}
```
### Sample Code

### Callouts
