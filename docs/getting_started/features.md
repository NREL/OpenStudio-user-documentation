<h1>Current Features</h1>
OpenStudio is constantly being improved, with a less stable developer release available every 2 weeks and a stable major release quarterly (4 per year). The features that are available in the current major release are described below. To learn what is coming in the future, see the [Planned Features](../getting_started/roadmap.md) page.

## New in OpenStudio 1.5.0

#### Grid View for Thermal Zones and Space Types

Previously available for Refrigeration Walk Ins and Refrigeration Cases, grid-view (a grid-style interface providing detailed component views) has now been applied to the Space Types tab, as well as the Thermal Zones tab.

Viewing and editing your thermal zones and space types in a grid view allows you to see all your thermal zones at once and compare settings.

![Grid view example](img/features/grid_thumb.png)

#### Plug-in Works in SketchUp 2014

This update allows OpenStudio to leverage upon the improvements available in Ruby 2.0, and provides compatibility with SketchUp 2014. OpenStudio is no longer be compatible with SketchUp 2013 or SketchUp 8.

For the full list of added features go to the [__Release Notes on GitHub__](http://github.com/NREL/OpenStudio/releases)

View the [OpenStudio Roadmap](roadmap.md) to see the release plan for future features.
____________________________

## Current Features

As of OpenStudio Version 1.5.0

### Building Geometry/3D CAD

- Quickly draw 3D building geometry using free plugin for SketchUp
- Building envelope, shading on windows, shading from other buildings, etc.
- Draw detailed shapes, trace floor plans, or a combination
- Use wizard to create standard shapes (H, L, E, Courtyard, Rectangle)
- Import geometry from gbXML files (from Revit, GreenBuildingStudio, Trace700, etc.)
- Import geometry from EnergyPlus files (IDF)
- Import model from SDD files (California Energy Commission)
- Assign and visually inspect space types assignments
- Define thermal zones and add/remove spaces
- Assign and see building envelope constructions
- Add daylighting sensors

### Building Constructions and Materials

- Specify default materials for each type of surface and subsurface (ext walls, windows, floors, etc.) in building
- Specify detailed or simple window properties
- Built-in library of building constructions (walls, windows, doors, floors, etc.) for all DOE reference building types and vintages (pre-1980, 1980-2004, and 2004) plus ASHRAE 189.1-2009, ASHRAE 90.1-2007, and ASHRAE 90.1-2010
- Online library of building materials and their modeling properties from ASHRAE Handbook

### Building Loads

- Specify people, lights, plug loads, gas loads (cooking, etc.), steam loads, internal mass, water using equipment, ventilation requirements, and infiltration
- Can input loads per-area or add actual quantities to accommodate schematic and detailed design
- Built in library of space types (loads and associated schedules) for DOE reference buildings for all vintages (pre-1980, 1980-2004, and 2004) plus ASHRAE 189.1-2009, ASHRAE 90.1-2007, and ASHRAE 90.1-2010
- Can apply loads in one place (space type) and apply throughout the building

### HVAC

- Graphical representation of HVAC systems, zones, and their connections
- Drag-and-drop components onto diagram and click to edit
- HVAC system templates for ASHRAE Appendix G system types

##### Hot, Chilled, and Condenser Water Systems

- Boilers (all fuels)
- District heating and cooling
- Evaporative fluid coolers
- Single, two-speed, and variable-speed cooling towers
- Chillers (electric)
- Vertical ground heat exchanger (bore fields for ground-source heat pumps)
- Bypass pipes
- Constant and variable speed pumps
- Fluid-to-fluid heat exchangers (for primary/secondary pumping and waterside economizers, etc.)
- Hot, Chilled, and Condenser Water System Controls
- Scheduled, OA reset, high and low with deadband, and follow OA setpoint controls

##### Air System Components

- Supply and return plenums
- Unitary equipment
- Changeover bypass (VVT) systems
- Multi-stage unitary equipment (used with staged thermostats)
- Outdoor air intake with economizers (all types) and damper control
- Chilled water, one-speed DX and two-speed DX cooling coils
- Gas, electric, hot water, and DX (heat pump) heating and/or preheat coils
- Variable and Constant Speed Fans
- Steam humidifiers (electrically powered) used with zone humidistats
- Direct and indirect evaporative coolers
- Sensible and latent heat recovery
- VAV-Reheat and CAV-Reheat terminals (gas, electric, and hot water reheat coils)
- VAV no reheat terminals
- Series and parallel fan powered boxes with reheat (all fuel types)
- Diffusers
- Chilled beams (active and passive)
- Four-pipe induction terminals

##### Air System Controls

- Demand-controlled ventilation
- Night-cycle controls (whole system and/or terminal fans)
- Scheduled, OA reset, SAT reset, and follow OA setpoint controls
- Single-zone VAV system control (one control zone, many slaves)

##### Zone-level Heating and Cooling Systems

- Unit heaters (all fuels)
- Low temp radiant heating (electric, variable and constant flow water)
- Low temp radiant cooling (variable and constant flow water)
- PTAC (DX cooling + fan + all heating fuels)
- Water-source heat pump
- Air-source heat pump
- Exhaust fans
- Four pipe fan coils (may be supplied via DOAS system)
- Electric and hot-water baseboards
- High temperature radiant heaters (gas and electric)

##### Variable Refrigerant Flow Systems

- Condenser plus zone-level terminals

##### Commercial Refrigeration

- DX Refrigeration Systems
- Cascading DX Refrigeration Systems
- Fluid-filled DX Secondary Refrigeration Systems
- Cases
- Walk-in freezers
- Compressors
- Air, water, and evaporatively-cooled condensers
- Liquid-suction heat exchangers and mechanical subcoolers
- Heat-recovery to domestic hot water systems (desuperheater)
- Heat-recovery to unitary air systems (desuperheater)

##### Domestic Water Systems

- Hot Water Heaters (all fuels)
- Equipment that uses warm water (showers, faucets, etc.), can specify mixed water temp
- Equipment that uses cold water only
- Recirculation, no pump, or instantaneous water heaters

### Daylighting

- Add daylighting control points via the SketchUp plugin
- Run daylighting analysis using Radiance, state-of-the-art ray-tracing daylight simulation engine without making a separate model
- Lights in the EnergyPlus model controlled based on daylight available per Radiance

### Location-Specific Information

- Find typical [weather data and ASHRAE design conditions](http://apps1.eere.energy.gov/buildings/energyplus/weatherdata_about.cfm) for most locations in the world
- Use actual weather data (AMY) from a variety of vendors/sources

### Economics

- Full lifecycle costing (NIST Handbook 135 compliant) including built-in EIA fuel escalation rates and inflation
- Adjustable analysis period length
- Capital, recurring O&M, salvage, and replacement costs
- Lifecycle is adjustable per-cost (IE windows can last longer than lamps)
- Utility rates can include time-of-use, demand charges, ratchets, seasonal values, etc.
- Utility rates for Xcel Energy CO pre-made; users pick from list

### Import and Export Options

- IDF import (geometry, constructions, loads, thermal zones, and schedules only)
- IDF export (full model including HVAC)
- gbXML import (geometry, constructions, thermal zones, and schedules only)
- gbXML export (geometry, constructions, and thermal zones only)
- SDD import (simulation format - full model including HVAC)
- SDD export (input format - geometry, constructions, and thermal zones only)

### Analysis of Existing Buildings

- Enter utility bills for all fuel types in building
- Run model using actual weather data (AMY)
- Automatically compare model results to bills and shows goodness-of-fit by fuel type
- Automatically show whether goodness of fit meets common calibration standards (FEMP, ASHRAE)

### Libraries

- Space types (people, lights, equipment, ventilation, infiltration, schedules) for DOE reference buildings for all vintages (pre-1980, 1980-2004, and 2004), ASHRAE 189.1-2009, ASHRAE 90.1-2007, and ASHRAE 90.1-2010
- Building constructions (walls, windows, doors, floors, etc.) for DOE reference buildings for all vintages (pre-1980, 1980-2004, and 2004), ASHRAE 189.1-2009, ASHRAE 90.1-2007, and ASHRAE 90.1-2010
- Extensive online library of building materials from ASHRAE Handbook of Fundamentals
- Extensive online library of weather files and design day conditions

### Parametric Analysis

- OpenStudio Measures provide reliable and repeatable mechanism to apply ECMs to models
- Eliminates ambiguity and user error; all rules encapsulated in Measure itself
- More than 130 Measures available online and always growing
- Write Measure once and apply to many projects
- Perform complex ECMs, like full HVAC replacement, easily
- Quickly access online and local libraries of measures from drag-and-drop interface
- Edit user inputs to control how Measure modifies the model
- Creates meaningful results, ready for inclusion in reports to design team, building owners, etc.

### QAQC

- Measures can be used to check for common modeling errors
- Users don't have to understand to use; gives expert review to junior modelers more cheaply
- Automate key checks for Utility Regulators to keep up quality
- Lower time spent by reviewers on mundane checks; frees time to focus on real issues

### Reporting

- Measures can be used to create custom reports in HTML format (view in any web browser)
- Allows users to quickly visualize and summarize data for different audiences
- Reports are shareable via email
- Reports can be simple or highly interactive

### Cloud Computing

- Any user with an Amazon account can run simulations on cloud with 1 click
- Very cheap vs. engineer's time (16 simulations in parallel for ~$2.00/hr)
- Can run up to 300 simulation in parallel (costs scale in 16-processor increments)
- Enables small firms to access cloud computing without upfront hardware costs

### Share Modeling Best-Practices

- Online database called BCL (Building Component Library) can be used to share Measures
- BCL can be used to share building components
- Instantaneous world-wide distribution and updating of content
- Allows Utilities to ensure uniformity and best-practices across many EC firms

### Documentation

- More than 100 YouTube video tutorials
- Interactive PDFs describing each Application
- Measure writing guide
- Lifecycle costing guide
- Documentation of all modeling commands (SDK) online, updated bi-weekly

## Applications

The following applications are included in the OpenStudio installation:

### SketchUp Plug-in

- Select a template containing building space types and constructions as a starting point
- Trace a 2D footprint and extrude into 3D geometry
- Draw new or edit existing building geometry in 3D
- Use Measures to quickly build up the model
- Add site shading
- Assign building activity and thermal zones
- Add daylighting objects

### OpenStudio Application

- Add loads, schedules, space types, thermal zones, mechanical systems and more
- Create HVAC systems using a visual drag-and-drop interface
- Add refrigeration systems using a layout visual view and a grid view
- Add variable refrigerant flow systems using a layout visual view and a grid view
- Change the model programmatically using the _Apply Measure Now_ feature
- Run a simulation
- View high level simulation results and detailed simulation output
- Use reporting measures to create new/custom summary reports

### ResultsViewer

- View the detailed timeseries simulation results
- Create interactive line graphs and heat maps

### Parametric Analysis Tool (PAT)

- Select a baseline model to serve as the starting point for a parametric analysis
- Drag in Measures and set their input values
- Select combinations of Measures to run
- Run the simulations locally or on the cloud
- View a high-level comparison of the simulation results or dig into the detailed reports
