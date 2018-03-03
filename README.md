# geojson-polygon-labels

* Command line tool to generate point labels from GeoJSON polygons.
* Point and Line features present in the input are ignored.
* Supports GeometryCollections and MultiPolygons with options to label each part, only the largest part, or treat all parts as one.
* Label placement algorithms are [polylabel](https://github.com/mapbox/polylabel) *pole of inaccessibility*, [centroid](http://turfjs.org/docs/#centroid) and [center of mass](http://turfjs.org/docs/#centerofmass).
* Source feature properties are retained.
* Optionally adds an `_area` property (in m²)
* Optionally adds a `tippecanoe` minzoom to each label

## Install

    npm install --global geojson-polygon-labels

## Command Line

    geojson-polygon-labels [--precision=0.001] [--include-area] [--label=polylabel] [--by-feature] [--include-minzoom=0-16] [--verbose] layer.geojson > labels.geojson

 - `--precision` Polylabel precision. Defaults to `0.001` since GeoJSON is usually in geographic coordinates.
 - `--label` Label placement algorithm. Options are `polylabel`, `centroid`, `center-of-mass`.
 - `--include-area` Adds an `_area` property in m².
 - `--style` How to place labels for GeometryCollections or Multi\* Geometry types. Options are `explode`, `largest`, `combine`.
 - `--include-minzoom` will try to determine a suitable minzoom for the label to appear at and save it in the `tippecanoe` key for use in tippecanoe. Value in the form min-max where min is the smallest minzoom and max the largest minzoom.
