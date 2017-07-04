# geojson-polygon-labels

Command line tool to generate point labels from GeoJSON polygons. Point and Line features present in the input are ignored. Internally we use [geojson-flatten](https://github.com/mapbox/geojson-flatten) to get seperate point labels for MultiPolygons and GeometryCollections and [polylabel](https://github.com/mapbox/polylabel) to generate the position of the label by finding the *pole of inaccessibility*.

Original properties are retained, however an `_area` property is added (in sq kilometers) which is designed to aid in selecting which labels to show/hide based on the zoom level.

## Build

    npm install

## Command Line

    geojson-polygon-labels [--precision=0.001] layer.geojson > labels.geojson

Defaults to `0.001` precision since GeoJSON is usually in geographic coordinates.
