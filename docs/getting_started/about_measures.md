<h1>About Measures</h1>
In building design and retrofits, the terms energy efficiency measure (EEM) and energy conservation measure (ECM) refer to a specific change that can be made to a building to reduce its energy use. As an example, if you are retrofitting an existing building and one of the ECMs suggested by the design team is "Add insulation to the roof", then you can run that measure to quickly alter your model.

In OpenStudio SDK, a measure is a set of programmatic instructions (such as an Excel macro) that makes changes to an energy model to reflect its application. In our example, the measure might find the default construction used by roof surfaces in the model, copy this construction and add insulation material to the outside, then set the new construction with added insulation as the default construction to be used by roof surfaces. Measures can be written specifically for an individual model, or they may be more generic to work on a wide range of possible models.

![Measure Diagram](img/measures/what_measures.png)

_________________

## Benefits of Measures
__Measures can help energy modelers by:__

- Reducing modeling time and cost
- Finding deeper savings
- Lowering administrative and training costs
- Maintain quality and consistency

![Expert Energy Modeler](img/measures/expert.png)

![Training One-on-one](img/measures/training_now.png)

![Passing on Knowledge with Measures](img/measures/knowledge.png)

![Passing on Knowledge with Measures and BCL](img/measures/share_bcl.png)

_________________

## How Do You Use Measures in the SDK?

### Command Line Interface

Refer to the Command Line Interface page for information on applying measures as [Subcommands](../reference/command_line_interface/#measure-subcommand) or within an [OpenStudio Workflow](../reference/command_line_interface/#osw-structure).

### Parametric Analysis Tool
Measures are essential to the parametric studies within the [Parametric Analysis Tool](../reference/parametric_analysis_tool_2/#add-measures-and-create-measure-options).

_________________

## Where Do You Find Measures?
### Building Component Library (BCL)
You can find measures by going directly to the [BCL site](https://bcl.nrel.gov/) and searching or browsing for measures.

Measures can be downloaded directly from BCL through the OpenStudio Application and the ParametricAnalysisTool.

### Locally Shared Measures
Under the "Preferences" menu you can set a local measure path using the "Change My Measures Directory" menu option. This allows you to set a local or network directory for measures to show in the OpenStudio Application and Parametric Analysis Tool. This is in addition to any BCL measures you already have downloaded. They local measures will have say "My" in front of them vs. "BCL".

### Create Your Own
Want to write your own custom measure? Start with the [Measure Writing Guide](../reference/measure_writing_guide.md).

