# Notes on Scraping

After waiting a year for the Virginia Department of Health to release their data, it now seems unlikely that they will do so. As such, it's time to start writing a scraper.

## Steps

1. Manually assemble an array of localities and their URLs (e.g., `Albemarle` `=>` `http://www.healthspace.com/Clients/VDH/TJefferson/TJefferson_Website.nsf`).
1. Iterate through the list of locality URLs and iterate through the alphabet to generate a URL for every letter of the alphabet with which an establishment's name can start (e.g., `http://www.healthspace.com/Clients/VDH/TJefferson/TJefferson_Website.nsf/Food-List-ByFirstLetterInName?OpenView&Count=1000&RestrictToCategory=A`). Store the resulting data (name, URL, address, smoking status, last inspection date), plus the locality's name. Store each locality's data as a JSON file, and combine all of them into one master JSON file.
1. Load the JSON file from the previous time that the scraper was run, if it exists ("old records").
1. Load the master JSON file ("new records") and iterate through every establishment. If the date of the last inspection in the new record is newer than the date in the old record, then proceed.
1. Open the record for the establishment. (e.g., `http://www.healthspace.com/Clients/VDH/TJefferson/TJefferson_Website.nsf/Food-FacilityHistory?OpenView&RestrictToCategory=A1CFEFF6506B3605852572050052CDB9`.) Grab the complete address, facility type, facility phone number, and the tabular "Facility Inspection History" data. Save this to a JSON file.
1. Iterate through the inspection history table, saving the inspection type, inspection date, and URL. If the inspection date is newer than the one in the date of the old record, then proceed.
1. Open each inspection history URL. Save the number of critical violations, the number of non-critical violations, the comments, and each recorded violation, if any (code, observation, corrective action, and whether it's critical or non-critical). Save this inspection data to the establishment's JSON file.

## Notes

* It will be tempting to use the "(sorted by last inspection date)" view of all restaurants in a given locality. This is a mistake, because that, mysteriously, fails to list every restaurant, and misses many inspections.
