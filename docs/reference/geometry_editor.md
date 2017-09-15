<h1>OpenStudio Geometry Editor</h1>
The [OpenStudio Geometry Editor](https://github.com/NREL/openstudio-geometry-editor) is a new, open source software module that developers can leverage to produce building energy modeling UIs that include geometry creation.  The OpenStudio Geometry Editor is meant to cover simple building geometry use cases only.  More complex building geometry is best developed in a full featured CAD tool and exported to gbXML for building energy modeling.  The OpenStudio Geometry Editor is implemented in JavaScript with minimal dependencies, allowing it to be integrated into a wide range of applications.  The OpenStudio Geometry Editor reads and writes a custom [floorplan.json](https://raw.githubusercontent.com/NREL/openstudio-geometry-editor/develop/schema/geometry_schema.json) JSON file format.  New methods have been added to the OpenStudio SDK, which can translate this file format to OSM.  Additionally, new methods have been added to the SDK, which allows two OpenStudio Models to be merged.  These new methods are demonstrated by integrating the Geometry Editor directly within the OpenStudio Application.  The OpenStudio Geometry Editor and integration within the OpenStudio Application are experimental, and are not recommended for production workflows.  However, we invite users to try these software components out and provide feedback to help us make them better for use by third party developers.

------

## Getting Started
To try the OpenStudio Geometry Editor within the OpenStudio Application, first navigate to the "Geometry" vertical tab and then to the "Editor" sub tab.  At this time, OpenStudio Geometry Editor cannot be used on previously created OpenStudio Models with existing geometry (either developed in the OpenStudio SketchUp plug-in, imported through gbXML, or procedurally generated from scripts like the DOE Prototype Measure) as these models do not include the requisite floorplan.json file used by the editor.  For models with no existing geometry a new floorplan may be created by pressing the "New" button next to the "Floorplan" dialog box.  Existing OpenStudio Models that include a floorplan.json model may be edited.

[![Start Screen](img/geometry_editor/start_screen.png "Start Screen")](img/geometry_editor/start_screen.png)

After pressing the "New" button, you will be prompted to open an existing floorplan file, create a new floorplan file, or create a new floorplan file with a map background.  The last option is useful for geolocating and tracing existing building geometry from satellite imagery.  In this example we will choose to use the map background for reference.  

[![Initial Dialog](img/geometry_editor/initial_dialog.png "Initial Dialog")](img/geometry_editor/initial_dialog.png)

When using a map background, you will be taken to the location specified in your OpenStudio Model as a starting point.  Navigate on the map to the actual place you want to locate your building using the "Search for a location" box and map navigation controls. Once you have selected where you want to place your building, use the cross hair tool to select your building's origin.  You may wish to rotate your view (press alt + shift) to align your building with the x, y axes in the editor.  Press the "Done" button to place your building and set the rotation.  Note that building placement is currently a one time operation that cannot be changed once the building is located.

[![Rotate 1](img/geometry_editor/rotate1.png "Rotate 1")](img/geometry_editor/rotate1.png)

[![Rotate 2](img/geometry_editor/rotate2.png "Rotate 2")](img/geometry_editor/rotate2.png)

------

## Drawing Spaces
The navigator in the upper left corner of the editor is used to select the current story and space for the drawing area.  The geometry for the current story is shown, the geometry for the previous story can be toggled on and off using the "Story Below" check box.  A grid can also be toggled on and off for reference when drawing.  The grid spacing may be customized as well.  Note that the units selected for drawing are set based on the OpenStudio Application's units preferences at the time the floorplan is created.  Currently, the floorplan units selection may not be changed after the initial setting.  At this stage of the OpenStudio Geometry Editor development, we are testing two drawing modes.  "Strict Grid" only allows drawing operations on the grid, "Edges Too" is more general and allows the user to snap drawing tools to the nearest existing edges when drawing.  We invite users to try both modes and provide feedback.  To add geometry to the current space, select either the "Rectangle" or "Polygon" tool.

[![Space 1](img/geometry_editor/space1.png "Space 1")](img/geometry_editor/space1.png)

Once you have drawn geometry for a space, you can extend it by drawing an additional rectangle or polygon, which overlaps the existing space geometry.  This allows the creation of more complex space boundaries.  Use the "Eraser" tool to completely erase or to create cutouts within a space. Note that you cannot add new geometry for a space that does not intersect existing space geometry.  Additionally, you cannot use the eraser tool to divide a single space geometry into two or more separate pieces. 

[![Space 1-2](img/geometry_editor/space1-2.png "Space 1-2")](img/geometry_editor/space1-2.png)

To create geometry for additional spaces, first create the new space by using the "+Space" button in the navigator.  Then, with the new space selected, draw the new space geometry.  If new space geometry overlaps existing geometry in another space, then the new geometry will be created and existing geometry in the other space will be reduced.  Geometry for multiple spaces cannot overlap.  

[![Space 2](img/geometry_editor/space2.png "Space 2")](img/geometry_editor/space2.png)

Continue in this way to create all of the spaces for the current story.

[![All Spaces](img/geometry_editor/all_spaces.png "All Spaces")](img/geometry_editor/all_spaces.png)

Press the "+Story" button to create a new story.  This will automatically create a new space for the second story that you can begin to define geometry for.

[![Story 2](img/geometry_editor/story2.png "Story 2")](img/geometry_editor/story2.png)

------

## Image Import
Existing floorplan images can be imported in to the OpenStudio Geometry Editor for reference when drawing.  At this time, only JPEG and PNG formats are supported; PDF, DXF, and other common formats may be supported in the future.  Floorplan images are associated with a particular story in the editor.  Navigate to the story of interest (usually the first floor) and change the object type above the navigator to "Image".  Press the "+Image" button and navigate to your image. 

[![Image Import](img/geometry_editor/image_import.png "Image Import")](img/geometry_editor/image_import.png)

Once the image is imported, activate the "Drag" tool.  This will allow you to move, resize, and rotate the image.

[![Image Drag](img/geometry_editor/image_drag.png "Image Drag")](img/geometry_editor/image_drag.png)

Once you have correctly sized and positioned you image, change the object type above the navigator to "Space" and generate space geometry on top of the image.

------

## Bottom Panel
The bottom panel provides access to specify and edit data associated with the floorplan such as space types, thermal zones, and constructions.  Objects of these types are imported from your OpenStudio Model each time you switch to the "Editor" sub tab.  You can select the type of object to display in this panel.  All objects of that type are displayed.  Press the "New" button to create new objects of that type.  For example, you can use this functionality to create new thermal zones.

[![Thermal Zone 1](img/geometry_editor/thermal_zone-1.png "Thermal Zone 1")](img/geometry_editor/thermal_zone-1.png)

[![Thermal Zone 2](img/geometry_editor/thermal_zone-2.png "Thermal Zone 2")](img/geometry_editor/thermal_zone-2.png)

You can assign thermal zones and other properties to spaces by selecting the "Space" object type and making selections in the thermal zone field for each space.

[![All Spaces](img/geometry_editor/all_spaces.png "All Spaces")](img/geometry_editor/all_spaces.png)

You can also set properties for stories such as "Floor to Ceiling Height".  Setting "Below Floor Plenum Height" or "Above Ceiling Plenum Height" to non-zero values will result in plenum geometry creation.

[![Story 2-1](img/geometry_editor/story2-1.png "Story 2-1")](img/geometry_editor/story2-1.png)

------

## Preview and Merge
At any time, you can preview your floorplan in 3D by pressing the "Preview" button.  

[![Preview 1](img/geometry_editor/preview1.png "Preview 1")](img/geometry_editor/preview1.png)

[![Preview 2](img/geometry_editor/preview2.png "Preview 2")](img/geometry_editor/preview2.png)

Your OpenStudio Model is not altered until you press the "Merge" button.  Performing a merge translates your floorplan to a new OpenStudio Model that is merged them with your current OpenStudio Model.  Any geometry in your current OSM will be replaced by new geometry from the floorplan OSM.  However, non-geometry objects such as HVAC in your current OSM will be preserved.

[![Merge](img/geometry_editor/merge.png "Merge")](img/geometry_editor/merge.png)

Once your floorplan has been merged with the current OSM you will see new objects associated with your floorplan throughout the rest of the OpenStudio Application.

[![Post Merge](img/geometry_editor/post-merge.png "Post Merge")](img/geometry_editor/post-merge.png)

[![Space Tab](img/geometry_editor/space-tab.png "Space Tab")](img/geometry_editor/space-tab.png)

The intention of integrating the OpenStudio Geometry Editor with the OpenStudio Application is to demonstrate how geometry data may be moved seamlessly into the OpenStudio object model to support a variety of sophisticated workflows.  Thermal zones, space types, default construction sets, and building units are synchronized between the two interfaces intuitively and with little effort on the part of the user.  As with any new software feature, some rough edges are expected.  Please let us know of issues you find by sending email to [OpenStudio@nrel.gov](mailto:OpenStudio@nrel.gov).  If the OpenStudio Geometry Editor becomes unresponsive, please press the "Debug" button, navigate to the console, and cut/paste diagnostic messages that may help us identify and fix any issues. 

