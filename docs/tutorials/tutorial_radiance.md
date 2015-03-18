<h1>Radiance and OpenStudio</h1>
This tutorial explains how to use [Radiance](http://www.radiance-online.org/) to simulate the daylight ingress in your OpenStudio model, allowing for higher fidelity simulations of daylighting-related energy efficiency measures. For OpenStudio [v1.7.0](https://github.com/NREL/OpenStudio/releases/tag/v1.7.0), added support for window shades and wall thickness has increased the utility of the Radiance simulation option in the OpenStudio application. 

## Overview
This tutorial describes the workflow for using OpenStudio (the plug-in and the application) to perform a [climate-based daylight simulation](http://climate-based-daylighting.com/doku.php?id=academic:climate-based-daylight-modelling), using Radiance as the lighting simulation engine (in lieu of EnergyPlus' daylight simulation options). For implementation details, and caveats, refer to the OpenStudio-Radiance Reference Guide.

### 1. Create building model (SketchUp Plug-in)
__Create Geometry, Define Thermal Zones & Spaces Building Geometry__
* Building Shading surfaces (overhangs, fins, parapets)
* Site Shading (other buildings, trees, ground)
* Interior Partitions-Furniture, cubicle walls, & other relevant structures

__Add Daylighting Objects__
* Illuminance map(s)
* Daylighting control point(s)
* Glare sensors- add and move to correct spot, pick number of glare vectors
* Define shading controls
* Assign shading controls

__Hook Up Elements__

* Associate Space(s) to Thermal Zone(s)
* Assign Primary Illuminance Map to daylit Thermal Zone(s)
* Thermal zone load percentages to daylighting controls
* Attach shading controls to windows (user script)

###2. SketchUp Plug-in or OpenStudio Application

__Define Materials__
* Interior finishes
* Glazing Surfaces

###3. OpenStudio Application
* Attach a weather file
* Run Radiance Selected on Run Tab
* Use Radiance results to run in Energy Plus

###4. Results Viewer
* radout.sql
* eplusout.sql


![Add Window Property Frame and Divider](img/tutorials/windowproperty_frameanddivider1.jpg)

### Importing IDF files from the WINDOW program
IDF files exported from [WINDOW](http://windows.lbl.gov/software/window/window.html) containing Window Property Frame and Divider objects can be imported using the OpenStudio SketchUp plug-in via Extensions>OpenStudio>Import>Import EnergyPlus Idf Constructions.  WINDOW exports two IDF files, a *_Avg.idf and a *_Spec.idf file. Only the *_Avg.idf file may be imported as the MaterialProperty:GlazingSpectralData object in the *_Spec.idf file is not yet supported by OpenStudio.

![Import Window Property Frame and Divider](img/tutorials/windowproperty_frameanddivider2.jpg)

## Apply Window Property Frame and Divider
Once you have a Window Property Frame and Divider object in your model, you can apply it to sub surfaces using the object inspector.  Only exterior windows and glass doors can reference Window Property Frame and Divider objects.

![Set Window Property Frame and Divider](img/tutorials/windowproperty_frameanddivider3.jpg)

The Window Property Frame and Divider object can also be applied to all valid sub surfaces in the current selection using the OpenStudio user script "Set Window Property Frame and Divider" under "Alter or Add Model Elements.

![Add Window Property Frame and Divider Script](img/tutorials/windowproperty_frameanddivider4.jpg)


