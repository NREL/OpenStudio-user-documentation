<h1>Modeling Best Practices</h1>
This page is a collection of best practices that have been developed over time and by experience. Following these best practices will help you avoid the issues that users experience most often.

## General
- EnergyPlus is a detailed simulation engine, but you have to tell it how you want your building modeled. A common misunderstanding is that EnergyPlus will interpret "voids" between zones "correctly." EnergyPlus does not compute heat transfer between zones if they do not share a surface, so you must input the shared surfaces and set appropriate boundary conditions. To correctly model air transfer between zones, you have to add input objects that describe the airflow between zones. To model daylight transmission between zones, you need to add interior windows. Just because a building looks right, does not mean it is modeled correctly; digging in to the IDF and looking at detailed results is the only way to determine that you have modeled your building correctly.
- When you import an IDF into OpenStudio, it may be altered as part of the import process. For example, if your windows are not in the same plane as their base surface, OpenStudio moves them into the base surface plane. There may be other changes as well. 

## Guidelines for Spaces
- Spaces should be top-level objects. Do not combine multiple spaces into a group or component, or put a space under another group.
- Name your spaces to make large models easier to manage and search. You may want to name your surfaces and subsurfaces.
- Geometry within a space should be convex.
- Ideally, spaces, not just space surfaces, are also convex.

## Guidelines for Building Surfaces
- Model exterior walls to the outside face of the wall.
- Draw interior walls to their centerlines if possible. You may, however, choose any edge, as long as you are consistent with adjacent zones. Surfaces for adjacent zones must not overlap each other.
- As much as possible, you should avoid using curves (arcs or circles) to create your geometry. Curves and arcs will create faceted surfaces and increase simulation time. If you do use curves, set the segment count as low as possible. 

## Guidelines for Subsurfaces
- Do not place a subsurface (window or door) inside another subsurface.
- Do not place two subsurfaces against each other. Place a small space between them.
- Do not make a window the size of an entire base surface. Use SketchUp's Offset Tool to inset the sub-surface some nominal amount.
- Do not draw a subsurface that shares two edges with a base surface. This will create a new base surface. You can draw a window at the edge of wall, but not at the edge as well as the roof or floor.

## Guidelines for Interior Partition Surfaces
- By default interior partition surfaces are included and converted to internal mass objects for EnergyPlus simulation. Adding a large number of interior partitions surfaces will increase your simulation runtime. If this is a concern, you can model similar internal mass objects within a space as a single larger object.

## Guidelines for Shading Surfaces
- By default EnergyPlus mirrors shading surfaces, so typically face orientation does not matter. In some cases, however, such as when you add PV to a shading surface, it must be oriented correctly. 

<!--## Deciding on the Level of Detail for Your Model
## Run Simulations on Local Hard Drive.
## Don't use Undo in the SketchUp Plugin
## When Working in the SketchUp Plugin and OpenStudio Application at the Same Time Make sure to Manage Files Properly.
-->
