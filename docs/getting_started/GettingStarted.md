# Installation and Introductory Tutorial
## Installation Instructions
OpenStudio is supported on Windows 7 – 8.1, OS X 10.8 – 10.9, and Ubuntu 12.04.
<ol>
<li>[Download and install EnergyPlus 8.1.] [Download EnergyPlus]
[Download EnergyPlus]: http://apps1.eere.energy.gov/buildings/energyplus/
<ul>
<li> Create an EnergyPlus account, if you don't have one, and then login.</li>
<li> After you log in you can click the link to access the page to "Download Older Versions of Energy Plus". Choose the appropriate version of EnergyPlus 8.1 for your computer.</li>
<li> Download and follow the instructions. OpenStudio will work with 32 or 64bit EnergyPlus installers.</li>
</ul>
<li>The OpenStudio SketchUp Plug-in requires [SketchUp 8.0 or SketchUp 2013][SketchUp Download] (not available for Linux).</li>
The OpenStudio SketchUp Plug-in is not yet compatible with SketchUp 2014. Create an OpenStudio account, then download and install OpenStudio.
[SketchUp Download]: http://www.sketchup.com/download/all
</li>
<li>Setup a [Building Component Library (BCL)][BCL] account to access online building components and measures.
View instructions on how to setup your account and configure the key in the "Connecting with the Building Component Library" section below.
[BCL]: http://bcl.nrel.gov
</li>
</ol>
** Optional Installations **
<p>For Radiance integration, [download and install Radiance][Radiance].Learn more about using Radiance in the "Creating Your Model" section.</p>
[Radiance]: https://github.com/NREL/Radiance
<p>If you plan to use the OpenStudio SDK Ruby bindings via command prompt on Windows, download and extract ruby.zip to C:\Ruby (or other desired location), and add C:\Ruby\bin to the PATH environment variable.</p>
## Connecting with the Building Component Library
BCL content can now be accessed from within the OpenStudio SketchUp Plug-in and from the standalone OpenStudio application. To take advantage of this integration, you will need to follow the steps outlined here to request a BCL key.


1. If you already have a BCL account, log in and go to step 3. If you do not already have a BCL account, go to [register at BCL](https://bcl.nrel.gov/user/register) to create a new account.  
2. After you click "Create new account," you are taken back to the BCL home page. Follow the instructions from the email sent to you upon registration and then login.
3. Click on the "My Dashboard" near the top right of the website.
4. Copy the text after __"APIv1.1 key:"__ then paste the key into the SketchUp Plug-in, the OpenStudio application, or the Parametric Analysis Tool (PAT). __You only need to configure the key in one place and it will be used globally throughout the OpenStudio tools.__ Additionally, this key will be maintained when you install updates to OpenStudio. Specific application instructions are below.

![Key Request](../../img/bcl_key_request.png "Key Dialog")

__Enter the Key Through the OpenStudio SketchUp Plug-in__ under the menu "Plugins/OpenStudio User Scripts/Building Component Library/Setup BCL Key" enter your key, and click "OK."

__Or__

__Register the Key Through the OpenStudio Application__ open the menu "Components & Measures/Find Components" and if a key is not already registered, it will prompt you for one. 

## Workflow Overview
After installing OpenStudio you will have the SketchUp Plug-in, OpenStudio Application, ParametricAnalysisTool (PAT) and ResultsViewer. The typical OpenStudio workflow is shown in the diagram below. 

 <a href="../../img/workflow_diagram.png" target="_blank">
<img src="../../img/workflow_diagram.png" alt="Resized JPEG graphic" title="Click to view larger image" border="2" width="750" height="" hspace="10" /></a>

*About: Click on the diagram above to view a larger version.*

Results view is used to view simulation results. The section on Running Simulation & Viewing Results has information on using [ResultsViewer.](../../next_steps/RunningYourSimulation/#using-resultsviewer)

## Quick Start Guide to OpenStudio Modeling Tools
* This [OpenStudio Quick Start Guide (PDF)](../../img/pdfs/openstudio_interface_quickstart.pdf) provides an introduction to the interface for the Plug-in and the OpenStudio application. It also provides guidance on the basic workflow. Checkout the [Introductory Tutorial](#introductory-tutorial) below to get started.

## Quick Start Guide to the ParametricAnalysisTool (PAT)
* This [ParametricAnalysisTool Quick Start Guide (PDF)](../../img/pdfs/PAT-Quick_Start_Guide.pdf) and the [ParametricAnalysisTool section](../comparative_analysis/ParametricStudies.md) provide an introduction to the interface and workflow for creating multiple design alternatives from a seed model. 

## Introductory Tutorial

The tutorial below was created before the grid view was added to the Space Types and Thermal Zones tabs. Grid view allows you to view and edit more than one space type or thermal zone at a time. Go to the [OpenStudio Application Interface](../next_steps/openstudio_application_interface.md) to learn more about grid view.   

### SketchUp Plug-in—Building Envelope
For additional information on the SketchUp Plug-in interface, go to the [SketchUp Plug-in Interface](../next_steps/sketchup_plugin_interface.md) section.
 
<iframe width="640" height="360" src="http://www.youtube.com/embed/wzzY_W2WELo?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>
    
*Above: This video shows you how to choose a template and create your building envelope. It uses the OpenStudio SketchUp Plug-in.*

### SketchUp Plug-in—Space Types and Thermal Zones

<iframe width="640" height="360" src="http://www.youtube.com/embed/8LTexVna_vw?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>

*Above: This video shows you how to assign space types, thermal zones, and thermostats to the spaces in your model. It uses the OpenStudio SketchUp Plug-in.*

### Site, Facility, and Basic Run

<iframe width="640" height="360" src="http://www.youtube.com/embed/tgeepiBltJI?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>

*Above: This video goes into the OpenStudio application, adds weather data, shows the outline view in the facility tab, and runs a simulation with ideal air loads.*

### Space Types, Internal Loads, and Schedules

<iframe width="640" height="360" src="http://www.youtube.com/embed/PCcxruCaZO0?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>

*Above: This video demonstrates how you can inspect, alter, and apply resource objects in OpenStudio.*

### Constructions, Materials, and the Building Component Library (BCL)

<iframe width="640" height="360" src="http://www.youtube.com/embed/8KdVvBds_30?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>

*Above: This video shows you how to obtain construction and material objects from the Building Component Library and load them into your current model.*

### HVAC—Zone Equipment, Air Loops, and Plant Loops

<iframe width="640" height="360" src="http://www.youtube.com/embed/DKLnZaNoRX0?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>

*Above: This video shows you how to add HVAC systems. It introduces the variable and scripts tabs and runs a simulation with the resulting model.*

### Service Hot Water

<iframe width="640" height="360" src="http://www.youtube.com/embed/jUJhi6YH51E?rel=0&start=&end=&autoplay=0" frameborder="0" allowfullscreen></iframe>

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
## Software License Description and Terms
* OpenStudio is licensed under the Lesser General Public License (LGPL), and is free for use and development. Visit the [LGPL license web page](https://raw.githubusercontent.com/NREL/OpenStudio/develop/license.txt) for details on the software development kit terms of use.

_______________________


<p class="text-center"><small>OpenStudio is developed in collaboration by NREL, ANL, LBNL, ORNL, and PNNL.</small></p> 

<p class="text-center"><small>NREL is a National Laboratory of the U.S. Department of Energy, Office of Energy Efficiency and Renewable Energy, operated by the Alliance for Sustainable Energy, LLC.</small></p>
 
  
<p class="text-center"><small> <a href="http://openstudiodev.prod.acquia-sites.com/">Return to OpenStudio Home</a></p>  

