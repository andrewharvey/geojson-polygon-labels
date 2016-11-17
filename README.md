# geojson-polygon-labels

Command line tool to generate point labels from GeoJSON polygons. Point and Line features present in the input are ignored. Internally we use [geojson-flatten](https://github.com/mapbox/geojson-flatten) to get seperate point labels for MultiPolygons and GeometryCollections and [polylabel](https://github.com/mapbox/polylabel) to generate the position of the label by finding the *pole of inaccessibility*.

## Build

    npm install

## Command Line

    geojson-polygon-labels < layer.geojson > labels.geojson
