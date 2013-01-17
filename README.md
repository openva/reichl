Reichl
======

Tools to parse and analyze Virginia Department of Health restaurant inspection reports.

This data is presently available at http://www.healthspace.com/Clients/VDH/vdh_website.nsf, though not in bulk or in any machine-readable format. This project is awaiting a bulk release of this data from the Virginia Department of Health.

A pair of sample files are available. They were provided in response to a FOIA request for a complete dump of all records for a single Department of Health district for one year. A single Excel file was provided, with data in two worksheets. Each of those worksheets is provided as a CSV file, titled as the worksheet was titled: FoodInspection.csv and CombInspWithViolationsLong.csv. The bulk data provided by VDH is likely to resemble substantially these files.

Planned tasks:

* Create a parser to for the provided data to (inevitably) turn it into friendlier formats—JSON, XML, YAML, etc.
* Install repository software ([CKAN](http://ckan.org/)?) to host the data, display it on screen, and provide an API.
* Write an algorithm to analyze inspection data and assign some kind of a quantitative indicator of the restaurant's cleanliness. (Virginia does not grade or otherwise rank restaurants, making this a useful function.)
* Create an exporter to render data [per Yelp's specs](http://www.yelp.com/healthscores), and syndicate inspection data to Yelp.

Pronounced RYE-chil.
