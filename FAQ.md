
#### Q: Why is the connection not following the connectors when I move a node?

A1: You didn't bind the `Anchor` of the connector, or the `Source` and `Target` properties of the connection.

A2: The `Anchor` of the connectors updates only if the `IsConnected` property is set to true.

***

#### Q: Can I change the mouse/key bindings?

A: Yes! You can configure the [editor gestures](https://github.com/miroiu/nodify/blob/master/Nodify/EditorGestures.cs) to your liking.

***

#### Q: Would there be an Avalonia port?

A: No.

***

#### Q: Is there a non-MVVM approach to adding nodes and connections?

A: No.

***

#### Q: How can I set the selected nodes to be always on top?

A: https://github.com/miroiu/nodify/issues/57

***

#### Q: How can I change the size of a node?

A: https://github.com/miroiu/nodify/issues/55