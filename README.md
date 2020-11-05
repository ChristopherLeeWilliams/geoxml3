# geoxml3
Forked code from https://github.com/geocodezip/geoxml3


\
**Added Features**
<ul>
<li>Added support for the "gx:LatLonQuad" element when parsing KMZ files. Reference: https://developers.google.com/kml/documentation/kmlreference#gxlatlonquad
</ul>

\
**Example Usage For KMZ From Local File Input**

1. Download  geoxml3.js, ProjectedOverlay.js, and ZipFile.complete.js.

2. Include each in your map page:

````javascript
<script src="/js/geoxml3.js"></script>
<script defer src="/js/ProtectedOverlay.js"></script>
<script defer src="/js/ZipFile.js"></script>
````

3. On file input change, instantiate and initialize the geoxml object and read file

````javascript
document.getElementById("my-file-input").addEventListener("change", function(event) {
    let geoXML = new geoXML3.parser({
        map: map, // Google Map
        zoom : true, // Sets viewing bounds after parse
        afterParse: functionToCallAfterParse, // Function to call when parse is complete
    });
    let file = this.files[0];
    let fileURL = URL.createObjectURL(file);
    geoXML.parse(fileURL);
});
````

4. Create the function to be called after the source has been parsed

````javascript
function functionToCallAfterParse(doc) {
    alert("KMZ File Has Finished Loading!");
}
````