# Overview

Nodes are the building blocks of a node editor, hence the following nodes are part of the library:

### 1. The ```Node``` control
This type of node supports both ```Input``` and ```Output``` connectors and can be moved around.

<details>
<summary>Example XAML</summary>

```xml
<nodify:NodifyEditor>
    <nodify:NodifyEditor.Resources>
	<local:FlowNodeViewModel x:Key="NodeContext"
		                 Title="My Node">
	    <local:FlowNodeViewModel.Input>
	        <local:ConnectorViewModel Title="In 0" />
	   	<local:ConnectorViewModel Title="In 1" />
	    </local:FlowNodeViewModel.Input>
	    <local:FlowNodeViewModel.Output>
		    <local:ConnectorViewModel Title="Out 0" />
	    	    <local:ConnectorViewModel Title="Out 1" />
	    </local:FlowNodeViewModel.Output>
	</local:FlowNodeViewModel>
    </nodify:NodifyEditor.Resources>

    <nodify:Node DataContext="{StaticResource NodeContext}"
		 Header="{Binding Title}"
		 Input="{Binding Input}"
		 Output="{Binding Output}">
	<nodify:Node.InputConnectorTemplate>
	    <DataTemplate>
	 	<nodify:NodeInput Header="{Binding Title}" />
	    </DataTemplate>
	</nodify:Node.InputConnectorTemplate>
	<nodify:Node.OutputConnectorTemplate>
	    <DataTemplate>
	        <nodify:NodeOutput Header="{Binding Title}" />
	    </DataTemplate>
	</nodify:Node.OutputConnectorTemplate>
    </nodify:Node>
</nodify:NodifyEditor>
```

</details>

![FlowNode](https://i.imgur.com/VwAYlX3.gif)

### 2. The ```GroupingNode``` control

This type of node can be resized and will will move nodes that are inside it if dragged by the ```Header```.

If the ```SwitchMovementModeModifierKey``` (**Shift** key by default) is held, it will move without moving its children.

<details>
<summary>Example XAML</summary>

```xml
<nodify:NodifyEditor>
    <nodify:GroupingNode Header="Grouping node"
			 Width="300"
			 Height="250" />
    <nodify:Node Header="My node" />
    <nodify:Node Header="My other node" />
</nodify:NodifyEditor>
```

</details>

![Grouping Node](https://i.imgur.com/HYxt2cs.gif)

### 3. The ```KnotNode``` control

This type of control can be used to reroute ```Connection```s as it supports only one ```Connector```.

<details>

<summary>Example XAML</summary>

```xml
<nodify:NodifyEditor>
	<nodify:KnotNode />
</nodify:NodifyEditor>
```

</details>

![Knot Node](https://i.imgur.com/fMrEqY1.gif)

### 4. The ```StateNode``` control

This type of node is a ```Connector``` itself, meaning that it will raise ```PendingConnection``` events on interaction.

<details>

<summary>Example XAML</summary>

```xml
<nodify:NodifyEditor>
    <nodify:StateNode Content="My node" />
</nodify:NodifyEditor>
```

</details>

![State Node](https://i.imgur.com/FrI2epL.gif)