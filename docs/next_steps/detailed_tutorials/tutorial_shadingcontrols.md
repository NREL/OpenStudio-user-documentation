<h1>OpenStudio Shading Controls</h1>
This tutorial explains how to add shading controls to an OpenStudio model to study the impact of blinds, shades, switchable glazing, or other shading controls.

## Setting up the initial model

1.  Create a model with fenestration.  Apply a fenestration construction which represents the unshaded state to your windows.  Create either a fenestration construction representing the shaded state or a shading material such as a blind, screen, or shade.  Run the "Add Shading Controls" user script to create a shading control object.

![Add Shading Controls](../../../img/tutorials/shadingcontrol1.png)

Chose either your shaded construction or shading material.

![Add Shading Controls](../../../img/tutorials/shadingcontrol2.png)
 
2.  Select the windows that you want to apply the shading controls to.  This can be done individually or by using the surface search feature.  Run the "Apply Shading Controls" user script to apply a shading control object to the selected windows.

![Apply Shading Controls](../../../img/tutorials/shadingcontrol3.png)

3.  Edit details related to the shading control object (e.g. control algorithm) using the OpenStudio inspector.

![OpenStudio Inspector](../../../img/tutorials/shadingcontrol4.png)
    
You can also assign shading control objects to individual surfaces using the OpenStudio inspector.

![OpenStudio Inspector](../../../img/tutorials/shadingcontrol5.png)