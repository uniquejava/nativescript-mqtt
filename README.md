# NativeScript MQTT 3.1.1 Module

This nativescript-mqtt module is a cross-platofrm javascript implementation leveraging native socket support and the open source [MQTT 3.1.1 PAHO library link](http://www.eclipse.org/paho). Currently the library only supports the websocket protocol for cross-platform on port 80 or 443 for SSL.

## Usage Sample
### Create an MQTT Client
```
import {MQTTClient, ClientOptions} from "nativescript-mqtt";
...
mqtt_host : string = "broker.mqttdashboard.com";
mqtt_port : number = 8000;
mqtt_useSSL : boolean = false;

mqtt_clientOptions: ClientOptions = {
    host: this.mqtt_host,
    port: this.mqtt_port,
    useSSL: this.mqtt_useSSL
};

mqtt_client : MQTTClient = new MQTTClient(this.mqtt_clientOptions);
```
### Setup Handlers
```
...
mqtt_topic : string = "sample-topic"

constructor() {
    this.setupHandlers();
}

setupHandlers() : void {
    this.mqtt_client.onConnectionFailure.on((err : any) => {
        console.log("Connection failed: " + JSON.stringify(err));
    });
    this.mqtt_client.onConnectionSuccess.on(() => {
        console.log("Connected successfully!");
        this.subscribe();
    });
    this.mqtt_client.onConnectionLost.on((err : any) => {
        console.log("Connection lost: " + JSON.stringify(err));
    });
    this.mqtt_client.onMessageArrived.on((message: Message) => {
        console.log("Message received: " + message.payload);
    });
}

subscribe() : void {
    this.mqtt_client.subscribe(this.mqtt_topic);
}
```

### Connect
```
mqtt_username : string = "";
mqtt_password : string = "";

connect() : void {
    this.mqtt_client.connect(this.mqtt_username, this.mqtt_password);
}
```
And in the template:
```
<Button text="Connect" (tap)="connect()"></Button>
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
