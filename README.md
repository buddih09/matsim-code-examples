[![mvn-verify](https://github.com/matsim-org/matsim-code-examples/actions/workflows/mvn-verify.yml/badge.svg?branch=15.x)](https://github.com/matsim-org/matsim-code-examples/actions/workflows/mvn-verify.yml)

# matsim-code-examples
A repository containing code examples around MATSim.

# Generate network
Install Osmosis: Follow the instructions in http://wiki.openstreetmap.org/wiki/Osmosis. 

Download the required xxx.osm.pbf file from http://download.geofabrik.de/. 

Run the following commands:
```
osmosis --read-pbf-fast file=switzerland-latest.osm.pbf --bounding-box top=46.034 left=8.936 bottom=46.007 right=8.978 completeWays=true --used-node --write-pbf allroads-example.osm.pbf
osmosis --read-pbf-fast file=switzerland-latest.osm.pbf --tf accept-ways highway=motorway,motorway_link,trunk,trunk_link,primary,primary_link --used-node --write-pbf bigroads-example.osm.pbf
osmosis --rb file=bigroads-example.osm.pbf --read-pbf-fast allroads-example.osm.pbf --merge --write-xml merged-example-network.osm 
```
An example script of how to convert the resulting merged-example-network.osm file into a MATSim network file is RunPNetworkGenerator.java in matsim-code-examples.
