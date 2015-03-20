<h1>Radiance and OpenStudio</h1>
This tutorial explains how to use [Radiance](http://www.radiance-online.org/) to simulate the daylight ingress in your OpenStudio model, allowing for higher fidelity simulations of daylighting-related energy efficiency measures. For OpenStudio [v1.7.0](https://github.com/NREL/OpenStudio/releases/tag/v1.7.0), added support for window shades and wall thickness has increased the utility of the Radiance simulation option in the OpenStudio application. 

## Workflow
This tutorial describes the workflow for using OpenStudio (the plug-in and the application) to perform a [climate-based daylight simulation](http://climate-based-daylighting.com/doku.php?id=academic:climate-based-daylight-modelling), using Radiance as the lighting simulation engine (in lieu of EnergyPlus' daylight simulation options). For implementation details, and caveats, refer to the OpenStudio-Radiance Reference Guide.

The process for using Radiance for daylighting analysis in OpenStudio is not dissimilar from using EnergyPlus. The basic steps are as follows, with the required applications in parentheses:
### 1. Create (or Import) Building Geometry, Define Thermal Zones & Spaces (SketchUp Plug-in)

Many of the Radiance-related elements are not directly accessible from the OpenStudio Application, so regardless of whenther you are starting your geometric model from scratch or importing form another CAD tool, you must start in the SketchUp Plugin. 

Using the SketchUp Plugin tools, create the following elements:

* Building Shading Objects - to represent overhangs, fins, parapets
* Site Shading Objects - to represent other buildings, trees, ground
* [Interior Partition Surfaces](next_steps/sketchup_plugin_interface#NewInteriorPartitionSurfaceGroup) - can be used to define furniture, cubicle walls, & other relevant structures, in addition to refining the interior space geometry (e.g. adding columns, ceiling coffers, soffits)


###2. Add Daylighting Elements (SketchUp Plugin)

* Illuminance map(s)
* Daylighting control point(s)
* Glare sensors (optional)
* Define shading controls
* Assign shading controls

###3. Configure Daylighting Elements (SketchUp Plugin)

* Associate Space(s) to Thermal Zone(s)
* Assign Primary Illuminance Map to daylit Thermal Zone(s)
* Thermal zone load percentages to daylighting controls
* Attach shading controls to windows (user script)

###4. Define Materials (SketchUp Plug-in or OpenStudio Application)

* Interior finishes
* Glazing Surfaces

###5. Run Simulation (OpenStudio Application)
* Attach a weather file
* Run Radiance Selected on Run Tab
* Use Radiance results to run in Energy Plus

###6. Review Results (Results Viewer, Excel, et al.)
* radout.sql
* eplusout.sql
* daylightmetrics.csv
* *.ill


