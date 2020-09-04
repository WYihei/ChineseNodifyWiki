# Overview

Nodes are the building blocks of a node editor, hence the following nodes are part of the library:

### 1. The ```Node``` control
This type of node supports both ```Input``` and ```Output``` connectors as seen in the example below.

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