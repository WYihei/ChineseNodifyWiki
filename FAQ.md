
#### Q: Why is the connection not following the connectors when I move a node?

A1: You didn't bind the `Anchor` of the connector, or the `Source` and `Target` properties of the connection.

A2: The `Anchor` of the connectors updates only if the `IsConnected` property is set to true.

***

#### Q: Would there be an Avalonia port?

A: No.

***

#### Q: Is there a non-MVVM approach to adding nodes and connections?

A: No.

***

#### Q: Can I change the mouse/key bindings?

A: Yes! You can configure the [editor gestures](https://github.com/miroiu/nodify/blob/master/Nodify/EditorGestures.cs) to your liking.