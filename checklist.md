# Formatting data tables

## Darwin Core Term Checklist for OBIS

There are many Darwin Core terms listed in the [TDWG quick reference guide](https://dwc.tdwg.org/terms/). However, not all these terms are necessary for publishing data to OBIS.

For your convenience, we have created a checklist of all the Darwin Core terms relevant for OBIS data providers. You can reference this list to quickly see which terms are required by OBIS, which data table (Event, Occurrence, eMoF, DNA) they can be found in, and which Darwin Core class each term belongs to. These terms correlate with the [IPT vocabulary mapping](ipt.html#map-your-data-to-darwin-core) you will do when it comes time to publish your dataset. You may notice some terms are accepted in multiple data tables (e.g., Event and Occurrence) - this is because it depends on your dataset structure. If you have an Event Core, you will include some terms that would not be included if you had Occurrence Core. For guidance on specific class terms (e.g., location, taxonomy, etc.), see the [Darwin Core](darwin_core.html#darwin-core-guidelines) section of the manual.

Note that when you publish your dataset on the IPT, if you use a term not listed below it will be an unmapped field and will **not** be published alongside your data. You may still wish to include such fields in your dataset if you are publishing to other repositories, just know that they will not be included in your OBIS dataset. You may include this information either by putting it in the `dynamicProperties` field in JSON format, or putting the information into the [eMoF](format_emof.html). Alternatively, you may have fields that you do not wish to be published and that do not correspond to one of these terms (e.g. personal notes). This is okay - if they are not mapped to one of the terms, that column in your dataset will not be published.

**Table Legend**:

- Terms marked with ^ indicate that the specified term is accepted in the Event or Occurrence table, but preference is that they be recorded in the eMoF table to link with controlled vocabulary
- For the Occurrence table, distinction is made if the term could be used in the core or the extension table
  - x/x = term can be used in either Occurrence core or extension
  - x/- term is recommended only for the Occurrence core
  - -/x term is recommended only for the Occurrence extension

```{r checklist-button, echo=FALSE}
library(downloadthis)
library(webshot)
downloadthis::download_file(
    path = "docs/OBIS-termchecklist.csv",
    output_name = "OBISchecklist",
    output_extension = ".csv",
    button_label = "Download checklist as csv",
    button_type = "default",
    has_icon = TRUE,
    icon = "fa fa-save",
    style = "background-color: #1e74ac; color: white; border: none; padding: 10px 20px; font-size: 16px; border-radius: 5px; margin-top: 5px; margin-bottom: 20px;"
  )
```


| Term | OBIS Required | Term's DarwinCore Class | Event core | Occurrence core | Occurrence extension | eMoF Table | DNA Table |
|---------|-----------|---------|----------|--------|----------|----------|--------|
| eventDate | required |  event |  x | x| |  |  |
| eventID | required | event | x | |x | x |  |
| decimalLatitude | required | location | x | x| |  |  |
| decimalLongitude | required | location | x | x| |  |  |
| occurrenceID | required | occurrence |  | x|x | x | x |
| occurrenceStatus | required | occurrence |  | x|x |  |  |
| basisOfRecord | required | record |  | x|x |  |  |
| scientificName | required | taxon |  | x|x |  |  |
| scientificNameID |  strongly recommended | taxon |  | x|x |  |  |
| DNA_sequence | strongly recommended | dna |  | | |  | x |
| env_broad_scale | strongly recommended | dna |  | | |  | x |
| env_local scale | recommended | dna |  | | |  | x |
| env_medium | strongly recommended | dna |  | | |  | x |
| lib_layout | recommended | dna |  | | |  | x |
| nucl_acid_amp | recommended | dna |  | | |  | x |
| nucl_acid_ext | recommended | dna |  | | |  | x |
| otu_class_appr | recommended | dna |  | | |  | x |
| otu_db | recommended | dna |  | | |  | x |
| otu_seq_comp_appr | recommended | dna |  | | |  | x |
| pcr_primer_forward | strongly recommended | dna |  | | |  | x |
| pcr_primer_name_forward | strongly recommended | dna |  | | |  | x |
| pcr_primer_name_reverse | strongly recommended | dna |  | | |  | x |
| pcr_primer_reference | strongly recommended | dna |  |  | | | x |
| pcr_primer_reverse | strongly recommended | dna |  | | |  | x |
| samp_name | recommended | dna |  | | |  | x |
| samp_vol_we_dna_ext | recommended | dna |  | | |  | x |
| seq_meth | recommended | dna |  | | |  | x |
| sop | recommended | dna |  | | |  | x |
| target_gene | strongly recommended | dna |  | | |  | x |
| target_subfragment | strongly recommended | dna |  | | |  | x |
| day | recommended | event | x | x|  |  |  |
| endDayOfYear | recommended | event | x | x|  |  |  |
| eventType | strongly recommended | event | x | | |  |  |
| eventRemarks | optional | event | x | x|  |  |  |
| eventTime | recommended | event | x | x|  |  |  |
| fieldNotes | optional | event | x | | |  |  |
| fieldNumber | optional | event | x | | |  |  |
| habitat | recommended | event | x | x | | x |  |
| month | strongly recommended | event | x | x|  |  |  |
| parentEventID | required (if exists) | event | x |  |  |  |
| sampleSizeUnit | strongly recommended | event | x1 | x1|  | x |  |
| sampleSizeValue | strongly recommended | event | x1 | x1|  | x |  |
| samplingEffort | strongly recommended | event | x1 | x1|  | x |  |
| samplingProtocol | strongly recommended | event | x1 | x1|  | x |  |
| startDayOfYear | recommended | event | x | | |  |  |
| verbatimEventDate | recommended | event | x | x | |  |  |
| year | strongly recommended | event | x | x| |  |  |
| bed | optional | geologicalContext | x | x|x |  |  |
| earliestAgeOrLowestStage | optional | geologicalContext | x | x|x |  |  |
| earliestEonOrLowestEonothem | optional | geologicalContext | x | x|x |  |  |
| earliestEpochOrLowestSeries | optional | geologicalContext | x | x|x |  |  |
| earliestEraOrLowestErathem | optional | geologicalContext | x | x|x |  |  |
| earliestPeriodOrLowestSystem | optional | geologicalContext | x | x|x |  |  |
| formation | optional | geologicalContext | x | x|x |  |  |
| group | optional | geologicalContext | x | x|x |  |  |
| highestBiostratigraphicZone | optional | geologicalContext | x | x|x |  |  |
| latestAgeOrHighestStage | optional | geologicalContext | x | x|x |  |  |
| latestEonOrHighestEonothem | optional | geologicalContext | x | x|x |  |  |
| latestEpochOrHighestSeries | optional | geologicalContext | x | x|x |  |  |
| latestEraOrHighestErathem | optional | geologicalContext | x | x|x |  |  |
| latestPeriodOrHighestSystem | optional | geologicalContext | x | x|x |  |  |
| lithostratigraphicTerms | optional | geologicalContext | x | x|x |  |  |
| lowestBiostratigraphicZone | optional | geologicalContext | x | x|x |  |  |
| member | optional | geologicalContext | x | x|x |  |  |
| dateIdentified | optional | identification |  | x|x |  |  |
| identificationID | optional | identification |  | x|x |  |  |
| identificationQualifier | recommended | identification |  | x|x |  |  |
| identificationReferences | optional (required for imaging data) | identification |  | x|x |  |  |
| identificationRemarks | recommended | identification |  | x|x |  |  |
| identificationVerificationStatus | optional (required for imaging data) | identification |  | x|x |  |  |
| identifiedBy | optional (required for imaging data) | identification |  | x|x |  |  |
| identifiedByID | optional | identification |  | x|x |  |  |
| typeStatus | optional | identification |  | x|x |  |  |
| continent | strongly recommended | location | x | x|  |  |  |
| coordinatePrecision | strongly recommended | location | x | x|  |  |  |
| coordinateUncertaintyInMeters | strongly recommended | location | x | x|  |  |  |
| country | recommended | location | x | x|  |  |  |
| countryCode | optional | location | x | x|  |  |  |
| county | optional | location | x | x|  |  |  |
| footprintSpatialFit | optional | location | x | x|  |  |  |
| footprintSRS | optional | location | x | x|  |  |  |
| footprintWKT | recommended | location | x | x|  |  |  |
| geodeticDatum | recommended | location | x | x|  |  |  |
| georeferencedBy | optional | location | x | x|  |  |  |
| georeferencedDate | optional | location | x | x|  |  |  |
| georeferenceProtocol | optional | location | x | x|  |  |  |
| georeferenceSources | optional | location | x | x|  |  |  |
| higherGeography | optional | location | x | x|  |  |  |
| higherGeographyID | optional | location | x | x|  |  |  |
| island | optional | location | x | x|  |  |  |
| islandGroup | optional | location | x | x|  |  |  |
| locality | recommended | location | x | x|  |  |  |
| locationAccordingTo | recommended | location | x | x|  |  |  |
| locationID | strongly recommended | location | x | x|  |  |  |
| locationRemarks | recommended | location | x | x|  |  |  |
| maximumDepthInMeters | strongly recommended | location | x | x|  |  |  |
| maximumDistanceAboveSurfaceInMeters | optional | location | x | x|  |  |  |
| maximumElevationInMeters | optional | location | x | x|  |  |  |
| minimumDepthInMeters | strongly recommended | location | x | x| |  |  |
| minimumDistanceAboveSurfaceInMeters | optional | location | x | x|  |  |  |
| minimumElevationInMeters | optional | location | x | x|  |  |  |
| municipality | optional | location | x | x|  |  |  |
| pointRadiusSpatialFit | optional | location | x | x|  |  |  |
| stateProvince | optional | location | x | x|  |  |  |
| verbatimCoordinates | optional | location | x | x|  |  |  |
| verbatimCoordinateSystem | optional | location | x | x|  |  |  |
| verbatimDepth | optional | location | x | x|  |  |  |
| verbatimElevation | optional | location | x | x|  |  |  |
| verbatimLatitude | optional | location | x | x|  |  |  |
| verbatimLocality | optional | location | x | x|  |  |  |
| verbatimLongitude | optional | location | x | x|  |  |  |
| verbatimSRS | optional | location | x | x|  |  |  |
| waterBody | recommended | location | x | x|  |  |  |
| materialSampleID | recommended | materialSample |  | x|x |  |  |
| measurementAccuracy | recommended | measurementOrFact |  | | | x |  |
| measurementDeterminedBy | optional | measurementOrFact |  | | | x |  |
| measurementDeterminedDate | optional | measurementOrFact |  | | | x |  |
| measurementID | recommended | measurementOrFact |  | | | x |  |
| measurementMethod | recommended | measurementOrFact |  | | | x |  |
| measurementRemarks | recommended | measurementOrFact |  | | | x |  |
| measurementType | strongly recommended | measurementOrFact |  | | | x |  |
| measurementTypeID | strongly recommended | measurementOrFact |  | | | x |  |
| measurementUnit | strongly recommended | measurementOrFact |  | | | x |  |
| measurementUnitID | strongly recommended | measurementOrFact |  | | | x |  |
| measurementValue | strongly recommended | measurementOrFact |  | | | x |  |
| measurementValueID | strongly recommended | measurementOrFact |  | | | x |  |
| associatedMedia | recommended | occurrence |  | x|x |  |  |
| associatedReferences | optional | occurrence |  | x|x |  |  |
| associatedSequences | recommended | occurrence |  | x|x |  |  |
| associatedTaxa | optional | occurrence |  | x|x |  |  |
| behavior | optional | occurrence |  | x1|x1 | x |  |
| catalogNumber | recommended | occurrence |  | x|x |  |  |
| disposition | optional | occurrence |  | x|x |  |  |
| establishmentMeans | optional | occurrence |  | x|x |  |  |
| georeferenceVerificationStatus | recommended | occurrence | x | x|  |  |  |
| organismQuantity (preferred over individualCount) | strongly recommended | occurrence |  | x1|x1 | x |  |
| organismQuantityType (preferred over individualCount) | strongly recommended | occurrence |  | x1|x1 | x |  |
| individualCount | recommended | occurrence |  | x1|x1 | x |  |
| lifeStage | optional | occurrence |  | x1|x1 | x |  |
| occurrenceRemarks | recommended | occurrence |  | x|x |  |  |
| otherCatalogNumbers | optional | occurrence |  | x|x |  |  |
| preparations | optional | occurrence |  | x|x |  |  |
| recordedBy | recommended | occurrence |  | x|x |  |  |
| recordedByID | recommended | occurrence |  | x|x |  |  |
| recordNumber | recommended | occurrence |  | x|x |  |  |
| reproductiveCondition | optional | occurrence |  | x1|x1 | x |  |
| sex | optional | occurrence |  | x1|x1 | x |  |
| associatedOccurrences | optional | organsim |  | x|x |  |  |
| associatedOrganisms | optional | organsim |  | x|x |  |  |
| organismID | recommended | organsim |  | x|x |  |  |
| organismName | optional | organsim |  | x|x |  |  |
| organismRemarks | optional | organsim |  | x|x |  |  |
| organismScope | optional | organsim |  | x|x |  |  |
| previousIdentifications | recommended | organsim |  | x|x |  |  |
| accessRights | recommended | record | x | x|  |  |  |
| bibliographicCitation | recommended | record | x | x|  |  |  |
| collectionCode | optional | record | x | x|x |  |  |
| collectionID | optional | record | x | x|x |  |  |
| dataGeneralizations | optional | record | x | x|x |  |  |
| datasetID | recommended | record | x | x|x |  |  |
| datasetName | recommended | record | x | x|x |  |  |
| dynamicProperties | recommended | record | x | x|x |  |  |
| informationWithheld | optional | record | x | x|x |  |  |
| institutionCode | optional | record | x | x|x |  |  |
| institutionID | optional | record | x | x|x |  |  |
| language | recommended | record | x | x|x |  |  |
| license | strongly recommended | record | x | x|x |  |  |
| modified | recommended | record | x | x|x |  |  |
| ownerInstitutionCode | optional | record | x | x|x |  |  |
| references | recommended | record | x | x|x |  |  |
| rightsHolder | recommended | record | x | x|x |  |  |
| type | strongly recommended | record | x | x|x | x |  |
| acceptedNameUsage | recommended | taxon |  | x|x |  |  |
| acceptedNameUsageID | recommended | taxon |  | x|x |  |  |
| higherClassification | recommended | taxon |  | x|x |  |  |
| infraspecificEpithet | recommended | taxon |  | x|x|  |  |
| nameAccordingToID | recommended | taxon |  | x|x |  |  |
| namePublishedInID | optional | taxon |  | x|x |  |  |
| namePublishedInYear | optional | taxon |  | x|x |  |  |
| nomenclaturalCode | optional | taxon |  | x|x |  |  |
| nomenclaturalStatus | optional | taxon |  | x|x |  |  |
| verbatimIdentification | recommended | identification | | x|x | | |
| originalNameUsage | recommended | taxon |  | x|x |  |  |
| originalNameUsageID | recommended | taxon |  | x|x |  |  |
| parentNameUsage | recommended | taxon |  | x|x |  |  |
| parentNameUsageID | recommended | taxon |  | x|x |  |  |
| phylum | recommended | taxon |  | x|x |  |  |
| scientificNameAuthorship | recommended | taxon |  | x|x |  |  |
| specificEpithet | recommended | taxon |  | x|x |  |  |
| subgenus | recommended | taxon |  | x|x |  |  |
| taxonConceptID | optional | taxon |  | x|x |  |  |
| taxonID | optional | taxon |  | x|x |  |  |
| taxonomicStatus | optional | taxon |  | x|x |  |  |
| taxonRank | strongly recommended | taxon |  | x|x |  |  |
| taxonRemarks | recommended | taxon |  | x|x |  |  |
| verbatimTaxonRank | recommended | taxon |  | x|x |  |  |
| vernacularName | recommended | taxon |  | x|x |  |  |
| class | recommended | taxon |  | x|x |  |  |
| family | recommended | taxon |  | x|x |  |  |
| genus | strongly recommended | taxon |  | x|x |  |  |
| kingdom | strongly recommended | taxon |  | x|x |  |  |
| order | strongly recommended | taxon |  | x|x |  |  |


```{r checklist-data, echo=FALSE}
Terms<-c('eventDate','eventID','decimalLatitude','decimalLongitude','occurrenceID','occurrenceStatus','basisOfRecord','scientificName','scientificNameID','DNA_sequence','env_broad_scale','env_local scale','env_medium','lib_layout','nucl_acid_amp','nucl_acid_ext','otu_class_appr','otu_db','otu_seq_comp_appr','pcr_primer_forward','pcr_primer_name_forward','pcr_primer_name_reverse','pcr_primer_reference','pcr_primer_reverse','samp_name','samp_vol_we_dna_ext','seq_meth','sop','target_gene','target_subfragment','day','endDayOfYear','eventRemarks','eventTime','fieldNotes','fieldNumber','habitat','month','parentEventID','sampleSizeUnit','sampleSizeValue','samplingEffort','samplingProtocol','startDayOfYear','verbatimEventDate','year','bed','earliestAgeOrLowestStage','earliestEonOrLowestEonothem','earliestEpochOrLowestSeries','earliestEraOrLowestErathem','earliestPeriodOrLowestSystem','formation','group','highestBiostratigraphicZone','latestAgeOrHighestStage','latestEonOrHighestEonothem','latestEpochOrHighestSeries','latestEraOrHighestErathem','latestPeriodOrHighestSystem','lithostratigraphicTerms','lowestBiostratigraphicZone','member','dateIdentified','identificationID','identificationQualifier','identificationReferences','identificationRemarks', 'identificationVerificationStatus','identifiedBy','identifiedByID','typeStatus','continent','coordinatePrecision','coordinateUncertaintyInMeters','country','countryCode','county','footprintSpatialFit','footprintSRS','footprintWKT','geodeticDatum','georeferencedBy','georeferencedDate','georeferenceProtocol','georeferenceSources','higherGeography','higherGeographyID','island','islandGroup','locality','locationAccordingTo','locationID','locationRemarks','maximumDepthInMeters','maximumDistanceAboveSurfaceInMeters','maximumElevationInMeters','minimumDepthInMeters','minimumDistanceAboveSurfaceInMeters','minimumElevationInMeters','municipality','pointRadiusSpatialFit','stateProvince','verbatimCoordinates','verbatimCoordinateSystem','verbatimDepth','verbatimElevation','verbatimLatitude','verbatimLocality','verbatimLongitude','verbatimSRS','waterBody','materialSampleID','measurementAccuracy','measurementDeterminedBy','measurementDeterminedDate','measurementID','measurementMethod','measurementRemarks','measurementType','measurementTypeID','measurementUnit','measurementUnitID','measurementValue','measurementValueID','associatedMedia','associatedReferences','associatedSequences','associatedTaxa','behavior','catalogNumber','disposition','establishmentMeans','georeferenceVerificationStatus','individualCount','lifeStage','occurrenceRemarks','organismQuantity','organismQuantityType','otherCatalogNumbers','preparations','recordedBy','recordedByID','recordNumber','reproductiveCondition','sex','associatedOccurrences','associatedOrganisms','organismID','organismName','organismRemarks','organismScope','previousIdentifications','accessRights','bibliographicCitation','collectionCode','collectionID','dataGeneralizations','datasetID','datasetName','dynamicProperties','informationWithheld','institutionCode','institutionID','language','license','modified','ownerInstitutionCode','references','rightsHolder','type','acceptedNameUsage','acceptedNameUsageID','higherClassification','infraspecificEpithet','nameAccordingToID','namePublishedInID','namePublishedInYear','nomenclaturalCode','nomenclaturalStatus','originalNameUsage','originalNameUsageID','parentNameUsage','parentNameUsageID','phylum','scientificNameAuthorship','specificEpithet','subgenus','taxonConceptID','taxonID','taxonomicStatus','taxonRank','taxonRemarks','verbatimTaxonRank','vernacularName','eventType','class','family','genus','kingdom','order')

OBISRequired<-c('required','required','required','required','required','required','required','required','strongly recommended','strongly recommended','strongly recommended','recommended','strongly recommended','recommended','recommended','recommended','recommended','recommended','recommended','strongly recommended','strongly recommended','strongly recommended','strongly recommended','strongly recommended','recommended','recommended','recommended','recommended','strongly recommended','strongly recommended','recommended','recommended','strongly recommended','optional','recommended','optional','optional','recommended','strongly recommended','required (if exists)','strongly recommended','strongly recommended','strongly recommended','strongly recommended','recommended','recommended','strongly recommended','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','recommended','optional (required for imaging data)','recommended','optional (required for imaging data)','optional (required for imaging )', 'optional','optional','strongly recommended','strongly recommended','strongly recommended','recommended','optional','optional','optional','optional','recommended','recommended','optional','optional','optional','optional','optional','optional','optional','optional','recommended','recommended','strongly recommended','strongly recommended','optional','optional','strongly recommended','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','optional','recommended','recommended','recommended','optional','optional','recommended','recommended','recommended','strongly recommended','strongly recommended','strongly recommended','strongly recommended','strongly recommended','strongly recommended','recommended','optional','recommended','optional','recommended','recommended','optional','optional','recommended','strongly recommended','recommended','recommended','strongly recommended','strongly recommended','optional','optional','recommended','recommended','recommended','recommended','recommended','optional','optional','recommended','recommended','recommended','optional','recommended','recommended','recommended','optional','optional','optional','recommended','recommended','recommended','optional','optional','optional','recommended','recommended','recommended','optional','recommended','recommended','strongly recommended','recommended','recommended','recommended','recommended','recommended','optional','optional','optional','optional','recommended','recommended','recommended','recommended','recommended','recommended','recommended','recommended','optional','optional','optional','strongly recommended','recommended','recommended','recommended','strongly recommended','recommended','recommended','strongly recommended','strongly recommended','strongly recommended')

DarwinCoreClass<-c('event','event','location','location','occurrence','occurrence','record','taxon','taxon','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','dna','event','event','event','event','event','event','event','event','event','event','event','event','event','event','event','event','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','geologicalContext','identification','identification','identification','identification','identification','identification','identification','identification','identification','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','location','materialSample','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','measurementOrFact','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','occurrence','organsim','organsim','organsim','organsim','organsim','organsim','organsim','record','record','record','record','record','record','record','record','record','record','record','record','record','record','record','record','record','record','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','taxon','event','taxon','taxon','taxon','taxon','taxon')

Event<-c('x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x',' ',' ',' ',' ','')
Occurrence <-c('x','x','x','x','x','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x','x','x','x',' ',' ',' ','x',' ','x','x','x','x',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x',' ','x','x','x','x','x')

eMoF<-c(' ','x',' ',' ','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x',' ',' ','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ','x',' ',' ',' ',' ','x','x',' ','x','x',' ',' ',' ',' ',' ',' ','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ')

DNA<-c(' ',' ',' ',' ','x',' ','x',' ',' ','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ',' ')

checklist<- as.data.frame(cbind(Terms,OBISRequired,DarwinCoreClass,Event,Occurrence,eMoF,DNA))

```

```{r checklist, echo=FALSE}
library(webshot)
DT::datatable(checklist, extensions = 'Buttons', options = list(pageLength = 100, dom = 'Bfrtip', buttons = c('copy', 'csv', 'excel', 'pdf')))

reactable::reactable(checklist,sortable=F,filterable=T, searchable=T, pagination=F,highlight=T, resizable=T,
          columns = list(
            OBISRequired = reactable::colDef(
                name="OBIS Required",
              style = function(value) {
                color <- NA
                if (value == "required") {
                  color <- "#8B0000"
                } else if (value == "strongly recommended") {
                  color <- "#006600"
                } else if (value == "recommended") {
                  color <- "#003366"
                } 
                else if (value == "optional") {
                  color <- "#FF6600"
                }
                list(color = color, fontWeight = "bold")
              }
              )
            )
          )

```
