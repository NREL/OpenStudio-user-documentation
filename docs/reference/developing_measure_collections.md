<h1>Developing Measure Collections</h1>
When writing a collection of measures meant to be used in conjunction with each other it's a good idea to develop an overall plan for the workflow. This page provides guidance on best practices to manage coordination between measures.

## How Will The Measures Be Used

Think about what you are trying to accomplish and how the measures will be used. This will greatly impact the design process. Below are some example uses cases for a measure collection

* Fully automated model generation from an empty seed model
* Taking any generic completed model as a seed and altering it through a set of guidelines such as the Advanced Energy Design Guides
* Running a collection of input diagnostics such as a collection of pre-flight measures

## Identify Result Requirements

* What should the resulting model look like. Can it be simple with power per area loads or do you need to model individual pieces of equipment?
* Is it being used in a controlled environment where you know what the seed models will look like, or is it meant for public consumption where it needs to gracefully handle any model or inputs thrown at it?
* What kinds of variables will you want to change?
* Is one person going to code all of these, or will a team be developing them?

## Outline the Workflow
Start with what the seed model looks like, and then move into what will be added or altered in the model. Think about how much modularity you want in your measures, there is a big sweet spot, but way too much or way too little modularity will make your work harder. Think about where you can use or adapt off the shelf measures vs. writing your own.

Here an a basic example workflow. Generally think about the order you would do this by hand. You wouldn't add the HVAC system before there are zones in the model.

* Seed model will be pre-loaded with weather file and spaces with stub space types assigned
* Based on stub space types add in real space types for a user selected standard
* Add in a construction set for the building based on a user selected standard and climate zone. May also allow user to pick the type of exterior wall (mass, steel frame, etc.).
* Rotate building
* Add fenestration and overhangs based on user specified targets (use multiple instances of the same measure with different input azimuths for each instance)
* Create thermal zones. Need to decide if one zone per space, or if space should be merged. Maybe define this and stories in the seed model?
* Add HVAC systems
* add service water heating
* add exterior lights
* add reporting measures

## Create Design Documents

Write a basic design document for each measure. It describes the general intent of the measure and how it will work. It should list descriptions, the arguments, and the log messages that will show up when the measure is run. It should also include an outline of the code from the run section of the measure. It can also include information on testing. You can use [this example google doc design document](https://docs.google.com/document/d/1TlFS-uvRTDkT26uU49sJGAyxhSCu6efo56X8nZMqe7I/edit#) for the "Hello World" measure as a starting point. If you place your design documents on a version control repository instead of using something like Google Documents, you may want to write as raw text files instead of Word documents for better version control.

## Writing the Measures
Once you have written the design documents and reviewed them as a collection to make sure they will function together correctly, you are ready to write the measures; or in some cases alter the existing measure. Some measures are simple and can be written in less than an hour, but sometimes they are more complex and may take a number of days or more to write. When the measure is going to take a long time, try not to go into a wormhole into each measure as you write it. Make a simplified first pass that runs, even if it is with limited functionality. This allows you to start to test the measures in a full workflow early on. The workflow testing is an important milestone as it validates that the overall logic of the process is working. It also allows multiple people to build out detail and functionality on individual measures while maintaining a test of the full workflow.

Having a version control system like Git or SVN is very useful for managing the coding process, in particular if a team will be working on the project. Once the workflow testing is passing you should try not to break it on the main branch of the repository. When breaking a measure in the process of adding more functionality; use your local checkout on your computer or on a branch in a repository. This isolates everyone else and the workflow testing from any instability.

## Testing the Entire Workflow
Workflow testing shouldn't wait until the end after all the code is written, it should be up and running as soon as possible. Each measure already has it's own unit test, but workflow testing provides a a cradle to grave test of all of your measures used in their intended combinations. Below are few options for workflow testing.

* Use the measures section of the OpenStudio application. (This isn't recommended because measure reporting in the OpenStudio application isn't as accessible as it is in PAT
* Use PAT with only "Always Run" Measures (this will produce only a single model and simulation. This is ok, but having multiple Paths for argument values is ideal
* Use PAT with a combination of "Always Run" and "Measure Group" measures. This will allow you to test more scenarios.
* Use the OpenStudio Analysis spreadsheet [described here](https://github.com/NREL/OpenStudio-analysis-spreadsheet). You can export a PAT project to the spreadsheet as a starting point.
* We are working on a scripted workflow testing solution that allows many tests to be run without having to trigger simulations. This is very useful for times when you want to inspect the model or the measure logging to see if it looks like it should. Because this is text based it is more manageable in version control than OpenStudio projects or Excel spreadsheets. When this is ready for use we will link to it from this documentation.

