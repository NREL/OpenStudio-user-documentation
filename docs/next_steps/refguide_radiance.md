<h1>OpenStudio-Radiance Reference Guide</h1>
This reference guide explains how to use [Radiance](http://www.radiance-online.org/) to simulate the daylight ingress in your OpenStudio model, allowing for higher fidelity simulations of daylighting-related energy efficiency measures. Radiance is not constrained to simple geometry, and the OpenStudio model supports interior architectural detail such as [interior partition surfaces](next_steps/sketchup_plugin_interface#NewInteriorPartitionSurfaceGroup) (for representing columns, soffits, furniture, etc) and air walls (for eliminating thermal zone boundaries that do not correspond to any actual building architecture). This allows for a more accurate characterization of the spatial distribution of daylight in the OpenStudio model. 

For OpenStudio [v1.7.0](https://github.com/NREL/OpenStudio/releases/tag/v1.7.0), added support for window shades and wall thickness has increased the utility of the Radiance simulation option in the OpenStudio application. 

The 3-Phase method is used in OpenStudio for conducting annual climate-based daylight simulations in a reasonably fast manner. This method solves the flux transfer from the sky to the window, separately from the flux transfer from the window to the point(s) of interest in the space. These matrices are called the daylight matrix (DMX) and view matrix (VMX), respectively. A third matrix called the transmission matrix (T), is represented by a bidirectional scattering distribution function (BSDF). The BSDF optically characterizes the shading layer and is inserted into the matrix and multiplied by a sky matrix (s) for each timestep to give a single hourly result for the model:

I<sub>3ph</sub> = VTDs

Where:

We rely on the rfluxmtx tool in Radiance to handle the creation of all the necessary daylight coefficient matrices, and on some generic BSDFs from the Building Component Library to represent the shading layers. The OpenStudio-to-Radiance model translator groups the building fenestration by unique (1) orientation, (2) visible light transmittance, and (3) shading control type. 
