<h1>Interactive Jupyter NoteBook Tutorials</h1>

The [OpenStudio Jupyter Notebooks](https://github.com/NREL/docker-openstudio-jupyter) is a public GitHub repository with a collection of notebooks to help users get started using OpenStudio interactively. These examples include running OpenStudio Workflow (OSW), OpenStudio Analysis jsons (OSA), and URBANopt workflows.

Below is a sample notebook that creates a baseline model. While you can copy and paste the code into your own terminal, running the jupyter notebook allows you to follow along and run the commands yourself to get a better understanding of the common API calls used when running an openstudio workflow.

Please see the instructions in the repo for details on installing jupyter and related dependencies. 



### BaselineModel NoteBook Example

To begin, load the 'openstudio' Ruby bindings to the SDK as well as 'fileutils' for basic file/directory manipulation.

```ruby 
require 'fileutils'
require 'openstudio'
```

Create a folder named Baseline in the current working directory, and ensures that it only gets created if it does not already exist. The FileUtils.mkdir_p method creates the directory, and the Dir.exist? method checks for its existence before creating it.


```ruby
project_dir = 'Baseline'
#create project folder
FileUtils.mkdir_p("#{project_dir}") unless Dir.exist?("#{project_dir}")
```

Change the working directory to the Baseline folder to make it the current directory for file operations. The Dir.chdir method sets the current working directory to the specified folder. This is useful when you want to perform file operations in a specific directory, rather than the current working directory.


```ruby
#change working directory
Dir.chdir "#{project_dir}"
```

Create an example model using OpenStudio::Model.exampleModel and saves it in the "seeds" directory as an OSM file. The directory is created with FileUtils.mkdir_p if it doesn't exist. The file path is created with OpenStudio::Path.new and the model is saved with model.save, with the second argument 'true' meaning it can overwrite an existing file.


```ruby

# Create the Example Model
model = OpenStudio::Model.exampleModel()

#create directory for the seed model
FileUtils.mkdir_p("seeds") unless Dir.exist?("seeds")
# Save the model to an OSM file
osm_path = OpenStudio::Path.new(File.expand_path("seeds/example_model.osm"))
model.save(osm_path, true)

```
Download the weather file 'USA_CO_Golden-NREL.724666_TMY3.epw' and save it in the "weather" directory, checking first if the file already exists locally to avoid redownloading it.

```ruby
#get weather file
require 'open-uri'

# URL of the file to download
url = 'https://github.com/NREL/OpenStudio/raw/develop/resources/utilities/Filetypes/'

# Local file name
weather_file_name = 'USA_CO_Golden-NREL.724666_TMY3.epw'
weather_file_path = "weather/" + weather_file_name

#create directory for the weather file
FileUtils.mkdir_p("weather") unless Dir.exist?("weather")

if !File.exist?(weather_file_path)
    puts "Download the file #{weather_file_name}"
    URI.open(url + weather_file_name) do |file|
      File.write(weather_file_path, file.read)
    end
else
    puts 'weather file exists locally'
end

```

Set a weather file in the OSM model.

Load the weather file into OpenStudio using the OpenStudio::EpwFile.load method and passing the file path, which is constructed using OpenStudio::Path.new and File.expand_path to obtain the absolute path of the weather file.

The weather file is then set in the model using the OpenStudio::Model::WeatherFile::setWeatherFile method, which takes the model and the weather file as arguments. The code then retrieves the weather file using model.getWeatherFile and assigns it to a variable weatherFile.

Finally, the code validates the weather file by checking three properties: the checksum, the country, and the state/province/region. The checksum property is compared to the string 'BDF687C1' using puts weatherFile.checksum.get == 'BDF687C1', the country property is compared to the string 'USA' using puts weatherFile.country == 'USA', and the stateProvinceRegion property is compared to the string 'CO' using puts weatherFile.stateProvinceRegion == 'CO'.

In summary, the code sets a weather file in the OSM model, retrieves it, and validates it by checking three of its properties.


```ruby
#set the weather file in the OSM
#use absolute path
epw_file = OpenStudio::EpwFile.load(OpenStudio::Path.new(File.expand_path(weather_file_path)))
OpenStudio::Model::WeatherFile::setWeatherFile(model, epw_file.get)
weatherFile = model.getWeatherFile
# validate the weather file
puts weatherFile.checksum.get == 'BDF687C1'
puts weatherFile.country == 'USA'
puts weatherFile.stateProvinceRegion == 'CO'

```

Use the 'Open3' library to make a system call to the OpenStudio command-line interface (CLI) and check its version. The CLI path is stored in the 'cli' variable and the system call is made using the 'capture3' method of the 'Open3' module, which captures the standard output, standard error, and exit status of the system command. The result of the system call is checked using the 'status.success?' method, and if it is successful, the standard output is printed to the console. If it fails, the standard error is printed instead.


```ruby
require 'open3'

#get path to OpenStudio CLI
cli = OpenStudio.getOpenStudioCLI.to_s

# Make a system call to get version
stdout, stderr, status = Open3.capture3("#{cli} --version")

# Check the result
if status.success?
  puts "Command executed successfully"
  puts stdout
else
  puts "Command failed"
  puts stderr
end
```

Require the "openstudio-calibration" and "openstudio-common-measures" ruby gems. These gems contain pre-written scripts (OpenStudio Measures) that can make programmatic changes to an OpenStudio model, that we want to use in our project. Use the "Gem::Specification" method or the "Gem.find_files" method to find the local path to the /lib folder of the gem which is where the Measures are located. These paths are then stored in the variables "calibration_measures_dir" and "common_measures_dir".


```ruby
require 'openstudio-calibration'
require 'openstudio-common-measures'

#find path to the Measures
puts Pathname.new(Gem.find_files('openstudio-common-measures.rb').first).dirname
# -or-
#find path to Measures using gem::spec
common_measures_dir = Gem::Specification.find_by_name("openstudio-common-measures").gem_dir
calibration_measures_dir = Gem::Specification.find_by_name("openstudio-calibration").gem_dir
```

Copy the OpenStudio Measures from the openstudio-common-measures and openstudio-calibration gems into a local project directory called "measures". The purpose of this is to make these scripts available for use in the current project. The measures copied include "openstudio_results", "AddMonthlyJSONUtilityData", "CalibrationReportsEnhanced", and "GeneralCalibrationMeasurePercentChange".


```ruby
#make measure directories for the project

FileUtils.mkdir_p("measures") unless Dir.exist?("measures")

#copy measure from gem to local project directory
FileUtils.cp_r("#{common_measures_dir}/lib/measures/openstudio_results", "measures")
FileUtils.cp_r("#{calibration_measures_dir}/lib/measures/AddMonthlyJSONUtilityData", "measures")
FileUtils.cp_r("#{calibration_measures_dir}/lib/measures/CalibrationReportsEnhanced", "measures")
FileUtils.cp_r("#{calibration_measures_dir}/lib/measures/GeneralCalibrationMeasurePercentChange", "measures")
```

Create a project directory named "data" if it doesn't already exist, and then copies the monthly metered data in the "Data" directory located outside of the project folder to the newly created "data" folder within the project folder. The data that is being copied is in JSON format.


```ruby
#make directory for the calibration data
FileUtils.mkdir_p("data") unless Dir.exist?("data")

#copy JSON data to local project directory
FileUtils.cp_r("../Data/.", "data")
```



The OpenStudio Workflow (OSW) format is a JSON file format that describes a simulation workflow. In an OpenStudio Workflow, a seed OpenStudio Model is loaded. OpenStudio Model Measures are applied to the seed model. After these measures, the OpenStudio Model is translated to EnergyPlus IDF format. Once in EnergyPlus IDF format, OpenStudio EnergyPlus Measures are applied. After these measures, the EnergyPlus simulation is executed. Once the EnergyPlus simulation is complete, OpenStudio Reporting Measures are applied which generate reports. An error at any point in the workflow will halt the workflow. Once the workflow is completed (successfully or unsuccessfully) an output OSW file is written which contains output related to running the workflow.

create a WorkflowJSON object which will be turned into our OSW json file.


```ruby
# Create a new OSW
osw = OpenStudio::WorkflowJSON.new

```


Each step listed in the OSW file describes an OpenStudio Measure to apply. Measures are applied in order and must progress from OpenStudio Model Measures to OpenStudio EnergyPlus Measures to OpenStudio Reporting Measures. Each step lists a measure_dir_name which is the directory name of an OpenStudio Measure to apply. Measures are found at run time according to logic in WorkflowJSON::findMeasure. Each step specifies arguments to be passed to the measure, the measure argument's name is the key and the value to pass is the measure. Optional arguments may be ommitted, default values will be used in this case. The value passed to choice arguments may be either a valid choice value or a valid choice value display name.

Set up two Model measure steps to be run on our OpenStudio model. The first measure step is to add the electricity bill data from an external JSON file (electric.json) to the OpenStudio model, and the second measure step is to add the gas bill data from another JSON file (natural_gas.json) to the model. The arguments to these measure steps set the details of the data to be added, such as the fuel type, consumption unit, data key name, start and end dates, etc. The measure steps are then set as model measure steps in the OpenStudio Workflow (OSW) object.

The AddMonthlyJSONUtilityData Measure populates a UtilityBill object in the OpenStudio Model using external JSON data.  The argument called 'json' is the file path, relative to the Measure at runtime, to the json data.  We have previously copied those jsons to the /data project folder.  At runtime there are two case to consider.  The first is if this run is taking place on an OS-Server or (OSAF) instance, where the project data is zipped up into an OSA.zip file and posted to the OS-Server Web node.  In this case, the relative path to the data would be:  

**on the server:** '../../../lib/calibration_data/electric_json.json'

Since we are running locally using the OpenStudio CLI, the path from the runtime copy of the Measure to the data is:       

**CLI run:** '../../../data/electric.json'

And that is what we will set the argument 'json' to.  

In the first application of the Measure, we want to remove any exisitng UtilityBill objects in the model, so we set 'remove_existing_data' to True. We also want to set the Run Period object in the model to the Start and End dates that we have specified in the Measure. Add that MeasureStep to the measure_step array.

In the second application of the Measure, we do not want to remove the existing UtilityBill object we previously setup, so that argument is now False.  The Run Period object is also already setup, so there is no need to set it since its default value is False. Add that MeasureStep to the measure_step array.

Finally, add the model measure steps to the OSW (OpenStudio Workflow) object. The measure type is defined as a "ModelMeasure" and the measure steps are passed as arguments to the setMeasureSteps method of the OSW object.


```ruby
# Define the model measure steps
measure_steps = []

#add Utility Bill object to model from external JSON file
os_results = OpenStudio::MeasureStep.new("measures/AddMonthlyJSONUtilityData")
os_results.setArgument("json","../../../data/electric.json")
os_results.setArgument("variable_name","Electricity Bill")
os_results.setArgument("fuel_type","Electricity")
os_results.setArgument("consumption_unit","kWh")
os_results.setArgument("data_key_name","tot_kwh")
os_results.setArgument("start_date","2013-01-1")
os_results.setArgument("end_date","2013-12-31")
os_results.setArgument("remove_existing_data",TRUE)
os_results.setArgument("set_runperiod",TRUE)
measure_steps << os_results

os_results = OpenStudio::MeasureStep.new("measures/AddMonthlyJSONUtilityData")
os_results.setArgument("json","../../../data/natural_gas.json")
os_results.setArgument("variable_name","Gas Bill")
os_results.setArgument("fuel_type","Gas")
os_results.setArgument("consumption_unit","therms")
os_results.setArgument("data_key_name","tot_therms")
os_results.setArgument("start_date","2013-01-1")
os_results.setArgument("end_date","2013-12-31")
os_results.setArgument("remove_existing_data",FALSE)
#os_results.setArgument("set_runperiod",TRUE)
measure_steps << os_results

# Add the measure steps to the OSW
measure_type = OpenStudio::MeasureType.new("ModelMeasure")
osw.setMeasureSteps(measure_type, measure_steps)
```

Add two reporting measures to be run as part of the OpenStudio Workflow (OSW): "measures/openstudio_results" and "measures/CalibrationReportsEnhanced". These reporting measures are added to the array reporting_steps and then set in the OSW object osw by creating a new MeasureType object with the type "ReportingMeasure" and calling the setMeasureSteps method on osw with this MeasureType object and the reporting_steps array.


```ruby
# Define the reporting measure steps
reporting_steps = []

#add openstudio_results to the reporting_steps array
os_results = OpenStudio::MeasureStep.new("measures/openstudio_results")
reporting_steps << os_results

os_results = OpenStudio::MeasureStep.new("measures/CalibrationReportsEnhanced")
reporting_steps << os_results

# Set the measure steps in the OSW
measure_type = OpenStudio::MeasureType.new("ReportingMeasure")
osw.setMeasureSteps(measure_type, reporting_steps)
```


Add the example_model OSM we generated earlier as the 'seed' model and set the weatherfile in the OSW.
Also, save the OSW as 'baseline_model.osw' by creating a full, absolute path to the file name and use the .saveAs() method.


```ruby
#add seed / weatherfile to OSW
osw.setSeedFile(osm_path)
osw.setWeatherFile(weather_file_path)
#save file locally
osw_path = OpenStudio::Path.new(File.expand_path("baseline_model.osw"))
osw.saveAs(osw_path)
```

Since this is in Ruby and the CLI is an executable, to run the workflow using the CLI, we will use the Open3.capture3 method to make a System Call to the CLI, which captures the standard output, standard error, and status code of the CLI command. The CLI command runs the workflow, specifying the workflow file path, and the --debug and --workflow options are passed to the CLI. Finally, the status code of the CLI command is stored in the status variable.


```ruby
#Run the workflow
stdout, stderr, status = Open3.capture3("#{cli} run --debug --workflow #{osw_path}")
status
```


To view the results, set the file path to an HTML report generated by the "CalibrationReportsEnhanced" measure and display the contents of the file using IRuby's display method. The argument passed to the display method is the content of the file read using Ruby's File.read method, and the mime type is specified as 'text/html' to indicate that the contents are HTML. This code assumes that the file exists and will raise an error if it cannot be found or read.


```ruby
file_path = File.expand_path(Dir.pwd + '/run/003_measures/CalibrationReportsEnhanced/report.html')

IRuby.display File.read(file_path), mime: 'text/html'
```

Or launch in an external browser like chrome, etc


```ruby
Open3.popen3("start chrome.exe #{file_path}")
```



