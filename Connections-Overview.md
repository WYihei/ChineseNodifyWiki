Connections are created between two points. The `Source` and `Target` dependency properties are of type `Point` and are usually bound to a connector's `Anchor` point.

## Base connection

The base class for all connections provided by the library is `BaseConnection` which derives from `Shape`. There's no restriction to derive from `BaseConnection` when you create a custom connection. 

It exposes two commands with their corresponding events:
 - `DisconnectCommand`, respectively `DisconnectEvent` - fired when the connection is clicked while holding `ALT`
 - `SplitCommand`, respectively `SplitEvent` - fired when the connection is double-clicked

The `Direction` of a connection can have two values:
 - `Forward`

![image](https://user-images.githubusercontent.com/12727904/192101918-af9b0da6-ecc8-48f7-bf4d-8f9fdd005153.png)
![image](https://user-images.githubusercontent.com/12727904/192101959-2cb9a837-1642-4e96-b2ef-eea5502a587f.png)


- `Backward`

![image](https://user-images.githubusercontent.com/12727904/192101941-a00e23db-07ae-49ac-a907-72e35ef67877.png)
![image](https://user-images.githubusercontent.com/12727904/192101977-1afd69f1-dab0-478e-9c3d-7d601486c289.png)

The `SourceOffset` and the `TargetOffset` works together with `OffsetMode` and will keep the distance from the anchor point:

![image](https://user-images.githubusercontent.com/12727904/192102096-b20887d5-b7ba-450f-9cf3-7fa4086d9637.png)

Connections also have a `Spacing` which will make the connection break the angle at a certain distance from the `Source` and `Target` points:

- With spacing:

![image](https://user-images.githubusercontent.com/12727904/192102286-9a79da8e-5e87-4f60-9e82-979bfabcd6f3.png)

- Without spacing:

![image](https://user-images.githubusercontent.com/12727904/192102302-4125b44a-dfad-4d9e-9131-efb7c17cefbe.png)

Settings the `ArrowSize` to "0, 0" will remove the arrow head.

## Line connection

## Circuit connection

## Connection



## Pending Connection

Canceling a pending connection is done by releasing the right mouse button.