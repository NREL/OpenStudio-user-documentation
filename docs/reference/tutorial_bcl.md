<h1>The Building Component Library</h1>

The [BCL](https://bcl.nrel.gov) is an online repository of components and measures that can be used in OpenStudio. 

There are 2 types of content on the BCL:  components and measures.  Components are the building blocks of an energy model, and include roofs, walls, windows, occupancy and equipment schedules, and weather information, to name a few.  Measures describe a change to an energy model for purposes such as comparison to a baseline model or estimation of potential energy savings. 

The BCL now uses GitHub repositories to manage component and measure content from various users. 
The new [Contribute Data](https://bcl.nrel.gov/contribute) page guides users through the process of creating their own measures and components, gathering them into a GitHub repository, registering the repository with the BCL Manifest, and configuring a webhook to automatically send content to the BCL when a release is made on the repository.


###Creating Measures

New measures are made in the OpenStudio application or Parametric Analysis tool by either creating a new measure or cloning an existing one. OpenStudio will place all necessary files in the directory set under preferences as *My Measures Directory*. Go within the directory for the measure and compress the files as shown below. Confirm that the xml file is updated after your last edit of the measure.rb file by clicking the *Sync Project Measures with Library* button or opening the *Apply Measure Now* dialog.

Additional details on the xml and other files can be found below:

>The measure package to upload should contain a measure.xml file created with the current [measure schema](https://bcl.nrel.gov/static/assets/json/measure_schema.xsd), available on the [BCL](https://bcl.nrel.gov) website. The &lt;uid&gt; and &lt;version_id&gt; fields can be left blank as they will be assigned by the BCL.

>Make sure to include the type of your measure in the &lt;tag&gt; field. Select from the available [BCL measure tags](https://bcl.nrel.gov/tags#measure), and include the full hierarchy. This is usually 2 or 3 levels separated by a dot.  For example, if you are creating a space types measure, the &lt;tag&gt; should be: *Whole Building.Space Types*. If you do not see a suitable measure type for your measure in the list, please [contact us](https://www.openstudio.net/contact).  Attributes can also be applied to measures via the measure.xml file.  Consult the supported list of [BCL attributes](https://bcl.nrel.gov/tags#attributes) to view the correct names. For more detailed information on writing OpenStudio measures, consult the [Measure Writing Guide](../reference/measure_writing_guide.md) for further details.

>The package should also contain the associated files referenced inside the measure.xml file's &lt;files&gt; section. These files should be contained in directories according to usage type:  the main measure file, usually named *measure.rb* should be compressed directly (same level as measure.xml), resource files should be in a *resources* directory, and test files should be in a *tests* directory. The compressed package should directly contain these files and directories; the upload will fail if the package has an inner directory containing the files.

