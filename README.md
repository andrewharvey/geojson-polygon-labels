# geojson-polygon-labels

Command line tool to generate point labels from GeoJSON polygons.

Features include:

 * Supports GeoJSON FeatureCollections or GeoJSON Features separated by a newline
 * Point and LineString features present in the input are ignored
 * Supports GeometryCollections and MultiPolygons with options to label each part (`--collections=explode`), only the largest part (`--collections=largest`), or treat all parts as one (`--collections=combine`)
 * Label placement algorithm supported are:
   * [polylabel](https://github.com/mapbox/polylabel) *pole of inaccessibility*, the most distant internal point from the polygon outline
   * [center](https://turfjs.org/docs/api/center), simple center by finding the midpoint between the extents of the polygon
   * [center of mass](https://turfjs.org/docs/api/centerOfMass), imagine the polygon is a sheet of paper, finds where the sheet would balance on a fingertip
   * [center mean](https://turfjs.org/docs/api/centerMean), takes the average of all the coordinates, unlike center it is sensitive to clusters and outliers
   * [center median](https://turfjs.org/docs/api/centerMedian), takes the mean center and tries to find, iteratively, a new point that requires the least amount of travel from all points in the polygon. not as sensitive to outliers as center-mean
   * [centroid](https://turfjs.org/docs/api/centroid), find the mean of all the verticies within the polygon
   * [point in polygon](https://turfjs.org/docs/api/pointOnFeature), finds an arbitrary point guaranteed to be within the polygon
 * Source feature properties are retained
 * Optionally adds an `_area` property (in m²) (`--include-area`)
 * Optionally adds a `_bbox` property (`[west, south, east, north]`) (`--include-bbox`)
 * Optionally adds a `tippecanoe` minzoom to each label (`--include-minzoom`)

## Install

    npm install --global geojson-polygon-labels

## Command Line

    geojson-polygon-labels [--precision=0.001] [--include-area] [--include-bbox] [--label=polylabel] [--style=explode] [--include-minzoom=0-16] [--verbose] layer.geojson > labels.geojson

 - `--polylabel-precision` Polylabel precision. Defaults to `0.000001`.
 - `--coordinate-precision` Output coordinate precision. Defaults to `5`.
 - `--method` Label placement algorithm. Options are `polylabel`, `centroid`, `center-of-mass`, `center-mean`, `center-median`, `centroid`, `point-in-polygon`.
 - `--include-area` Adds an `_area` property in m².
 - `--include-bbox` Adds a `_bbox` property as `[west, south, east, north]`
 - `--include-minzoom` will try to determine a suitable minzoom for the label to appear at and save it in the `tippecanoe` key for use in tippecanoe. Value in the form min-max where min is the smallest minzoom and max the largest minzoom.
 - `--collections` How to place labels for GeometryCollections or Multi\* Geometry types. Options are `explode`, `largest`, `combine`.
 - `--input-format` Input format. Options are `geojson`, `geojsonseq`.
 - `--output-format` Output format. Options are `geojson`, `geojsonseq`.
