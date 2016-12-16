<h1>OpenStudio Command Line Interface</h1>

The OpenStudio Command Line Interface (CLI) is a self-contained executable which includes everything needed to apply OpenStudio Measures to an OpenStudio Model and run an EnergyPlus simulation.  The CLI is only avaiable in OpenStudio version 2.0 and higher. The CLI contains a full OpenStudio Ruby environment, the list of Ruby Gems available in each version of OpenStudio can be found [here](https://github.com/NREL/OpenStudio/wiki/OpenStudio-Version-Compatibility-Matrix).  

This document provides an overview of the most important features of the CLI, it is not meant to be an exhaustive reference.  For an exhaustive list of features available in the CLI please refer to the command line output of the `--help` command.  For a complete list of the properties available in the OSW file format please refer to the [OSW JSON schema](https://raw.githubusercontent.com/NREL/OpenStudio-workflow-gem/osw/spec/schema/osw_output.json).  For a complete description of the WorkflowJSON class please refer to the [documentation](https://github.com/NREL/OpenStudio/tree/develop/openstudiocore/src/utilities/filetypes/WorkflowJSON.hpp).  

# Command Overview

The CLI is executed by calling the OpenStudio executable from the command line with a set of command line arguments.  Calling the CLI with no arguments (such as when double-clicking the executable) causes the CLI to print a help message and then exit.  Several switches which control program behavior may be passed immediately following the OpenStudio executable.  Switches often have both a short form and a long form for convienence. Multiple program level switches may be combined.  Program level switches include:

The `-h` or `--help` switches print the help message:

```
openstudio.exe --include /path/to/add/ --include /another/path/to/add
```

The `-I` or `--include` switches can be used to add additional directories to the Ruby $LOAD_PATH (this switch may be used more than once):

```
openstudio.exe --include /path/to/add/ --include /another/path/to/add
```

The `--verbose` switch can be used to print additional information for debugging:

```
openstudio.exe --verbose
```

Program level switches (if any) are followed by a subcommand which directs the program to perform a particular function.  These subcommands are explained in further detail below.


# Measure Subcommand

The `measure` subcommand is used to query OpenStudio Measures on disk.  The following arguments may be passed to the `measure` subcommand. 

The `-h` switch prints help specific to the `measure` subcommand:

```
openstudio.exe measure -h
```

The `-t` or `--update_all` switches process all measures in a given directory and updates their measure.xml files if updates to their content are detected.  Information about the measures is printed to standard out in JSON format:

```
openstudio.exe measure --update_all /path/to/measures/
```

The `-u` or `--update` switches process a single measure in a given directory and updates its measure.xml file if updates to the content are detected. Information about the measure is printed to standard out in JSON format:

```
openstudio.exe measure --update /path/to/measure/
```

The `-a` or `--compute_arguments` switches process a single measure in a given directory and updates its measure.xml file if updates to the content are detected. Information about the measure, including model specific arguments, is printed to standard out in JSON format:

```
openstudio.exe measure --compute_arguments /path/to/model.osm /path/to/measure/
```

or for an EnergyPlus Measure:

```
openstudio.exe measure --compute_arguments /path/to/model.idf /path/to/measure/
```

# Run Subcommand
 
The `run` subcommand is used to load an OpenStudio Model, apply a series of OpenStudio Model Measures, translate to EnergyPlus IDF, apply a series of OpenStudio EnergyPlus Measures, run an EnergyPlus simulation on the resulting model, and finally apply a series of OpenStudio Reporting Measures. The OpenStudio Workflow (OSW) file format is used to describe which OpenStudio Measures to apply to the model and what arguments to pass to each measure.  The OSW format is explained in the following section.

The `-h` switch prints help specific to the `run` subcommand:

```
openstudio.exe run -h
```

The `-w` or `--workflow` switches run the complete simulation workflow as described in an OSW file:

```
openstudio.exe measure --workflow /path/to/workflow.osw
```

The `--debug` switch can be used to include additional outputs for debugging failing workflows and does not clean up the run directory:

```
openstudio.exe measure --debug --workflow /path/to/workflow.osw
```

The `-m` or `--measures_only` switches run only the OpenStudio Model and EnergyPlus Measures but do not run the EnergyPlus simulation or OpenStudio Reporting Measures in an OSW file:

```
openstudio.exe measure --measures_only /path/to/workflow.osw
```

The `-p` or `--postprocess_only` switches do not run the OpenStudio Modelm EnergyPlus Measures, or EnergyPlus simulation in an OSW file.  Existing simulation results are loaded and only OpenStudio Reporting Measures are run, this is useful for generating new reports without re-running simulations:

```
openstudio.exe measure --postprocess_only /path/to/workflow.osw
```

# OSW Structure

The OpenStudio Workflow (OSW) format is a JSON file format that describes a simulation workflow.  In an OpenStudio Workflow, a seed OpenStudio Model is loaded.  OpenStudio Model Measures are applied to the seed model.  After these measures, the OpenStudio Model is translated to EnergyPlus IDF format.  Once in EnergyPlus IDF format, OpenStudio EnergyPlus Measures are applied.  After these measures, the EnergyPlus simulation is executed.  Once the EnergyPlus simulation is complete, OpenStudio Reporting Measures are applied which generate reports.  An error at any point in the workflow will halt the workflow.  Once the workflow is completed (successfully or unsuccessfully) an output OSW file is written which contains output related to running the workflow.

An example OSW project is included in the OpenStudio installer under './Examples/compact_osw'.

The OSW file format is described in JSON schema format [here](https://raw.githubusercontent.com/NREL/OpenStudio-workflow-gem/osw/spec/schema/osw_output.json).

The OpenStudio API includes the class [WorkflowJSON](https://github.com/NREL/OpenStudio/tree/develop/openstudiocore/src/utilities/filetypes/WorkflowJSON.hpp) which is able read, modify, and write the OSW file format.  The WorkflowJSON class also includes features for finding measures and files associated with a simulation workflow.

The WorkflowJSON associated with an OpenStudio Model can be accessed using `model.workflowJSON`.  The WorkflowJSON object can also be accessed from the OSRunner object within a measure using `runner.workflow`.  Within the context of a measure, the WorkflowJSON object can be used to find files and measures associated with the simulation.  It can also be used to tell which OpenStudio Measures will be run during the workflow, what arguments they will be passed, and capture output from previously run measures.  However, during the course of a simulation workflow the OSW associated with an OpenStudio Model or OSRunner cannot be altered.

An example OSW is shown below, the meaning of key terms is explained in more detail later in this section:

```json
{
  "seed_file": "baseline.osm",
  "weather_file": "USA_CO_Golden-NREL.724666_TMY3.epw",
  "steps": [
    {
      "measure_dir_name": "IncreaseWallRValue",
      "arguments": {}
    },
    {
      "measure_dir_name": "IncreaseRoofRValue",
      "arguments": {
        "r_value": 45
      }
    },
    {
      "measure_dir_name": "SetEplusInfiltration",
      "arguments": {
        "flowPerZoneFloorArea": 10.76
      }
    },
    {
      "measure_dir_name": "DencityReports",
      "arguments": {
        "output_format": "CSV"
      }
    }
  ]
}
```

## Seed File

The seed file is the file name of the OpenStudio Model to be loaded at the beginning of the simulation workflow.  The seed model may be empty or the memeber may be missing, in this case a newly constructed OpenStudio Model is passed to the first OpenStudio Model Measure.  The seed model is found using the logic documented for `WorkflowJSON::findFile`.

## Weather File

The weather file is the file name of the EnergyPlus Weather (EPW) file loaded at the beginning of the simulation workflow.  The weather file may be empty or the memeber may be missing.  The weather file is found using the logic documented for `WorkflowJSON::findFile`.  The following logic applies to the weather file during a simulation workflow:

1. If a weather file is specified in the OSW, that file replaces any weather file specified in the seed OpenStudio Model before measure processing begins.
2. During OpenStudio Model Measure processing, the weather file may be changed by altering the WeatherFile object in the OpenStudio Model.
3. On translation to EnergyPlus, the weather file referenced in the OSM is found using WorkflowJSON.findFile and copied to in.epw in the run directory.
EnergyPlus measures may change the weather file by copying files on top of in.epw.

## Workflow Steps

Each step listed in the OSW file describes an OpenStudio Measure to apply.  Measures are applied in order and must progress from OpenStudio Model Measures to OpenStudio EnergyPlus Measures to OpenStudio Reporting Measures.  Each step lists a `measure_dir_name` which is the directory name of an OpenStudio Measure to apply. Measures are found at run time according to logic in `WorkflowJSON::findMeasure`.  Each step specifies arguments to be passed to the measure, the measure argument's name is the key and the value to pass is the measure.  Optional arguments may be ommitted, default values will be used in this case.  The value passed to choice arguments may be either a valid choice value or a valid choice value display name.

# Environment Variables

The OpenStudio Command Line Interface can be configured with several environment variables.  In cases where a value can be configured with either a command line switch or an environment variable, the command line switch will take precedence.

The `ENERGYPLUS_EXE_PATH` environment variable can be used to configure the CLI to use a different version of the EnergyPlus engine than the one OpenStudio is installed with:

Windows
```
set ENERGYPLUS_EXE_PATH=/path/to/EnergyPlus.exe
```

Unix
```
export ENERGYPLUS_EXE_PATH=/path/to/energyplus
```

The `RUBYLIB` environment variable can be used to configure the CLI to require Ruby files from locations on the user's disk, locations passed using the `--include` take precedence over the path found in this environment variable:

Windows
```
set RUBYLIB=/home/git/project;/home/git/project/app/helpers
```

Unix
```
export RUBYLIB=/home/git/project:/home/git/project/app/helpers
```

The `GEM_HOME` environment variable can be used to configure the CLI to load gems from a location on the user's disk, the location passed using the `--gem_path` take precedence over the path found in this environment variable. *Loading external gems is not currently available in CLI*:

Windows
```
set GEM_HOME=/home/gems
```

Unix
```
export GEM_HOME=/home/gems
```
