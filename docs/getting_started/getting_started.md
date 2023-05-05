<h1>Installation</h1>
This page walks you through installing OpenStudio and the basic workflow.

## Installation Instructions

AsOpenStudio SDK is supported on 64-bit versions of Windows 7-11, macOS X 10.15+, 12.1+ arm64 and Ubuntu 20.04,22.04.
OpenStudio SDK supports the latest EnergyPlus release which is bundled with the OpenStudio SDK installer. The [version compatibility matrix](https://github.com/NREL/OpenStudio/wiki/OpenStudio-SDK-Version-Compatibility-Matrix) lists specific versions of EnergyPlus and other dependencies for each version of OpenStudio SDK.

### Installation Steps

__Download and install OpenStudio SDK__

1. Open a web browser to the [OpenStudio SDK GitHub Repository](https://github.com/nrel/openstudios/releases). 
2.  
2. Choose the installer under "Assets" that matches your operating system. The OpenStudio SDK package contains the following components:
    - EnergyPlus
    - Ruby API
    - Python API
    - C# API
    - Command Line Interface
    - Radiance

__Optional - Command Line Installation__

The OpenStudio SDK installer is built using the [Qt Installer Framework](https://doc.qt.io/qtinstallerframework/index.html).  Installation of OpenStudio SDK packages can be automated by passing the path to a customizable script to the installer using the `--script` argument:

```
OpenStudio-3.5.0+7b14ce1588-Windows.exe --script install.qs
```

An [example installation script](https://raw.githubusercontent.com/NREL/OpenStudio/develop/install.qs) can be modified to support custom installation.


__Legacy Support - Building Component Library (BCL) key__

The BCL contains many useful measures that can be incorporated into OpenStudio SDK workflows or Parametric Analsysis Tool (PAT) projects. You no longer need to create an account to access content, but certain apps may still ask you for a BCL key.

If you are prompted for a key, simply enter 32 Xs as shown below:

```
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```


__Optional - Install Ruby__
If you plan to use the OpenStudio SDK Ruby bindings via command prompt, you must install Ruby. Check the [version compatibility matrix](https://github.com/NREL/OpenStudio/wiki/OpenStudio-Version-Compatibility-Matrix) to see which version of Ruby is compatible.

1. Download the [Ruby](http://rubyinstaller.org/downloads/) installer.  If you have the Windows (x64) version of OpenStudio SDK (Help>About>Compiler shows Visual Studio 14 2017 Win64), you'll need the x64 Ruby installer.
2. Add `C:\ruby-2.7.2-x64-mingw32\bin` (or wherever you installed Ruby) to the PATH environment variable. [Detailed instructions](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx).
3. Create a text file with the following text inside (modify `C:\openstudio-3.5.0` based on where your version of OpenStudio SDK is installed):

    ```
    require 'C:\openstudio-3.6.0\Ruby\openstudio.rb'
    ```

4. Save the file as `openstudio.rb` to `C:\ruby-2.7.2-x64-mingw32\lib\ruby\site_ruby\openstudio.rb` (or wherever you installed Ruby).
5. Test your installation by opening a command prompt and typing: `irb` ENTER.  Then, type `RUBY_VERSION` ENTER.  Ensure that the Ruby correct version is shown.  Then, type `require 'openstudio'` ENTER.  If you see `=> true`, it's working.

## Quick Start Guide to the Parametric Analysis Tool (PAT)

The [Parametric Analysis Tool Quick Start Guide (PDF)](img/pdfs/PAT-Quick_Start_Guide.pdf) and the [Parametric Analysis Tool Interface Guide](../reference/parametric_analysis_tool_2.md) provide an introduction to the interface and workflow for creating multiple design alternatives from a seed model.
