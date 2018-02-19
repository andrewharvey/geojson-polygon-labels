## 1.1.0

* Add `--by-feature` flag to only label the largest part in a MultiPolygon feature #2
* 'use strict' for compatibility with older versions of node

## 1.0.4

* Fixes to usage and add `--help`

## 1.0.3

* Revert undeclared breaking change in units of `_area`.

## 1.0.2

* Stream geojson features to process larger input files. As a result of this input features geojson is no longer read from stdin but instead a file.
* Add an `--include-area` flag to control the creation of the `_area` property.
* Add support for other label placement algorithms. Options are now [pole of inaccessibility](polylabel), [centroid](http://turfjs.org/docs/#centroid) or [center of mass](http://turfjs.org/docs/#centerofmass).

## 1.0.1

* Use a polylabel precision more appropriate for geojson usually in geographic coordinates

## 1.0.0

* Initial release
