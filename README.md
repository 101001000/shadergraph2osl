# Blender Shading Graph -> OSL serializer.

# ATTENTION, WIP: Nothing works yet!

OSL proposes a way to serialize shader groups in the 9th chapter of their [specification](https://github.com/AcademySoftwareFoundation/OpenShadingLanguage/blob/main/src/doc/osl-languagespec.pdf)

Blender uses OSL for Cycles Render, but a custom shading node design which needs to be manually serialized or interpreted for many use cases.

In this repo, I propose a way to convert that custom shader graph implementation, to a representation of the graph which conforms the OSL spec proposal.


## How to use it:

You have two options here:
The first one is to use the standalone plug-in, which will output a text file of the shadergroup desired.
The second one is to copy the repo, and use it as a library without the plugin for you application.


## Dependencies:

If you're using the standalone plugin, you need to install the following dependencies on the Blender's Python installation

* [Pyecore](https://github.com/pyecore/pyecore) 
* [Motra](https://github.com/pyecore/motra)

If you're using it as a library for interacting with blender, you need the additional dependencies:
* [bpy](https://pypi.org/project/bpy/)
* Python = v3.10



## How it works:
To make this possible, instead making manually a graph parser, I did two metamodels. The first one, fits the Blender shading graph, and the second one, one which fits the OSL serialization model. 

Then I described a model to model transformation. This allows to have all the transformation details, all parameter mappings and all shader names, organized.

Finally, the new model, is converted to the OSL serialized representation with a Model To Text transformation.
