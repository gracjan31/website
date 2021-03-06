:Author: René Westerholt (edited Daniel Kastl)
:License: Creative Commons

.. _convert_osm:

================================================================
 Converting OSM-Files into PostgreSQL-Scripts
================================================================

**Author:** René Westerholt (edited by Daniel Kastl)

If you desire to put some data for displaying as an WFS or WMS into your 
database you will assert, that most of the available tools for doing something 
like this are not very satisfying. The tool "osm2pgsql" has the fault, that only 
attributes that are necessary for rendering the map, are imported into your 
database. If you want to have the attribute "surface" (for example) in your 
database, this wouldn't be imported by osm2pgsql.

The tool "osm2pgrouting" works well with creating a routing topology, but it's 
not usefull for the problem aforementioned. "osmosis" is another tool for 
importing data into a PostgreSQL database. But it creates a table structure that 
is very disastrous because it creates one row for each attribute that belongs to 
a geometry. So, if your geometry has 5 attributes, there would be 5 rows with 
the structure: ID, Attribute. If you have a big amount of data, you will assert 
that this would be very uncomfortable.

Here are some new java programs written by myself, that make it very easy to 
import data from OSM-Files into your PostgreSQL databases:

* :download:`nodes2postgis.jar <download/nodes2postgis.jar>`
* :download:`lines2postgis.jar <download/lines2postgis.jar>`
* :download:`latlon2google.jar <download/latlon2google.jar>`

The use of the programs is as follows:

For nodes2postgis.jar: 

.. code-block:: bash

	java -jar nodes2postgis.jar map.osm 


For lines2postgis.jar: 

.. code-block:: bash

	java -jar lines2postgis.jar map.osm 


For latlon2google.jar: 

.. code-block:: bash

	java -jar latlon2google.jar yourTablename 


The result of running those java-programms are .sql scripts that can be easily 
loaded in the SQL-Performer in PGAdmin III or even be executed on command-line 
as ususal.

.. note:: 

	The program "latlon2google" converts the data in the declared table from 
	geographical reference system into the google projection.
	

	
