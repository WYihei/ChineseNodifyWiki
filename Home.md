# Welcome to Nodify!

Nodify is a WPF control library that offers the base controls needed for a node based editor.

### Requirements
![IDE](https://img.shields.io/static/v1?label=%20&message=VS%202019&color=informational&style=for-the-badge&logo=visual-studio)
![.NET](https://img.shields.io/static/v1?label=%20&message=Core%203.1&color=5C2D91&style=for-the-badge&logo=.net)
![C#](https://img.shields.io/static/v1?label=%20&message=8.0&color=239120&style=for-the-badge&logo=c-sharp)

### Install Nodify from Nuget
[![Download Package](https://img.shields.io/nuget/v/Nodify?label=Download&logo=nuget&style=for-the-badge)](https://www.nuget.org/packages/Nodify/)

```xml
Install-Package Nodify
```

### Quick start
Declare the namespace: ```xmlns:nodify="http://miroiu.github.io/winfx/xaml/nodify"```

Use the following XAML:
```xml
<nodify:NodifyEditor>
    <nodify:Node Header="My node"
                 nodify:ItemContainer.LocationOverride="100 100" />
    <nodify:Node Header="My other node"
                 nodify:ItemContainer.LocationOverride="200 100" />
    <nodify:GroupingNode Header="Grouping node"
                         Width="300"
                         Height="150"
                         nodify:ItemContainer.LocationOverride="50 50" />
    <nodify:KnotNode nodify:ItemContainer.LocationOverride="400 100" />
</nodify:NodifyEditor>
```
If you see this, then we're good to go:

![Result](https://i.imgur.com/SAbOxhY.png)

# Documentation

### Table of contents
- [Editor overview](Editor-Overview)
- [ItemContainer overview](ItemContainer-Overview)
- [Nodes overview](Nodes-Overview)
- [Connections overview](Connections-Overview)
- [Connectors overview](Connectors-Overview)

### Application examples
- [Playground](https://github.com/miroiu/nodify/tree/master/Examples/Nodify.Playground)
- [State machine](https://github.com/miroiu/nodify/tree/master/Examples/Nodify.StateMachine)
