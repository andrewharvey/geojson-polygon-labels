# geojson-polygon-labels

* Command line tool to generate point labels from GeoJSON polygons.
* Point and Line features present in the input are ignored.
* [geojson-flatten](https://github.com/mapbox/geojson-flatten) is used to get separate point labels for MultiPolygons and GeometryCollections.
* Label placement algorithms supported are [polylabel](https://github.com/mapbox/polylabel) *pole of inaccessibility*, [centroid](http://turfjs.org/docs/#centroid) and [center of mass](http://turfjs.org/docs/#centerofmass).
* Original properties are retained.
* Optionally add an `_area` property (in km²) which is designed to aid in selecting which labels to show/hide based on the zoom level.

## Build

    npm install

## Command Line

    geojson-polygon-labels [--precision=0.001] [--include-area] [--label polylabel] [--verbose] layer.geojson > labels.geojson

Defaults to `0.001` precision since GeoJSON is usually in geographic coordinates.
