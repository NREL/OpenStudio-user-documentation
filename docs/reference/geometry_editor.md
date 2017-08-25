<h1>OpenStudio Geometry Editor</h1>
The [OpenStudio Geometry Editor](https://github.com/NREL/openstudio-geometry-editor) is a new, open source tool for creating geometry for building energy modeling.  The OpenStudio Geometry Editor is meant to cover simple building geometry use cases only.  More complex building geometry is best developed in a full featured CAD tool and exported to gbXML for building energy modeling.  The OpenStudio Geometry Editor is implemented in JavaScript with minimal dependencies, this allows it to be integrated into a wide range of web applications.  The OpenStudio Geometry Editor reads and writes a custom (floorplan.json)[https://raw.githubusercontent.com/NREL/openstudio-geometry-editor/develop/schema/geometry_schema.json] JSON file format.  New methods have been added to the OpenStudio SDK which can translate this file format to OSM.  Additionally, new methods have been added to OpenStudio SDK which allows two OSM files be merged.  These new functionalities have been demonstrated by integrating the OpenStudio Goemetry Editor into the OpenStudio Application.  The OpenStudio Geometry Editor and integration with the OpenStudio Application are still very experimental, they are not recommended for production workflows.  However, we invite users to try these tools out and provide feedback to help us make them better.  

------

## Getting Started
To try the OpenStudio Geometry Editor, first navigate to the Geometry vertical tab and then to the Editor tab.  At this time, OpenStudio Geometry Editor cannot be used on OpenStudio Models which have existing geometry (either developed in the OpenStudio SketchUp plug-in or imported through gbXML).  For models with no existing geometry a new floorplan can be created by pressing the New button next to the Floorplan dialog box.

[![Start Screen](img/geometry_editor/start_screen.png "Start Screen")](img/geometry_editor/start_screen.png)

After pressing the New button, you will be prompted to either open an existing floorplan file, create a new floorplan file, or create a new floorplan file with a map background (e.g. if you want to trace an existing building from satellite imagery).  In this example we will choose to use the map background for reference.  

[![Initial Dialog](img/geometry_editor/initial_dialog.png "Initial Dialog")](img/geometry_editor/initial_dialog.png)

When using a map background, you will be taken to the location specified in your OSM model as a starting point.  Navigate on the map to the actual place you want to locate your building using the "Search for a location" box as well as usual map navigation controls with your mouse. Once you have selected where you want to place your building, use the cross hair tool to select your building's origin.  You may want to rotate your view (press alt + shift) to align your building with the x, y axes in the editor.  Press the Done button to place your building and set the rotation.  Note that building placement is currently a one time operation that cannot be changed once the building is located.

[![Rotate 1](img/geometry_editor/rotate1.png "Rotate 1")](img/geometry_editor/rotate1.png)

[![Rotate 2](img/geometry_editor/rotate2.png "Rotate 2")](img/geometry_editor/rotate2.png)

------

## Drawing Spaces
The navigator in the upper left corner of the editor is used to select the current story and space for the drawing area.  The geometry for the current story is shown, the geometry for the previous story can be toggled on and off using the "Story Below" check box.  A grid can also be toggled on and off for reference when drawing, the grid spacing can be set as well.  Note that the units selected for drawing are set based on the OpenStudio Application's units preferences at the time the floorplan is created, currently these cannot be changed after the initial setting.  At this stage of the OpenStudio Geometry Editor development, we are testing two drawing modes.  "Strict Grid" only allows drawing operations on the grid, "Edges Too" is more general and allows the user to reference existing edges when drawing.  We invite users to try both modes and let us know what you think.  To add geometry to the current space, select either the Rectangle or Polygon tool.  Geometry drawn is added to the currently selected space.  

[![Space 1](img/geometry_editor/space1.png "Space 1")](img/geometry_editor/space1.png)

Once you have drawn geometry for a space, you can extend the geometry by drawing a new shape which overlaps existing space geometry.  To delete geometry from a space, use the Eraser tool. Note that you cannot draw new geometry for a space that does not intersect existing space geometry.  Additionally, you cannot use the eraser tool to divide a single space geometry into two or more pieces. 

[![Space 1-2](img/geometry_editor/space1-2.png "Space 1-2")](img/geometry_editor/space1-2.png)

To create geometry for a new space, first create the new space by using the "+Space" button in the navigator.  Then, with the new space selected, draw the new space geometry.  If new space geometry overlaps existing geometry in another space, then the new geometry will be created and existing geometry in the other space will be reduced.  Geometry for multiple spaces cannot overlap.  

[![Space 2](img/geometry_editor/space2.png "Space 2")](img/geometry_editor/space2.png)

You can continue in this way to create geometry for the current story.

[![All Spaces](img/geometry_editor/all_spaces.png "All Spaces")](img/geometry_editor/all_spaces.png)

Press the "+Story" button to create a new story.  This will automatically create a new space for the second story that you can begin to define geometry for.

[![Story 2](img/geometry_editor/story2.png "Story 2")](img/geometry_editor/story2.png)

------

## Bottom Panel
The bottom panel provides access to edit items in the floorplan.  You can select the type of object to display in this panel, all objects of that type are displayed.  Press the "New" button to create new objects of that type.  You can use this functionality to create new Thermal Zones.

[![Thermal Zone 1](img/geometry_editor/thermal_zone-1.png "Thermal Zone 1")](img/geometry_editor/thermal_zone-1.png)

[![Thermal Zone 2](img/geometry_editor/thermal_zone-2.png "Thermal Zone 2")](img/geometry_editor/thermal_zone-2.png)

You can assign thermal zones and other properties to spaces by selecting the "Space" object type. 

[![All Spaces](img/geometry_editor/all_spaces.png "All Spaces")](img/geometry_editor/all_spaces.png)

You can set properties for the story such as "Floor to Ceiling Height".  Setting "Below Floor Plenum Height" or "Above Ceiling Plenum Height" to non-zero values will result in plenum geometry creation.

[![Story 2-1](img/geometry_editor/story2-1.png "Story 2-1")](img/geometry_editor/story2-1.png)

------

## Preview and Merge
At any time, you can preview your floorplan in 3D by pressing the "Preview" button.  

[![Preview 1](img/geometry_editor/preview1.png "Preview 1")](img/geometry_editor/preview1.png)

[![Preview 2](img/geometry_editor/preview2.png "Preview 2")](img/geometry_editor/preview2.png)

However, your OSM model will not be altered until you press the "Merge" button.  Performing a merge will translate your floorplan to OSM, then merge that OSM with your current OSM.  Any geometry in your current OSM will be replaced by new geometry from the floorplan OSM.  However, non geometry objects such as HVAC in your current OSM will be preserved.  In future versions of the OpenStudio Application, we plan to use this same functionality to allow OSM models to be updated with multiple versions of gbXML.

[![Merge](img/geometry_editor/merge.png "Merge")](img/geometry_editor/merge.png)

Once your floorplan has been merged with the current OSM you will see new objects defined in your floorplan in the rest of the OpenStudio Application.

[![Post Merge](img/geometry_editor/post-merge.png "Post Merge")](img/geometry_editor/post-merge.png)

[![Space Tab](img/geometry_editor/space-tab.png "Space Tab")](img/geometry_editor/space-tab.png)

The intention of the integration of the OpenStudio Geometry Editor with the OpenStudio Application is that you should be able to move seemlessly between the OpenStudio Application and the OpenStudio Geometry Editor.  Thermal Zones, Space Types, Default Construction Sets, and Building Units should be synchronized between the two in intuitive ways.  However, since this functionality is very new, some rough edges are expected.  Please let us know of issues you find by sending email to OpenStudio@nrel.gov.  If the OpenStudio Geometry Editor becomes unresponsive, please press the Debug button and navigate to the console to find additional information that might help us identify and fix any issues.
