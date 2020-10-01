# Overview

## Table of contents
* [Moving the viewport](#panning)
* [Zooming](#zooming)
* [Selecting items](#selecting)
* [Snapping to grid](#snapping)
* [Commands](#commands)

## Panning

Panning is done by holding right click and moving the mouse and can be disabled by setting the ```DisablePanning``` dependency property to ```true```.
> Note: It can be programmatically changed by setting the ```Offset``` dependency property.

While panning, the ```IsPanning``` dependency property will be set to ```true``` and the ```Viewport``` and ```AppliedTransform``` dependency properties will be updated.

Automatic panning is also enabled by default and can be disabled by setting the ```DisableAutoPanning``` dependency property to ```true```. The behavior is to pan the viewport when selecting or dragging a selection or a pending connection near the edges of the viewport. 

The auto panning speed can be changed using the ```AutoPanSpeed``` dependency property and the distance from the edge to trigger the panning can be changed using the ```AutoPanEdgeDistance``` dependency property.

Panning can also be used in combination with selecting and zooming while auto panning can be used with both selecting and zooming and also with dragging a selection or a pending connection.

Default values: 
* ```Offset```: [0, 0]
* ```DisablePanning```: false
* ```DisableAutoPanning```: false
* ```AutoPanSpeed```: 10 pixels per tick
* ```AutoPanEdgeDistance```: 15 pixels
* ```AutoPanningTickRate```: 1 millisecond

## Zooming 

Zooming is done by using the mouse wheel or by pressing ```CTRL +``` to zoom in or ```CTRL -``` to zoom out and can be disabled by setting the ```DisableZooming``` dependency property to ```true```. 
> Note: It can be programmatically changed by setting the ```Scale``` dependency property to a value between ```MinScale``` and ```MaxScale```.

While zooming, the ```Viewport``` and ```AppliedTransform``` dependency properties will be updated.

Zooming can also be used in combination with panning, dragging a selection or a pending connection. 

Default values:
* ```Scale```: 1
* ```MinScale```: 0.1
* ```MaxScale```: 2

## Selecting

Selecting items is done by holding the left mouse button and moving the mouse. When a selection operation is in progress, the ```IsSelecting``` dependency property is set to ```true``` and the ```SelectedArea``` dependency property is updated with each move.
> Note: Selected items can also be set programmatically by binding a collection to the ```SelectedItems``` dependency property.

If real-time selection is enabled (```EnableRealtimeSelection```: true), the items will be selected and deselected while you resize the selection rectangle. Otherwise the items contained in the ```SelectedArea``` will only be selected after the selection operation finished.

When an ```ItemContainer``` is selected, its ```IsSelected``` dependency property is set to ```true```.

Different behavior is used depending on the ```ModifierKeys``` held when starting a selection:
* ```Replace``` - no modifier key (default behavior, clears the selected items and starts a new selection)
* ```Append``` - shift key (adds to the current selected items)
* ```Remove``` - alt key (removes selection from the current selected items)
* ```Invert``` - control key (removes selected items and adds unselected items)

Selecting items can also be used in combination with panning and zooming. 

Default values:
* ```EnableRealtimeSelection```: true

## Snapping

When a selection is moved the ```GridCellSize``` dependency property will be used to determine where to snap the current selected items.
The snapping is relative to the position of the selected item and not the virtual grid.

If the selected items are not snapped to grid when they are initially created or if the ```GridCellSize``` is changed at runtime, the final position will be corrected after moving the selection if the ```EnableSnappingCorrection``` dependency property is ```true```.

Default values:
* ```GridCellSize```: 1
* ```EnableSnappingCorrection```: true

## Commands

The following ```RoutedUICommand```s are found in the ```EditorCommands``` class:
* ```ZoomIn``` - ```CTRL +``` (zoom in relative to the viewport's center)
* ```ZoomOut``` - ```CTRL -``` (zoom out relative to the viewport's center)
* ```SelectAll``` - ```CTRL A``` (select all items)
* ```Delete``` - ```Delete``` (delete selected items if ItemsSource is not bound)
* ```BringIntoView``` - Moves the viewport to the specified location, defaults to [0,0]. (```CommandParameter``` is location of type ```Point``` or ```string```)
* ```Align``` - Aligns the selected items using the specified alignment method, defaults to Top. (```CommandParameter``` is of type ```Alignment``` or ```string```. Possible alignment: Top, Left, Bottom, Right, Middle, Center)
 