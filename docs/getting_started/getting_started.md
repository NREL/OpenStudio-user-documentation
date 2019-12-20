<h1>Installation</h1>
This page walks you through installing OpenStudio and the basic workflow.

## Installation Instructions
OpenStudio is supported on 64-bit versions of Windows 7 &ndash; Windows 10, OS X 10.9 &ndash; 10.10, and Ubuntu 16.04.
OpenStudio supports the latest EnergyPlus release which is bundled with the OpenStudio installer. The [version compatibility matrix](https://github.com/NREL/OpenStudio/wiki/OpenStudio-Version-Compatibility-Matrix) lists specific versions of EnergyPlus and other dependencies for each version of OpenStudio.
###Installation Steps
__Download and install OpenStudio__

1. Login to the [OpenStudio website](https://www.openstudio.net/downloads). Create an account if you don't have one. EnergyPlus and OpenStudio now share a password.
2. Click "Downloads" at the top of the page.
3. Choose the installer that matches your operating system. The OpenStudio package contains the following components:
    - EnergyPlus
    - Ruby API
    - C# API
    - Command Line Interface
    - Radiance

__Optional - Command Line Installation__

The OpenStudio installer is built using the [Qt Installer Framework](https://doc.qt.io/qtinstallerframework/index.html).  Installation of OpenStudio packages can be automated by passing the path to a customizable script to the installer using the `--script` argument:

```
OpenStudio-3.0.0-pre1+5cfb36386f-Windows.exe --script install.qs
```

An [example installation script](https://raw.githubusercontent.com/NREL/OpenStudio/develop/install.qs) can be modified to support custom installation.

__Optional - Install PAT__

Instructions coming soon.

__Optional - Setup a Building Component Library (BCL) Account__

BCL content can now be accessed from within the OpenStudio SketchUp Plug-in and from the standalone OpenStudio application. To take advantage of this integration, you will need to follow the steps outlined here to request a BCL key.

1. Login to [Building Component Library (BCL)](https://bcl.nrel.gov/). Create an account if you don't have one. Follow the instructions from the email sent to you upon registration and then login.
2. Click on the `My Dashboard` near the top right of the website.
3. Copy the text after `API v1.1 key`: then paste the key into the SketchUp Plug-in, the OpenStudio application, or the Parametric Analysis Tool (PAT). __You only need to configure the key in one place and it will be used globally throughout the OpenStudio tools.__ Additionally, this key will be maintained when you install updates to OpenStudio.

Enter the key through the OpenStudio SketchUp Plug-in under the menu `Plugins->OpenStudio User Scripts->Building Component Library->Setup BCL Key` and click `OK`. __Or__ register the key through the OpenStudio Application under the menu `Components & Measures->Find Components`. If a key is not already registered, it will prompt you for one.

![Key request dialog](img/bcl_key_request.png)

__Optional - Install Ruby__
If you plan to use the OpenStudio Ruby bindings via command prompt, you must install Ruby. Check the [version compatibility matrix](https://github.com/NREL/OpenStudio/wiki/OpenStudio-Version-Compatibility-Matrix) to see which version of Ruby is compatible.

1. Download the [Ruby](http://rubyinstaller.org/downloads/) installer.  If you have the Windows (x64) version of OpenStudio (Help>About>Compiler shows Visual Studio 12 2013 Win64), you'll need the x64 Ruby installer.
2. Add `C:\ruby-2.2.4-x64-mingw32\bin` (or wherever you installed Ruby) to the PATH environment variable. [Detailed instructions](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx).
3. Create a text file with the following text inside (modify `C:\openstudio-2.3.0` based on where your version of OpenStudio is installed):

    ```
    require 'C:\openstudio-2.3.0\Ruby\openstudio.rb'
    ```

4. Save the file as `openstudio.rb` to `C:\ruby-2.2.4-x64-mingw32\lib\ruby\site_ruby\openstudio.rb` (or wherever you installed Ruby).
5. Test your installation by opening a command prompt and typing: `irb` ENTER.  Then, type `RUBY_VERSION` ENTER.  Ensure that the Ruby correct version is shown.  Then, type `require 'openstudio'` ENTER.  If you see `=> true`, it's working.

## Workflow Overview
After installing OpenStudio you will have the SketchUp Plug-in, OpenStudio Application, Parametric Analysis Tool (PAT) and ResultsViewer. The typical OpenStudio workflow is shown in the diagram below.

[![Workflow Diagram](img/workflow_diagram.png "Click to view")](img/workflow_diagram.png)

*About: Click on the diagram above to view a larger version.*

ResultsViewer is used to view simulation results. The section on Running Simulation & Viewing Results has information on using [ResultsViewer](../../tutorials/running_your_simulation/#using-resultsviewer).

## Quick Start Guide to OpenStudio Modeling Tools
The [OpenStudio Quick Start Guide (PDF)](img/pdfs/openstudio_interface_quickstart.pdf) provides an introduction to the interface for the Plug-in and the OpenStudio application. It also provides guidance on the basic workflow. Read the [Introductory Tutorial](#introductory-tutorial) below to get started.

## Quick Start Guide to the Parametric Analysis Tool (PAT)
The [Parametric Analysis Tool Quick Start Guide (PDF)](img/pdfs/PAT-Quick_Start_Guide.pdf) and the [Parametric Analysis Tool Interface Guide](../reference/parametric_studies.md) provide an introduction to the interface and workflow for creating multiple design alternatives from a seed model.

