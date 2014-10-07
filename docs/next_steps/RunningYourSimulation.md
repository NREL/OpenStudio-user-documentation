# Running Simulation & Viewing Results

## Weather File and Design Days
Add weather files in the OpenStudio application under the Site tab (first vertical tab) on the left and the "Weather File & Design Days" sub-tab across the top. You can [download weather files](http://apps1.eere.energy.gov/buildings/energyplus/) on the EnergyPlus site.

![Weather File](../../img/run/weather_ddy.png "Add Weather File and Design Day")
<p>*Above: Screenshot of browsing for design day file.*</p>

## Requesting Output Variables

To select an output variable turn the toggle button to show a blue on. Then set the detail level you want from the drop down menu.

![Output Variables](../../img/run/output_variables.png "Select Output Variables")
<p>*Above: Screenshot of selecting output variables.*</p>

You can also choose variables to collect data on by using the "Add Output Variable" measure under the reporting measure category.

![Variables Measure](../../img/run/variables_measure.png "Measures to Get Variables")
<p>*Above: Screenshot of the variable measure being added to a project. Just type in the variable you want to collect in the edit panel.*</p>

## Running a Simulation
To run your simulation hit the green run button. Select the daylighting engine you want to use, EnergyPlus or Radiance. To use Radiance your file must be set up correctly. You will get a warning dialog if your file is not able to use Radiance.

![Running](../../img/run/run.png "Running a Simulation")
<p>*Above: Hit the run button to start running your simulation.*</p>

![Radiance Warning](../../img/run/radiance_warning.png "Radiance Error")
<p>*Above: If you select Radiance you must have the required objects in your model.*</p>


![Run Errors](../../img/run/output.png "Run Output")
<p>*Above: The output area displays the status of the run.*</p>

## Looking at Results
Standard OpenStudio results are provided with your run. If you add in utility bills you can also view a calibration report.

You can also use measures to add additional reports. You can also write your own measures to create custom reports. Add reporting measures on the OpenStudio Measures or Scripts tab.

![OS Results](../../img/run/os_results.png "OpenStudio Results")
<p>*Above: This screenshot shows and example of the standard OpenStudio results.*</p>

![Calibration Report](../../img/run/calibration_report.png "Calibration Report")
<p>*Above: The calibration report compares utility bills with the model.*</p>

## Using ResultsViewer 
ResultsViewer displays EnergyPlus output in formats that are more useful than those available directly from the EnergyPlus engine. This application was originally developed to support the needs of researchers at the National Renewable Energy Laboratory, who frequently use detailed EnergyPlus outputs to understand the intricacies of building systems.

ResultsViewer displays time series results, which are produced from EnergyPlus report variable requests. ResultsViewer reads the sqlite database output of the EnergyPlus engine and presents the time series data in line and two-dimensional flood plots. It also displays the html output of EnergyPlus in an internal browser window. ResultsViewer is still an immature product; it will be refined further and results viewing capabilities will be added. 

#### Quick Start

1. Request SQLite database output from EnergyPlus (EnergyPlus version 5.0.0 or newer must be used). Include one of the following lines in the IDF file:

        Output:SQLite, Simple;  or  Output:SQLite, SimpleAndTabular;
 
2. Choose either Simple or SimpleAndTabular. (ResultsViewer does not use tabular data.) Once the database output is requested, all report variable and meter requests will be output to the database. These can be viewed in ResultsViewer.
3. Click File->Open and browse to an eplusout.sql file in the EnergyPlus output folder. ResultsViewer is packaged with an example file that can be used to explore the software's capabilities; running EnergyPlus is not necessary.
4. Examine output variables on either of two main views, table view or tree view, on the left.
5. To plot an item, right click for a context menu or double click for a line plot.
6. Drag items from each view onto a plot. In a line plot, the data will be added as an additional curve. In a flood plot, the data will be replaced with the dragged item.

#### Opening an EnergyPlus Output File

1.  Run Result Viewer on Windows by clicking on Start->Programs->OpenStudio->ResultsViewer and on the Mac by going to Applications/OpenStudio/ResultsViewer. 
![RV Start](../../img/run/rv_start.png "ResultsViewer Start")

2.  Click File->Open and browse to your project folder
3.  Select the "eplusout.sql" file and click "Open"
    ![RV Open](../../img/run/rv_open.png "ResultsViewer Open")

ResultsViewer provides two views, "Table View" and "Tree View", on the left hand side for navigating through the output file. A report summary for the output file is provided on the right side "Eplustbl.htm"

![RV Initial](../../img/run/rv_initial.png "ResultsViewer Initial")

#### Generate a Line Plot
To generate a line plot from the table view, simply double-click on a row. In the tree view, open the categories and click on the name of the item you want to plot. 

For example, double-clicking the first row in the table view generates the Electricity:Facility line plot.

The tree view is used to view the EnergyPlus results in a hierarchical format. The hierarchy is based on the environmental period, the timestep, the variable name and the key name (when available). The tree view supports multiple selections using the "Ctrl" or "Command" and "Shift" keys with the mouse. The context menu provides the same functionality as the table view.

![RV Line Plot](../../img/run/line_graph1.png "ResultsViewer Line Plot")

#### Using the Plot Toolbar
![RV Toolbar](../../img/run/plot_toolbar.png "Toolbar")

* The "Select mode" ![RV select](../../img/run/plot_select.png "Select Mode")tool plot select mode is used to select the legend and move it. Sometimes the legend is behind plot lines and with this tool you can place the legend if a better place.
* The "Pan mode" tool ![RV Pan](../../img/run/pan.png "Pan")plot pan mode is used to drag the plot within the plot window. To pan a plot, click the pan mode tool and then click and drag the plot to the desired location. Clicking the "Zoom Out" tool![RV Zoom](../../img/run/zoom_out.png "Zoom Out") zoom out tool repeatedly resets the plot to the original position.
* The "Value Info mode" tool ![Value Info](../../img/run/value_info.png "Value Info") plot value info mode is used to show a value on a line in the plot. To display the value of a point on a curve, click on the value info mode tool and then locate the cursor near the point of interest and then click the mouse. The information in the box can be copied to other applications by selecting the desired text and **ctrl+c** or right mouse click in the box.
![RV Info](../../img/run/info_image.png "Info)
* The "Rubber-band zoom mode" tool ![Rubber-band Zoom](../../img/run/rubberband_zoom.png "Zoom Box") plot zoom mode is used to zoom in on the plot. To zoom in on a particular area of interest, click on the zoom mode tool and then click within the plot near the place of interest and hold the mouse button down and drag the green rectangle to enclose the desired area and then release the mouse button.
![Rubber-band Zoom Draw](../../img/run/rubberband_zoom_image.png "Zoom Box Draw")    ![Rubber-band Zoom Example](../../img/run/rubberband_zoom_image2.png "Zoom Box Example")

* The "Zoom In" ![zoom in](../../img/run/zoom_in.png "Zoom In") tool and the "Zoom Out" ![zoom out](../../img/run/zoom_out.png "Zoom Out") tools are used to zoom back in or out of the plot view.
* The "Save Image" tool ![Save Image](../../img/run/save_plot_image.png "Save Image") save plot image mode is used to save the plot to disk as an image file. Currently supported formats are JPEG, PNG and BMP. Currently supported resolutions are the current image size, 800x600, 400x300. To save a plot to an image file, click the save image tool and then select the desired resolution and then select the desired file locations and format.
 ![Save Image Screenshot](../../img/run/save_image_shot.png "Save Image Screenshot")

* The "Print" tool ![Print Plot](../../img/run/print_plot.png "Print Plot") print mode is used to print the plot. Selecting the print tool brings up a print dialog which is used to select the desired system printer.
* The "Properties" tool ![Plot Properties](../../img/run/plot_preferences.png "Plot Properties") print properties tool is used to change characteristics of the plot. Selecting the properties tool brings up a dialog which is used to change plot title, axes titles, legend display, curve styles and to remove curves from the plot.
![Properties Screenshot](../../img/run/properties_shot.png "Properties Screenshot")

#### Using the Plot Center and Span Controls
The plot window contains "Center" and "Span" controls near the bottom of the window. These controls are used to move along the horizontal axis of the plot. The "Center" control specifies the horizontal center that is displayed in the plot window. The "Span" control specifies the interval on each side of the "Center" that is displayed in the plot window. The values displayed are in fractional simulation days.

For example, to display simulation days 3 through 5 in the example line plot:

1. Set the "Center" to simulation day 4 using either the slider or spin box arrows or entering 4 into the spin box.
2. Set the "Span" to one simulation day using either the slider or spin box arrows or entering 1 into the spin box.
3. 
The data is displayed from simulation day 3 through simulation day 5:
![Center and Span](../../img/run/center_span.png "Center and Span Controls")

The data can now be viewed two simulation days at a time by sliding the "Center" slider with the mouse:
![Center and Span on 2 Days](../../img/run/center_span2.png "Center and Span for 2 Days")

#### Generate Multiple Lines on a Single Plot
To generate a line plot with multiple curves, use the mouse with the "Shift" and "Ctrl" keys to select the desired rows in the table view. Holding the "Ctrl" key down on Windows and "Command" on the Mac and clicking a selected row with unselect the item. Select the "Line Plot" from the context menu. In the tree view, find the names of the items you want to plot on the tree and select then holding down the "Command" or "Ctrl" key.
![Multiple Line Chart](../../img/run/multi_line_plot.png "Multiple Line Plot from Table view")

*Above: Screenshot showing selected multiple lines in table view.*

![Multiple Line Chart2](../../img/run/multi_line_plot2.png "Multiple Line Plot from Tree view")

*Above: Screenshot showing selected multiple lines in tree view.*

#### Generate a Difference Plot
Difference plots are obtained by selecting two rows in the table view. The context menu is then used to plot the difference of the two selections.

Select the two items you want to plot and then right click one of the rows to view a context menu. Choose from the list to get the desired difference line plot.

![Difference Line Chart 1](../../img/run/difference_plot1.png "Difference Line Plot 1)

![Difference Line Chart 1](../../img/run/difference_plot2.png "Difference Line Plot 2)

#### Using the Table View to Generate a Flood Plot
Flood plots are used to present data as a color map or contour map. The bottom axis displays days and the left axis displays hours within the day. Flood plots are most interesting for Hourly, Zone Timestep and HVAC System Timestep data.

For example, a flood plot of the hourly Electricity:Facility data is generated as follows:

Right mouse click on the Electricity:Facility row in the table view.
Select "Flood Plot" from the context menu.

![Flood Plot](../../img/run/flood_plot.png "Flood Plot")

To create a flood plot from the tree view, select the item you want to plot and hit the "Flood Plot" button on the toolbar.

![Flood Plot from Tree](../../img/run/tree_flood_plot.png "Flood Plot from Tree View")

#### Filtering the Views
Filtering is limiting the items that appear in the views by specifying criteria that the displayed fields must match. Filtering applies to both the table view and the tree view. Any data that matches the value entered in the "Filter Criteria" is displayed. If data in any column matches the "Filter Criteria", then the row is displayed in the table view. If data in any node along a branch matches the "Filter Criteria", then the entire branch is displayed in the tree view. The "Filter Criteria" is evaluated as a regular expression. Currently, no phrases and no boolean operators (AND, OR, etc.) are supported.

![Filter](../../img/run/filter_criteria.png "Filter Criteria")

Regular expressions are supported in the "Filter Criteria". For example, to display all data that has a field beginning with "N":

Enter "^N.*" in the "Filter Criteria" box above the tree view.
Click the "Apply" button.

#### Using the Tree View to Generate an Illuminance Map
Illuminance maps are used to show daylight intensity in a given region.

To generate an illuminance map using the tree view:

1.  Open an sql file that contains daylighting analysis
2.  Switch to the tree view tab and scroll down to the "Illuminance Map" section under the "Hourly" time step and right mouse click:
3.  Click on the "Illuminance Map" menu item on the context menu to generate a plot like the one below.

Note that double clicking on the "PERIMETER_ZN_1" under the "Illuminance Map" node is the same as clicking on the "Illuminance Map" menu item in the context menu.

If time series and illuminance map items are selected, no plotting occurs and the following warning message is shown:

![Map](../../img/run/illum_map_example.png "Illuminance Map") 

#### Using the Table View to Generate an Illuminance Map Difference Plot
Illuminance maps differences can be used to look at intensity differences between zones.

To generate an illuminance map difference using the table view:

1.  Enter "Illuminance Map" in the "Filter Criteria" section and click the "Apply" button to get the list of Illuminance Maps for the file.
2.  Hold down the Ctrl and click on the items in table and then right mouse click on one of the selections for the following context menu.
3.  Then select your desired difference plot.
 
![Difference Map](../../img/run/differ_flood_plot.png "Difference Map") 


