# TemplateScene

This template show the format forwanted to produce descriptions of the architectural, spectral and illumination related propertiesa of a scene
 to be illuminated by light models.

A project should contains :
1) Description : A textual description of the scene, with reference and associated measurements.
2) Plant Architecture: a list of plant files describing the geometry of plants in gltf/bin format. One Uid should be used for each organ.
	May also contain R,G,B colors (used for scene rendering only).
3) Background: a list of files describing the geometry of non-plant objects that are part of the scene. I.e. the soil, walls,...
4) Sensors: a list of files describing the geometry of sensors objects that are part of the scene. Sensors ar objects associated to measurements. 
	One Uid per sensor should be used
4) Scale: A list of csv files maping the UID of the plant organs to one or several grouping Scales (one column per grouping scale)
   file scale_PPPP.csv will be associated to plant PPPP. The first column should list node ids containes in the corresponding plant gltf.
5) Spectral_Band: A dict of band_name: [lambda_min, lambda_max] items defining spectral wavelengths associated to a band_name
6) Spectral_Properties: A dict of two items: 
	- "materials": a dict of dict of  "Band_name": {"material_name": "spectral_property", ...}, } 
		defining spectral properties of materials of the scene. Spectral properties are of the form: "type p1 p2", where type
could be 'lambertian','phong' or refer to a bsdf file (https://optics.ansys.com/hc/en-us/articles/18384793374227-Speos-BRDF-BTDF-and-BSDF-Formats).For lambertian materials, type can be followed be reflectance only (opaque), reflectance and transmitance, or reflectance_top, transmitance_top, reflectance_bottom, transmitance_bottom for both sides of the reflector
	- "mapping": a list of csv file that map the UID of the organs to a material_name.
		 file spectral_PPPP.csv will be associated to plant PPPP. The first column should list node ids containes in the corresponding plant gltf.
7) Illumination: A dict of two items:
	- "sky": a {"band_name": csv_file,...} dict specifying the luminance for the sky (infinite light source). The csv should have the form : x y z luminance, where (x,y,z) is the ligth vector direction
	- "light" : a {"band_name": [csv_file,...], }dict of list of ies files specifying the lamps positions and illumination (see https://techshelps.github.io/Acad_aug/WS73099cc142f48755f058a10f71c104f3-3b1a.htm). 
8) "measurements : a {"band_name": {"sensor_side": csv_file, ...},...} dict of dict indicating the files conting the measurment of the sensors in different band and for 'top' or 'bottom' sensor side.
