## Overview of OpenStudio Model Objects

### Benefits of Understanding the Model Structure
One of the advantages of OpenStudio, is that it adds modern object oriented software concepts such as relationships and inheritance  to EnergyPlus.  This makes it much easier to add new functionality to tools or write measures that can quickly manipulate energy models.  From a practitioner’s perspective, inheritance makes it very easy to quickly create new models.  __When you’re using OpenStudio templates to define building and space types, you’re using this capability to avoid specifying the hundreds or thousands of pieces of information EnergyPlus requires to create a detailed simulation.__

### Relationship Diagram
The diagram below shows the OpenStudio 0.6.0 Model Objects Hierarchical Relationships. This is not a comprehensive diagram, but rather focuses on the building envelope (external loads) and building activity (internal loads). It is a good reference to understand where objects reside in the model, and what other objects they impact, and are impacted by.

<a href="../../img/model/model_object_relationships.jpg" target="_blank">
<img src="../../img/model/thumb_model_object_relationships.png" alt="Resized JPEG graphic" title="Click to view" border="2" width="750" height="544" hspace="10" /></a>
<p>*Above: Click to view a larger diagram of model relationships.*</p>

### Inheritance
The diagram below shows the OpenStudio 0.6.0 Model Objects Inheritance Relationships. Again, this is not a comprehensive diagram, but focuses on some of the more commonly used objects. The red dot in each column represents the first place our OSM to IDF translator looks when converting  an OSM object to an IDF object or objects. If The field value is blank where the red dot is, the translator looks at the object where the yellow circle is, and continues this until the end of the path. The ability for objects to inherit values from elsewhere in the model allows for quick global changes, and for customization of any individual object in the model.

<a href="../../img/model/openstudio_inheritance.jpg" target="_blank">
<img src="../../img/model/thumb_openstudio_inheritance.png" alt="Resized JPEG graphic" title="Click to view" border="2" width="750" height="613" hspace="10" /></a>
<p>*Above: Click to view a larger diagram of model inheritance.*</p>
