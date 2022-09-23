
![editor-interaction](https://user-images.githubusercontent.com/12727904/192004838-ec6dd997-5e64-4c01-940c-1cd1b8d27837.gif)


# Welcome to Nodify!

Nodify is a WPF node-based [editor control](Editor-Overview) featuring a collection of useful components like [nodes](Nodes-Overview), [connections](Connections-Overview), and [connectors](Connectors-Overview) aiming to simplify the process of building node based tools.

### Requirements
![IDE](https://img.shields.io/static/v1?label=%20&message=VS%202019&color=informational&style=for-the-badge&logo=visual-studio)
![.NET](https://img.shields.io/static/v1?label=%20&message=Core%203.1&color=5C2D91&style=for-the-badge&logo=.net)
![C#](https://img.shields.io/static/v1?label=%20&message=8.0&color=239120&style=for-the-badge&logo=c-sharp)

### Install Nodify from Nuget
[![Download Package](https://img.shields.io/nuget/v/Nodify?label=Download&logo=nuget&style=for-the-badge)](https://www.nuget.org/packages/Nodify/)

```xml
Install-Package Nodify
```

### Table of contents
- [Editor overview](Editor-Overview)
- [ItemContainer overview](ItemContainer-Overview)
- [Nodes overview](Nodes-Overview)
- [Connections overview](Connections-Overview)
- [Connectors overview](Connectors-Overview)

### Application examples
- [Playground](https://github.com/miroiu/nodify/tree/master/Examples/Nodify.Playground)
- [State machine](https://github.com/miroiu/nodify/tree/master/Examples/Nodify.StateMachine)
- [Calculator](https://github.com/miroiu/nodify/tree/master/Examples/Nodify.Calculator)

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

Merge one of the following dictionaries in your application's resources to change the theme:

```Dark``` theme (default if not specified):
```xml
<ResourceDictionary Source="pack://application:,,,/Nodify;component/Themes/Dark.xaml" />
```
```Light``` theme:
```xml
<ResourceDictionary Source="pack://application:,,,/Nodify;component/Themes/Light.xaml" />
```

If you see this, then we're good to go:

![Result](https://i.imgur.com/SAbOxhY.png)

## Common XAML structure for MVVM:
```xml
<nodify:NodifyEditor ItemsSource="{Binding Nodes}"
                     Connections="{Binding Connections}"
                     ConnectionCompletedCommand="{Binding ConnectionCompletedCommand}">
    <nodify:NodifyEditor.ItemTemplate>
        <DataTemplate>
            <nodify:Node Header="{Binding Title}"
                         Input="{Binding Input}"
                         Output="{Binding Output}">
                <nodify:Node.InputConnectorTemplate>
                    <DataTemplate>
                        <nodify:NodeInput Header="{Binding Title}"
                                          Anchor="{Binding Anchor, Mode=OneWayToSource}"
                                          IsConnected="{Binding IsConnected}" />
                    </DataTemplate>
                </nodify:Node.InputConnectorTemplate>
                <nodify:Node.OutputConnectorTemplate>
                    <DataTemplate>
                        <nodify:NodeOutput Header="{Binding Title}"
                                           Anchor="{Binding Anchor, Mode=OneWayToSource}"
                                           IsConnected="{Binding IsConnected}" />
                    </DataTemplate>
                </nodify:Node.OutputConnectorTemplate>
            </nodify:Node>
        </DataTemplate>
    </nodify:NodifyEditor.ItemTemplate>
    <nodify:NodifyEditor.ConnectionTemplate>
        <DataTemplate>
            <nodify:Connection Source="{Binding Input.Anchor}"
                               Target="{Binding Output.Anchor}" />
        </DataTemplate>
    </nodify:NodifyEditor.ConnectionTemplate>
    <nodify:NodifyEditor.ItemContainerStyle>
        <Style TargetType="{x:Type nodify:ItemContainer}">
            <Setter Property="Location"
                    Value="{Binding Location}" />
        </Style>
    </nodify:NodifyEditor.ItemContainerStyle>
</nodify:NodifyEditor>
```
