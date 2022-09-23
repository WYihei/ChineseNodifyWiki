# Components Overview

It is _important_ to know how components are named and what's their role in the visual tree of the editor in order to understand the code and the documentation.

## Hierarchy and terminology

The root component is an [editor](Editor-Overview) which holds [nodes](Nodes-Overview) and [connections](Connections-Overview) together with a few additional UI elements such as a [selection rectangle](Editor-Overview#selecting) and a [pending connection](Connections-Overview#pending-connection) in order to make the editor interactive.

Nodes are containers for [connectors](Connectors-Overview) or the node itself can be a connector (e.g. [State Node](Nodes-Overview#4-the-statenode-control)).

Connectors can create pending connections that can become real connections when completed.

_A picture is worth a thousand words_

![nodes-hierarchy](https://user-images.githubusercontent.com/12727904/192028123-e2847f29-6517-4731-8672-f5d8356dead0.png)


## Items and Connections Layers

You may wonder how a node can be a connector itself and and still behave like a normal node. The editor contains three big layers which help solve this problem:

1. The items layer (`NodifyEditor.ItemsSource`) - here, each control is wrapped inside an [Item Container](ItemContainer-Overview) making it selectable, draggable, etc and it is possible to have any control rendered (e.g a connector, a text block).
2. The connections layer (`NodifyEditor.Connections`) - this is where all the [connections](Connections-Overview) coexist and are rendered behind the items layer by default
3. The decorators layer (`NodifyEditor.Decorators`) - here, each control is given a location inside the graph

Having those layers separated enables the possibility of asynchronously loading each one of them.
