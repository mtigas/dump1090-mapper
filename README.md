make maps of planes
===================

a node app to generate a map of an airplane's flight path, using its ICAO address and a [mtigas/dump1090-stream-parser database](https://github.com/mtigas/dump1090-stream-parser database)

`nodejs mapify.js ACB963` will generate an SVG map of the most recent path of the NYPD helicopter with the registration number N919PD.

`sh mapify.sh ACB963` will generate a PNG map (by creating the SVG, then converting it to PNG with Apache Batik)

If your MySQL database is not named `dump1090` or isn't accessible by the current user on localhost, specify how to reach it with the environment variables `MYSQLHOST`, `MYSQLPORT`, `MYSQLUSER`, `MYSQLPASSWORD` and `MYSQLDATABASE`.

prereqs
-------

  - ADSB radio, etc.
  - github.com/mutability/dump1090
  - github.com/mtigas/dump1090-stream-parser
  - nodejs, etc. and stuff


TODO
----

  - plane path should indicate altitude or speed or something with a gradient (https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Gradients)
  - maybe label airports?
  - use an API or the FAA airplane ownership database to allow planes to be specified by registration, not ICAO address.


Some useful resources.
- http://geoexamples.com/d3/2015/05/29/d3-maps-nodejs.html
- https://bost.ocks.org/mike/map/
- http://stackoverflow.com/questions/5433806/convert-embedded-svg-to-png-in-place


Location and Zoom
-----------------

The base map is centered around New York City: it includes county boundaries and airports in New York, New Jersey and Connecticut, and additional features in New York City. The zoom mechanism assumes your ADSB receiver has the same boundaries (or close to it) as mine. Generalizing this is work that still remains to be done.