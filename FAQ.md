## Frequency Asked Questions

#### General

* [I have data and want to publish to OBIS - what do I do?](contribute.html)
* [Why is it important to share and format data?](contribute.html#why-publish-data-to-obis)
* [How do I handle sensitive data?](contribute.html#how-to-handle-sensitive-data)
* [I am having trouble understanding how Core and Extension tables relate to each other](relational_db.html)
* [How does the OBIS format avoid redundancy in data](relational_db.html#how-to-avoid-redundancy)
* [Where can I learn about "Darwin Core"?](darwin_core.html)
* [How are extension tables (e.g. eMOF, occurrence) linked with the core table?](formatting.html#extensions-in-obis)
* [What is the difference between Occurence Core and Event Core?](formatting.html#dataset-structure)
* [What are the responsibilities of node managers?](nodes.html)
* [Where can I find marine datasets linked to the OBIS network by the GBIF registry, that now require endorising?](https://github.com/iobis/obis-network-datasets/)
* [Where can I make suggestions for improvements on this Manual?](https://github.com/iobis/manual)

#### Formatting Data

* [Is there a checklist of all required Darwin Core fields for OBIS?](checklist.html)
* [How does data flow in OBIS?](data_standards.html)
* [What should I do if I do not have the data for required fields by OBIS?](common_formatissues.html#missing-required-fields)
* [How do I construct an eventID?](identifiers.html#eventid)
* [How do I construct occurrenceID?](identifiers.html#occurrenceid)
* [What data goes into Occurrence core (or extension) and how do I set up this file?](format_occurrence.html)
* [How do I set up an Event core table?](format_event.html)
* [What data goes into extendedMeasurementOrFact and how do I set it up?](format_emof.html)
* [How do I map Measurement or Fact terms in OBIS with preferred BODC vocabulary?](vocabulary.html#measurementorfact-vocabularies)
* [I can't find a suitable vocabulary, how do I request a new vocabulary term?](vocabulary.html#requesting-new-vocabulary-terms)
* [How should I match raw data fields with Darwin Core terminology?](vocabulary.html#map-your-data-with-dwc-vocabulary)
* [How do I format dates?](common_formatissues.html#temporal-dates-and-times)
* [How do I handle historical data?](common_formatissues.html#historical-data)
* [How do I convert coordinates to decimal degrees?](common_formatissues.html#converting-coordinates)
* [How do I convert  different geographical formats to WGS84?](common_formatissues.html#geographical-format-conversion)
* [How do I compile acoustic, imaging, or other multimedia data for OBIS?](other_data_types.html#multimedia-data-acoustic-imaging)
* [How do I compile habitat data for OBIS?](other_data_types.html#habitat-data)
* [How do I compile tracking data for OBIS?](other_data_types.html#tracking-data)
* [How do I compile DNA and genetic data for OBIS?](dna_data.html)

#### Tools

* [How do I use the WoRMS taxon match tool?](name_matching.html)
  * [Can I fetch a full classification for a list of species from WoRMS?](name_matching.html#how-to-fetch-a-full-classification-for-a-list-of-species-from-worms)
  * [What do I do if my scientificName does not return a match from WoRMS?](name_matching.html#what-to-do-with-non-matching-names)

#### Quality Control

* [How do I do data quality control?](data_qc.html#how-to-conduct-quality-control)
* [What are the OBIS quality control flags?]()
* [Why are certain records dropped in OBIS?](data_qc.html#why-are-records-dropped)
* What do I do when I am uncertain about the:
  * [Temporal range of a dataset OR eventDate](common_qc.html#uncertain-temporal-range)
  * [Geospatial location](common_qc.html#uncertain-geolocation)
  * [Taxonomic identification](common_qc.html#uncertain-taxonomic-information)
  * [Individual count](common_qc.html#individualcount)
* [What do I do with freshwater species that are part of my marine dataset?](common_qc.html#non-marine-species)

#### Publishing

* [How do I add my data to the OBIS database?](data_publication.html)
* [What metadata do I have to provide? Where? How?](eml.html#metadata-sections)
* [How do you know which license to choose?](data_publication.html#licenses)
* [How do I access the IPT?](ipt.html#how-to-access-the-ipt)
* [How do I use the IPT?](ipt.html#create-your-resource-on-the-ipt)
* [Are there instructions for IPT administrators?](ipt_admin.html)
* [How do I add DOI to my dataset?](data_sharing.html#adding-a-doi-to-datasets)
* [How do I publish to both GBIF and OBIS?](data_sharing.html#simultaneous-publishing-to-gbif)
* [How do I update my already published dataset?](data_sharing.html#update-your-data-in-obis)

#### Accessing data

<ul>
  <li><a href="access.html#obis-homepage-and-dataset-pages">How do I download data from OBIS?</a></li>
  <li><details>
  <summary>How do I load the full (.csv) export of OBIS data?</summary>
  <br>
  
  Loading the entire OBIS dataset uses *a lot* of memory and is probably not feasible on most desktop computers. You have a few potential options depending on the use case:
  
  * Process the data in smaller batches
  * Load the dataset into a local database such as SQLite and use SQL queries to analyze the data
  
  In general, we recommend you use the parquet download which is available on [here](https://obis.org/data/access/), instead of the CSV. Then in R, you can use the [`arrow`](https://arrow.apache.org/docs/r/) package to work with parquet files. We also have a short tutorial on working with parquet files in R [here](https://resources.obis.org/tutorials/arrow-obis/), with an example application of this approach [here](https://iobis.github.io/notebook-diversity-indicators/) (see first code block).
  </details></li>
  <li><a href="access.html#r-package">How can I use R to access OBIS data?</a></li>
  <li><a href="access.html#api">How do I use the OBIS API to fetch and filter data?</a></li>
  <li><a href="access.html#api">How do I contact the data provider?</a></li>
  <li><a href="citing.html">How can I cite OBIS datasets and downloads?</a></li>
  <li><a href="access.html#interpreting-downloaded-files-from-obis">What are the definitions of the field names in the downloads generated by OBIS?</a></li>
  <li><details>
  <summary>How do I obtain a taxon checklist for an area?</summary>
  <br>
  
  There are a few possible ways to obtain a taxon checklist for a given area. We will obtain a checklist of species in the Albain EEZ as an example. To do this we will create a bounding box around our area of interest, and then apply filters to simplify the geometry.

  ```R
  library(mregions)
  library(dplyr)
  library(robis)
  library(sf)
  #obtain Albanian EEZ as sf
  geom <- mr_shp(key = "MarineRegions:eez", filter = "Albanian Exclusive Economic Zone", maxFeatures = NULL)
  #get WKT for the bounding box
  wkt <- st_as_text(st_as_sfc(st_bbox(geom)), digits = 6)
  #fetch occurrences for bounding box
  occ <- occurrence(geometry = wkt) %>%
    st_as_sf(coords = c("decimalLongitude", "decimalLatitude"), crs = 4326)
  #filter using geometry
  occ_filtered <- occ %>%
    filter(st_intersects(geometry, geom, sparse = FALSE)) %>%
    as_tibble() %>%
    select(-geometry)
  #get taxa
  alb_taxa <- occ_filtered %>%
    group_by(phylum, class, order, family, genus, species, scientificName) %>%
    summarize(records = n())
  ```

  </details></li>
  <li><details>
  <summary>How do I convert or obtain separate elements from dates in the data download file (e.g. <code>date_start</code> field)?</summary>
  <br>
  
 The values in `date_start`, `date_mid`, and `date_end` are unix timestamps which have been calculated from the ISO date in the `eventDate` column. We can convert these numerical values to dates using the formula below.

  ```Excel
  =(E2/86400000)+DATE(1970,1,1)
  ```

  If, when you apply this formula, you still see numbers, you will need to set the cell formatting to Date. Once you have dates, you can obtain, e.g. months for seasonal analyses using:
  
  ```Excel
  =MONTH(H2)
  ``` 

  </details></li>
<li><details>
<summary>How do I filter by or obtain trait information for OBIS data (e.g. all benthic organisms)?</summary>
<br>
  
  Currently, it is not possible to filter OBIS data by trait. To do this, we recommend using the traits database of the [World Register of Marine Species](https://www.marinespecies.org/traits/aphia.php?p=attributes). For example, searching by “functional group”, you can specify benthos, plankton, nekton, etc.
  </details></li>
</ul>
