## Overview of OpenStudio Model Objects

### Relationship Diagram
The diagram below shows the OpenStudio 0.6.0 Model Objects Hierarchical Relationships. This is not a comprehensive diagram, but rather focuses on the building envelope (external loads) and building activity (internal loads). It is a good reference to understand where objects reside in the model, and what other objects they impact, and are impacted by.

![Relationships Diagram](../../img/model/model_object_relationships.jpg "Relationships Diagram")
<p>*Above: Diagram of model relationships.*</p>

### Inheritance
The diagram below shows the OpenStudio 0.6.0 Model Objects Inheritance Relationships. Again, this is not a comprehensive diagram, but focuses on some of the more commonly used objects. The red dot in each column represents the first place our OSM to IDF translator looks when converting  an OSM object to an IDF object or objects. If The field value is blank where the red dot is, the translator looks at the object where the yellow circle is, and continues this until the end of the path. The ability for objects to inherit values from elsewhere in the model allows for quick global changes, and for customization of any individual object in the model.

![Inheritance](../../img/model/openstudio_inheritance.jpg "Inheritance Diagram")
<p>*Above: Diagram of model inheritance.*</p>