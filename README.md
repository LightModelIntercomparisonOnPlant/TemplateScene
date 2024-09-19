# TemplateScene

This template show the format wanted to produce a model to test light model.

A project should contains :
1) Metainformation : A description of how the model works.
2) Plants: a list of one or many plants geometry objects in gltf format. Or in the compress gltf format (.bin)
3) Environment: a list of additional geometry objects that are part of the scene. I.e. the ground.
4) Topology: A CSV file that map the UID of the organs to a Scale
The UID for plant organs are the namespace of the plant file + the gltf name of the node.
5) Lights:
6) Optical_Properties: a list of file that map the UID of either the organs or the Scale to 4 floats: RGBA values 
