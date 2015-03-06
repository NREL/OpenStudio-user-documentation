<h1>Installation and Introductory Tutorial</h1>
This page walks you through installing OpenStudio, the basics of the applications, and the basic workflow.

## Installation Instructions
OpenStudio is supported on Windows 7 - 8.1, OS X 10.9 - 10.10, and 64-bit Ubuntu 14.04.

OpenStudio 1.6.0 works with EnergyPlus 8.2.0 Update 1, which is now bundled with the OpenStudio installer.  It is no longer necessary to download and install EnergyPlus separately.

__Download and install SketchUp__

1. The OpenStudio SketchUp Plug-in requires [SketchUp 2015](http://www.sketchup.com/) (not available for Linux). Older versions of SketchUp are not supported.  SketchUp 2015 is available in 32 and 64 bit versions, the 32 bit version of OpenStudio on Windows will only work with the 32 bit version of SketchUp 2015 and the 64 bit version of OpenStudio will only work with the 64 bit version of SketchUp 2015.

__Download and install OpenStudio__

1. Login to the [OpenStudio website](www.openstudio.net). Create an account if you don't have one.
2. Click "Downloads" at the top of the page.
3. Choose the installer that matches your operating system. The OpenStudio package contains the following tools:
    - SketchUp Plug-in
    - OpenStudio Application
    - ParametricAnalysisTool(PAT)
    - ResultsViewer

__Optional - Setup a Building Component Library (BCL) Account__
BCL content can now be accessed from within the OpenStudio SketchUp Plug-in and from the standalone OpenStudio application. To take advantage of this integration, you will need to follow the steps outlined here to request a BCL key.

1. Login to [Building Component Library (BCL)](https://bcl.nrel.gov/). Create an account if you don't have one. Follow the instructions from the email sent to you upon registration and then login.
2. Click on the `My Dashboard` near the top right of the website.
3. Copy the text after `API v1.1 key`: then paste the key into the SketchUp Plug-in, the OpenStudio application, or the Parametric Analysis Tool (PAT). __You only need to configure the key in one place and it will be used globally throughout the OpenStudio tools.__ Additionally, this key will be maintained when you install updates to OpenStudio.

Enter the key through the OpenStudio SketchUp Plug-in under the menu `Plugins->OpenStudio User Scripts->Building Component Library->Setup BCL Key` and click `OK`. __Or__ register the key through the OpenStudio Application under the menu `Components & Measures->Find Components`. If a key is not already registered, it will prompt you for one.

![Key request dialog](img/bcl_key_request.png)

__Optional - Install Radiance__
If you want to be able to use Radiance for daylighting simulations, you must install Radiance.

1. Download and install [Radiance 4.2.2](https://github.com/NREL/Radiance/releases/tag/4.2.2).

__Optional - Install Ruby__
If you plan to use the OpenStudio SDK Ruby bindings via command prompt on Windows, you must install Ruby. OS X already has Ruby installed.

1. Download the [Ruby 2.0.0](http://rubyinstaller.org/downloads/) installer.  If you have the Windows (x64) version of OpenStudio (Help>About>Compiler shows Visual Studio 12 2013 Win64), you'll need the x64 Ruby installer.  If you have the Windows (x32) version of OpenStudio, you'll need the non-x64 Ruby installer.
2. Add `C:\Ruby200\bin` (or wherever you installed Ruby) to the PATH environment variable. [Detailed instructions](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx).
3. Create a text file with the following text inside:

    ```
    require 'C:\Program Files (x86)\OpenStudio 1.6.0\Ruby\openstudio.rb'
    ```

4. Save the file as `openstudio.rb` here: `C:\Ruby200\lib\ruby\site_ruby\openstudio.rb` (next to the `2.0.0` folder).
5. Test your installation by opening a command prompt and typing: `irb` ENTER.  Then, type `require 'openstudio` ENTER.  If you see some QSslSocket messages and => true, it's working.

## Workflow Overview
After installing OpenStudio you will have the SketchUp Plug-in, OpenStudio Application, ParametricAnalysisTool (PAT) and ResultsViewer. The typical OpenStudio workflow is shown in the diagram below.

[![Workflow Diagram](img/workflow_diagram.png "Click to view")](img/workflow_diagram.png)

*About: Click on the diagram above to view a larger version.*

ResultsViewer is used to view simulation results. The section on Running Simulation & Viewing Results has information on using [ResultsViewer](../../next_steps/running_your_simulation/#using-resultsviewer).

## Quick Start Guide to OpenStudio Modeling Tools
The [OpenStudio Quick Start Guide (PDF)](img/pdfs/openstudio_interface_quickstart.pdf) provides an introduction to the interface for the Plug-in and the OpenStudio application. It also provides guidance on the basic workflow. Read the [Introductory Tutorial](#introductory-tutorial) below to get started.

## Quick Start Guide to the ParametricAnalysisTool (PAT)
The [ParametricAnalysisTool Quick Start Guide (PDF)](img/pdfs/PAT-Quick_Start_Guide.pdf) and the [ParametricAnalysisTool section](../comparative_analysis/parametric_studies.md) provide an introduction to the interface and workflow for creating multiple design alternatives from a seed model.

## Introductory Tutorial
The tutorial below was created before the grid view was added to the Space Types and Thermal Zones tabs. Grid view allows you to view and edit more than one space type or thermal zone at a time. Go to the [OpenStudio Application Interface](../next_steps/openstudio_application_interface.md) to learn more about grid view.

### SketchUp Plug-in - Building Envelope
For additional information on the SketchUp Plug-in interface, go to the [SketchUp Plug-in Interface](../next_steps/sketchup_plugin_interface.md) section.

<iframe width="640" height="360" src="http://www.youtube.com/embed/wzzY_W2WELo" allowfullscreen></iframe>

*Above: This video shows you how to choose a template and create your building envelope. It uses the OpenStudio SketchUp Plug-in.*

### SketchUp Plug-in - Space Types and Thermal Zones
<iframe width="640" height="360" src="http://www.youtube.com/embed/8LTexVna_vw" allowfullscreen></iframe>

*Above: This video shows you how to assign space types, thermal zones, and thermostats to the spaces in your model. It uses the OpenStudio SketchUp Plug-in.*

### Site, Facility, and Basic Run
<iframe width="640" height="360" src="http://www.youtube.com/embed/tgeepiBltJI" allowfullscreen></iframe>

*Above: This video goes into the OpenStudio application, adds weather data, shows the outline view in the facility tab, and runs a simulation with ideal air loads.*

### Space Types, Internal Loads, and Schedules
<iframe width="640" height="360" src="http://www.youtube.com/embed/PCcxruCaZO0" allowfullscreen></iframe>

*Above: This video demonstrates how you can inspect, alter, and apply resource objects in OpenStudio.*

### Constructions, Materials, and the Building Component Library (BCL)
<iframe width="640" height="360" src="http://www.youtube.com/embed/8KdVvBds_30" allowfullscreen></iframe>

*Above: This video shows you how to obtain construction and material objects from the Building Component Library and load them into your current model.*

### HVAC - Zone Equipment, Air Loops, and Plant Loops
<iframe width="640" height="360" src="http://www.youtube.com/embed/DKLnZaNoRX0" allowfullscreen></iframe>

*Above: This video shows you how to add HVAC systems. It introduces the variable and scripts tabs and runs a simulation with the resulting model.*

### Service Hot Water
<iframe width="640" height="360" src="http://www.youtube.com/embed/jUJhi6YH51E" allowfullscreen></iframe>

*Above: This video shows you how create models using service hot water. This includes water heaters, water use connections, water use equipment, and other associated objects.*

<!--
## Introductory Tutorial
* Choosing a Template
* Modeling the Building Envelope
* Assigning Building Activity
* Assigning Thermal Zones
* Assign Thermostats
* Saving the OSM model from the SketchUp Plugin
* Moving from the Plugin to the OpenStudio Application
* Adding Weather and Design Day Files
* Adding a Mechanical System
* Running a Simulation
* Viewing Simulation Results
-->
