# ulp2emf
EMF vector image exporting tool
<p>
This ULP exports EMF (Enhanced Metafile) vector images from Eagle schematics and boards.
Load any schematic or board and run the ULP. You have to manually enable or disable visible layers
before you run the ULP. If your board contains polygons, you must use the Ratsnest command 
to process them, otherwise only their outline will be exported. 
Some export parameters are configurable, you need to edit variables in the ULP.
<p>
<author>Author: Roman Sickaruk, romansichkaruk(at)gmail(dot)com<br><br>
The ULP is partially based on: <ul>
<li>eagle2svg by nils(dot)springob(at)nicai-systems(dot)de</li>
<li>sch2wmf by henrik(dot)haftmann(at)e-technik(dot)tu-chemnitz(dot)de</li>
</ul><p>
The ULP was created as a part of master's thesis 'Program pro export vektorovych obrazku z Autodesk Eagle' 
at the Faculty of Electrical Engineering and Communication, Brno University of Technology, 
thesis supervisor Pavel Hanak, hanakp(at)feec(dot)vutbr(dot)cz
<br>

<p>
  License: This file is released under GNU Public license Version 2. 
<p>

<p> THIS PROGRAM IS PROVIDED AS IS AND WITHOUT WARRANTY OF ANY KIND, EXPRESSED OR IMPLIED <p>

<br> The EMF format has some quirks and limitations that prevent accurate reproduction of board layers. Probably the biggest limitation is the absence of transparency, so all layers are 
always 100% opaque on white background. Moreover, different programs (MS Office, Adobe Illustrator, Inkscape) interpret the EMF files differently, which results in visual artefacts in some cases.
To combat this, there are several user-configurable variables:

<br> Variable "roundedRectangles" is particularly useful for MS Office products, because they incorrectly import roudned rectangles (they are missing if you insert the EMF file into your document).
Setting this variable to 0 will fix it, but at the cost of lesser fidelity of the image.

Normally, the program exports the layers like they are ordered in Eagle. However, EMF doesn't support transparency, so some objects on a board may become hidden under other objects. Therefore, the ULP forces some layers to be processed first and other layers last. You can change them with "firstLayers" and "lastLayers" variables (enter layer names or their numbers).
Don't forget to put the correct number of layers into the "firstLayersCount" and "lastLayersCount" variables if you use this feature.

Example:
Original:
![alt text](https://github.com/RomanSichkaruk/ulp2emf/blob/master/demo2.png?raw=true)
Generated EMF:
![alt text](https://github.com/RomanSichkaruk/ulp2emf/blob/master/demo2g.png?raw=true)
