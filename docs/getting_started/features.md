<h1>Current Features</h1>
OpenStudio is constantly being improved, with a less stable developer release available every 2 weeks and a stable major release quarterly (4 per year). The features that are available in the current major release are described below. To learn what is coming in the future, see the [Planned Features](../getting_started/roadmap.md) page.

##OpenStudio 1.11.0 

##### Some of the more noteworthy new features and bug fixes are listed below: 

* OpenStudio now supports EnergyPlus version 8.5.0
* OpenStudio now includes Radiance version 5.0.a.8 
* Added support for graphical dual duct system layout in the OpenStudio Application
* Added class PointLatLon for converting geographic coordinates to building coordinates
*  Added version_modified element to BCL Measure XML
* Correct parsing of ISO 8601 formatted time strings
* Radiance measure now supports multiple (unlimited) glare sensors per space
* Construction inheritance is now displayed in the space tab

## OpenStudio 1.10.0 

##### Some of the more noteworthy new features and bug fixes are listed below: 
*	Updated plug-in to work with SketchUp 2016.  SketchUp autosave will no longer save the osm.  Surfaces referencing constructions with no layers are no longer shown as air walls in the plug-in.*	Fixed code in Date and Time classes that resulted in memory access violation crashes in Ruby bindings. *	Changed operation of ConstructionBase.getNetArea, see documentation for details.*	Deprecated field 'Source Zone Infiltration Treatment' from object ZoneAirMassFlowConservation, adding E+ 8.4 fields 'Infiltration Balancing Method' and 'Infiltration Balancing Zones'.*	The Radiance Daylighting Measure has the following additions:	*	Added support for electrochromic glazing (two-state)	*	Renderings are generated for each primary daylighting control point and glare sensor found in the model	*	Added ability to optionally generate "debug" images showing each window group octree*	Made minor enhancements to standard OpenStudio simulation results. *	Added water to water heat pump component models, including HeatPumpWaterToWaterEquationFitCooling and HeatPumpWaterToWaterEquationFitHeating.*	Added capability to assign DesignSpecificationOutdoorAir object directly on VAV air terminals, including  AirTerminalSingleDuctVAVReheat and AirTerminalSingleDuctVAVNoReheat. This is an EnergyPlus feature that allows for more precise outdoor air control, but was previously not available in OpenStudio.*	Refined GridView elements in the OpenStudio Application to increase their performance.*	Extended OSGridController and SpacesLoadsGridView to show loads inherited from SpaceTypes, and more generally, inherited subrows.OpenStudio 1.10.0 includes several other minor features as well as many bug fixes. For a full list of changes included in OpenStudio 1.10.0, please see the [complete changelog](http://github.com/NREL/OpenStudio/blob/v1.10.0/CHANGELOG.md).

## New in OpenStudio 1.9.0

OpenStudio 1.9.0 adds a substantial number of new HVAC features. Among the new features are three entirely new categories of HVAC capability beyond the routine component additions. The first new category is a family of availability managers that allow for detailed control over the air system period of operation. With these new availability managers, it is possible to have detailed control over night cycling, night ventilation, optimum morning start, temperature-based on/off and more. The second new category of HVAC capability included in this release is another family of control related inputs known as plant operation schemes. With plant operation schemes, it is possible to control the sequencing of plant system supply components relative to one another while considering ambient conditions. Third, OpenStudio has added support for dual duct air based systems. These new features are available through the OpenStudio API and Measures; user interface controls will be added in a future release. All of these features are backwards compatible, meaning users now have access to detailed control inputs, but the established OpenStudio default control remains in place. Therefore, these new features can be utilized on an as-needed basis and existing models will continue to operate in the same way. Examples and tutorials of applying these new features will be available in the weeks following the release of OpenStudio 1.9.0.

<iframe width="640" height="360" src="http://www.youtube.com/embed/9uBcb3NBQ84" allowfullscreen></iframe>

*Above: This video demonstrates the new Spaces tab and the redesigned Facilities tab.*
There are significant additions at the HVAC component level, including a large number of new coil types, Zone HVAC, and plant components. Of particular interest are a number of new variable speed DX coils, new zone mixing inputs, a new Zone HVAC model that accommodates natural ventilation, idealized plant components that allow a user defined constant temperature source on the supply side, and a user defined load on the demand. The full list of new input object types is included below. All of these are available in the OpenStudio API and Measures, and many of them are available in the graphical interface through drag and drop.
* ZoneCrossMixing 
* ZoneMixing 
* SolarCollectorPerformanceFlatPlate 
* SolarCollectorFlatPlateWater 
* SolarCollectorIntegralCollectorStorage 
* SolarCollectorPerformanceIntegralCollectorStorage 
* SolarCollectorFlatPlatePhotovoltaicThermal 
* ZoneVentilationDesignFlowRate 
* FluidCoolerTwoSpeed 
* FluidCoolerSingleSpeed 
* PipeOutdoor 
* PipeIndoor 
* Duct
* AvailabilityManagerHybridVentilation 
* CoilSystemCoolingWaterHeatExchangerAssisted 
* CoilSystemCoolingDXHeatExchangerAssisted 
* PlantEquipmentOperationOutdoorDewpoint 
* PlantEquipmentOperationOutdoorWetBulb
* TemperingValve 
* ChillerAbsorption 
* ChillerAbsorptionIndirect 
* CoilCoolingDXTwoStageWithHumidityControlMode 
* AirTerminalDualDuctVAV 
* AvailabilityManagerOptimumStart 
* AvailabilityManagerDifferentialThermostat 
* ThermalStorageIceDetailed 
* GroundHeatExchangerHorizontalTrench 
* PlantEquipmentOperationOutdoorRelativeHumidity 
* AvailabilityManagerNightVentilation 
* PlantEquipmentOperationOutdoorDryBulbDifference
* PlantEquipmentOperationOutdoorDewpointDifference 
* PlantEquipmentOperationOutdoorWetBulbDifference 
* PlantEquipmentOperationOutdoorDryBulb 
* HeaderedPumpsConstantSpeed 
* HeaderedPumpsVariableSpeed 
* WaterHeaterHeatPump 
* CoilPerformanceDXCooling 
* CoilWaterHeatingAirToWaterHeatPump 
* CoilHeatingWaterToAirHeatPumpVariableSpeedEquationFit 
* CoilHeatingDXVariableSpeed 
* CoilCoolingWaterToAirHeatPumpVariableSpeedEquationFit 
* SetpointManagerSingleZoneHumidityMaximum 
* ThermalStorageChilledWaterStratified 
* SetpointManagerColdest 
* EvaporativeFluidCoolerTwoSpeed
* SetpointManagerMultiZoneCoolingAverage 
* SetpointManagerMultiZoneHeatingAverage 
* ZoneHVACDehumidifierDX 
* ZoneHVACEnergyRecoveryVentilatorController 
* ZoneHVACEnergyRecoveryVentilator 
* CoilCoolingDXVariableSpeed 
* CentralHeatPumpSystem 
* SetpointManagerMultiZoneHumidityMaximum 
* CoilHeatingDXMultiSpeed 
* SetpointManagerFollowSystemNodeTemperature 
* SetpointManagerSingleZoneOneStageCooling 
* SetpointManagerSingleZoneOneStageHeating 
* SetpointManagerMultiZoneMaximumHumidityAverage
* SetpointManagerMultiZoneMinimumHumidityAverage 
* SetpointManagerReturnAirBypassFlow 
* SetpointManagerFollowGroundTemperature 
* ChillerHeaterPerformanceElectricEIR 
* PlantComponentTemperatureSource 
* ZoneHVACUnitVentilator 
* WaterHeaterStratified 
* ZoneHVACBaseboardRadiantConvectiveWater 
* ZoneHVACBaseboardRadiantConvectiveElectric 
* LoadProfilePlant

There are a number of enhancements in areas beyond HVAC capability particularly to the OpenStudio application and the Measure ecosystem:
The OpenStudio application has been enhanced with new grid views for the design day and facility interfaces. A spaces grid tab was also added.

* Users can now specify costs and ECMs on external models imported to PAT for export to EDAPT    * A new standard reporting Measure has been added
* Radiance functionality has been refactored as a Measure; as a result, the “select daylight simulation engine” radio buttons have been removed from the Run Tab. Users wishing to use Radiance for their daylight simulations must apply the “Radiance Daylighting Measure” from their measures library (under Electric Lighting / Electric Lighting Controls / Radiance Daylighting Measure) as an “Always Run Measure”. Support for shadecloth (e.g. Mechoshade) and daylight redirecting louvers (exemplified in this release with Lightlouver) have been added to the shade material types along with the existing venetian blind option. Daylight metrics reporting has been improved, and a fully automated 3-phase simulation workflow that supports multiple window groups is part of this new measure. As a measure, this also allows users to run Radiance-based daylighting simulations with PAT and OpenStudio Server.
* OpenStudio ships with select gems [(https://github.com/NREL/OpenStudio/wiki/OpenStudio- Version-Compatibility-Matrix#packaged-gems)](https://github.com/NREL/OpenStudio/wiki/OpenStudio- Version-Compatibility-Matrix#packaged-gems)
* Improvements have been made to EpwFile allow direct access to timeseries properties from the weather file"
* IFC import improvements were contributed by the BIMDataHub team at Penn State/CBEI"
* This release resolves a long-standing issue using OpenStudio with Honeybee: [https://github.com/mostaphaRoudsari/Honeybee/issues/214](https://github.com/mostaphaRoudsari/Honeybee/issues/214).

OpenStudio 1.9.0 includes several other minor features as well as many bug fixes. For a full list of changes included in OpenStudio 1.9.0, please see the [complete changelog](https://github.com/NREL/OpenStudio/blob/v1.9.0/CHANGELOG.md).

View the [OpenStudio Roadmap](roadmap.md) to see the release plan for future features.
____________________________

## Current Features

As of OpenStudio Version 1.9.0

### Building Geometry/3D CAD

- Quickly draw 3D building geometry using free plug-in for SketchUp
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

### Grid View for Thermal Zones and Space Types

- Previously available for Refrigeration Walk Ins and Refrigeration Cases, grid-view (a grid-style interface providing detailed component views) has now been applied to the Space Types tab, as well as the Thermal Zones tab.
- Viewing and editing your thermal zones and space types in a grid view allows you to see all your thermal zones at once and compare settings.

![Grid view example](img/features/grid_thumb.png)

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
