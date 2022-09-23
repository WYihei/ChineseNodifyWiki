It is _important_ to understand how components are named and what's their role in the visual tree of the editor in order to understand the code and the documentation.

## Hierarchy and terminology

The root component is an [editor](Editor-Overview) which holds [nodes](Nodes-Overview) and [connections](Connections-Overview) together with a few additional UI elements such as a [selection rectangle](Editor-Overview#selecting) and a [pending connection](Connections-Overview#pending-connection) in order to make the editor interactive.

Nodes are containers for [connectors](Connectors-Overview) or the node itself can be a connector (e.g. [State Node](Nodes-Overview#4-the-statenode-control)).

Connectors can create pending connections that can become real connections when completed.

_A picture is worth a thousand words_

![nodes-hierarchy](https://user-images.githubusercontent.com/12727904/192028123-e2847f29-6517-4731-8672-f5d8356dead0.png)

## Content Layers

You may wonder how a node can be a connector itself and still behave like a normal node. The editor contains three big layers which help solve this problem:

1. The items layer (`NodifyEditor.ItemsSource`) - here, each control is wrapped inside an [Item Container](ItemContainer-Overview) making it selectable, draggable, etc and it is possible to have any control rendered (e.g a connector, a text block).
2. The connections layer (`NodifyEditor.Connections`) - this is where all the [connections](Connections-Overview) coexist and are rendered behind the items layer by default
3. The decorators layer (`NodifyEditor.Decorators`) - here, each control is given a location inside the graph

Having those layers separated enables the possibility of asynchronously loading each one of them.

## Creating an editor

Import the `nodify` namespace: `xmlns:nodify="https://miroiu.github.io/nodify"` or `xmlns:nodify="clr-namespace:Nodify;assembly=Nodify"` in your file and create an instance of the editor `<nodify:NodifyEditor />`. If you start the application, you will see an empty space where you can create a selection rectangle.
> Tip: Drag the selection rectangle near the edge of the editor area and the screen will automatically move in that direction.

## Using an existing theme

Merge one of the following themes into your resource dictionary in `App.xaml`:

- Dark theme (default theme if not specified):
```xml
<ResourceDictionary Source="pack://application:,,,/Nodify;component/Themes/Dark.xaml" />
```

- Light theme:
```xml
<ResourceDictionary Source="pack://application:,,,/Nodify;component/Themes/Light.xaml" />
```

- Nodify theme:
```xml
<ResourceDictionary Source="pack://application:,,,/Nodify;component/Themes/Nodify.xaml" />
```

## Drawing a grid

Drawing a simple grid is just a matter of creating a grid brush, applying the editor transform to it, and using the brush as the `Background` of the editor.

Because the grid we are drawing is made of lines and is not filled, the `Background` of the editor will have some transparency, meaning that we'll see the background color of the control below. To solve this, wrap the editor in a `Grid` and set its `Background` or set the `Background` of the `Window`.

Use the `ViewportTransform` dependency property to have the grid move with the view.

> Note: The example uses static resources which are provided by the selected theme in `App.xaml`.

```xml
<Window x:Class="MyProject.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:nodify="https://miroiu.github.io/nodify"
        mc:Ignorable="d">

    <Window.Resources>
        <GeometryDrawing x:Key="SmallGridGeometry"
                        Geometry="M0,0 L0,1 0.03,1 0.03,0.03 1,0.03 1,0 Z"
                        Brush="{StaticResource NodifyEditor.SelectionRectangleBackgroundBrush}" />

        <GeometryDrawing x:Key="LargeGridGeometry"
                        Geometry="M0,0 L0,1 0.015,1 0.015,0.015 1,0.015 1,0 Z"
                        Brush="{StaticResource NodifyEditor.SelectionRectangleBackgroundBrush}" />

        <DrawingBrush x:Key="SmallGridLinesDrawingBrush"
                    TileMode="Tile"
                    ViewportUnits="Absolute"
                    Viewport="0 0 20 20"
                    Transform="{Binding ViewportTransform, ElementName=Editor}"
                    Drawing="{StaticResource SmallGridGeometry}" />

        <DrawingBrush x:Key="LargeGridLinesDrawingBrush"
                    TileMode="Tile"
                    ViewportUnits="Absolute"
                    Opacity="0.5"
                    Viewport="0 0 100 100"
                    Transform="{Binding ViewportTransform, ElementName=Editor}"
                    Drawing="{StaticResource LargeGridGeometry}" />
    </Window.Resources>

    <Grid Background="{StaticResource NodifyEditor.BackgroundBrush}">
        <nodify:NodifyEditor x:Name="Editor" Background="{StaticResource SmallGridLinesDrawingBrush}" />

        <Grid Background="{StaticResource LargeGridLinesDrawingBrush}"
              Panel.ZIndex="-2" />
    </Grid>
</Window>
```

> Tip: Right-click and drag the screen around to move the view and use the mouse wheel to zoom in and out.