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

###2. Define Materials (SketchUp Plug-in or OpenStudio Application)
It is recommended to review the materials of your model constructions to ensure the photometric properties, e.g., visible light transmittance, transmittance model (specular or diffuse), and visible light reflectance, are correct. 

* Interior finishes
* Glazing

###3. Add Daylighting Elements (SketchUp Plugin)

For each space where you wish to analyze daylighting, add:
* Illuminance map (primary)
* Daylighting control point (primary)
* Define shading controls
* Assign shading controls

Optionally to these spaces, add:
* Glare sensors
* Create & assign OS:WindowFrameAndDivider objects, to represent wall thickness in the Radiance model (user script) 

###4. Configure Daylighting Elements (SketchUp Plugin)

* Associate Space with Thermal Zone(s)
* Assign primary Illuminance Map to daylit Thermal Zone(s)
* Assign primary Daylightng Control Point to Thermal Zone
* Thermal zone load percentages to daylighting controls
* Attach shading controls to windows (user script)

###5. Run Simulation (OpenStudio Application)
* Attach a weather file
* Select "Radiance" as the daylight simulation engine on the Run Tab

The Radiance daylighting results will inform the electric lighting load schedules and will be automatically used in the EnergyPlus model

###6. Review Results (Results Viewer, Excel, et al.)
The results of the Radiance/EnergyPlus simulation are stored in a few locations:
* **radout.sql** - this file contains the Radiance-computed daylighting information, as well as the exterior daylight data from the weather file, for reference.
* **daylightmetrics.csv** -
* **_windowgroup_.ill** - 
* **eplusout.sql** - the electric lighting schedules


