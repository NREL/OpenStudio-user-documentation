<h1>Adding Utility Rate Tariffs</h1>
Typically, life cycle cost analyses compare current capital costs required to implement energy conservation measures with future energy cost savings over the analysis period. In order to compute future energy cost savings the model must include information about the utility rate tariffs which apply to the project. Higher energy costs will give energy conservation measures a better pay back relative to their initial costs.

Before this interface is completed, users in the Xcel EDA program may set utility rates for their project in the PAT application using the "Xcel EDA Tariff Selection and Model Setup" EnergyPlus measure. This measure should be added to the simulation workflow as an always run measure so it is applied to all design alternatives in the analysis. Users interested in other utility rates may modify this measure as needed.

## Weather File and Design Days
Add weather files in the OpenStudio application under the Site tab (first vertical tab) on the left and the "Weather File & Design Days" sub-tab across the top. You can [download weather files](http://apps1.eere.energy.gov/buildings/energyplus/) on the EnergyPlus site.

![Open DDY File Dialog](img/run/weather_ddy.png)

*Above: Screenshot of browsing for design day file.*