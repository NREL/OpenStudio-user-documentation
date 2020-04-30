<h1>Installation</h1>
This page walks you through installing OpenStudio and the basic workflow.

## Installation Instructions

OpenStudio SDK is supported on 64-bit versions of Windows 7 &ndash; Windows 10, OS X 10.12 &ndash; 10.14, and Ubuntu 18.04.
OpenStudio SDK supports the latest EnergyPlus release which is bundled with the OpenStudio SDK installer. The [version compatibility matrix](https://github.com/NREL/OpenStudio/wiki/OpenStudio-Version-Compatibility-Matrix) lists specific versions of EnergyPlus and other dependencies for each version of OpenStudio SDK.

### Installation Steps

__Download and install OpenStudio SDK__

1. Login to the [OpenStudio SDK website](https://www.openstudio.net/downloads). Create an account if you don't have one. EnergyPlus and OpenStudio SDK now share a password.
2. Click "Downloads" at the top of the page.
3. Choose the installer that matches your operating system. The OpenStudio SDK package contains the following components:
    - EnergyPlus
    - Ruby API
    - C# API
    - Command Line Interface
    - Radiance

__Optional - Command Line Installation__

The OpenStudio SDK installer is built using the [Qt Installer Framework](https://doc.qt.io/qtinstallerframework/index.html).  Installation of OpenStudio SDK packages can be automated by passing the path to a customizable script to the installer using the `--script` argument:

```
OpenStudio-3.0.0-pre1+5cfb36386f-Windows.exe --script install.qs
```

An [example installation script](https://raw.githubusercontent.com/NREL/OpenStudio/develop/install.qs) can be modified to support custom installation.

__Optional - Install PAT__

Instructions coming soon.

__Optional - Setup a Building Component Library (BCL) Account__

The BCL contains many useful measures that can be incorporated into OpenStudio SDK workflows or Parametric Analsysis Tool (PAT) projects. To access the content you will need to create an account:

- Navigate to [Building Component Library (BCL)](https://bcl.nrel.gov/). Create an account if you don't have one. Follow the instructions from the email sent to you upon registration and then login.

BCL content can also be accessed from within PAT. To take advantage of this integration, you will need to follow the steps outlined here to request a BCL key.

1. Login to [Building Component Library (BCL)](https://bcl.nrel.gov/).
2. Click on the `My Dashboard` near the top right of the website.
3. Copy the text after `API v1.1 key`: then paste the key into the PAT. __You only need to configure the key in one place and it will be used globally throughout the OpenStudio SDK tools.__ Additionally, this key will be maintained when you install updates to OpenStudio SDK.

__Optional - Install Ruby__
If you plan to use the OpenStudio SDK Ruby bindings via command prompt, you must install Ruby. Check the [version compatibility matrix](https://github.com/NREL/OpenStudio/wiki/OpenStudio-Version-Compatibility-Matrix) to see which version of Ruby is compatible.

1. Download the [Ruby](http://rubyinstaller.org/downloads/) installer.  If you have the Windows (x64) version of OpenStudio SDK (Help>About>Compiler shows Visual Studio 12 2013 Win64), you'll need the x64 Ruby installer.
2. Add `C:\ruby-2.5.5-x64-mingw32\bin` (or wherever you installed Ruby) to the PATH environment variable. [Detailed instructions](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx).
3. Create a text file with the following text inside (modify `C:\openstudio-3.0.0` based on where your version of OpenStudio SDK is installed):

    ```
    require 'C:\openstudio-3.0.0\Ruby\openstudio.rb'
    ```

4. Save the file as `openstudio.rb` to `C:\ruby-2.5.5-x64-mingw32\lib\ruby\site_ruby\openstudio.rb` (or wherever you installed Ruby).
5. Test your installation by opening a command prompt and typing: `irb` ENTER.  Then, type `RUBY_VERSION` ENTER.  Ensure that the Ruby correct version is shown.  Then, type `require 'openstudio'` ENTER.  If you see `=> true`, it's working.

## Quick Start Guide to the Parametric Analysis Tool (PAT)

The [Parametric Analysis Tool Quick Start Guide (PDF)](img/pdfs/PAT-Quick_Start_Guide.pdf) and the [Parametric Analysis Tool Interface Guide](../reference/parametric_analysis_tool_2.md) provide an introduction to the interface and workflow for creating multiple design alternatives from a seed model.
