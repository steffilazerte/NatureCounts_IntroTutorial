# Downloading and Filtering Data {#Dowload4}



This chapter jumps right into downloading NatureCounts data, which builds directly on the skills developed in [Chapter 3](#Data3). 

## Downloading NatureCounts data {#Dowload4.1}

Open access collections are available for download without a username/password, however, we encourage you to [sign up](https://www.birdscanada.org/birdmon/default/register.jsp) for a **free** account. 

Here we demonstrate how to download the Ontario Whip-poor-will collection (WPWI), since it is Open Access (Level 5) and contains relatively few records (nrecords = 3012).  Click [here](https://www.birdscanada.org/birdmon/default/datasets.jsp?code=WPWI) for more information on this dataset.    

```r
WPWI1<-nc_data_dl(collections="WPWI", username = "sample", info="test data download")
```
You should now see a copy of the WPWI collection in the Environments window (upper right panel of RStudio). 
Notice in the code that `info` needs to be provided. This is a short description of reason for the download. This does not need to be specified when using the `nc_count` function.

To access Level 3 or 4 collections you must [sign up](https://www.birdscanada.org/birdmon/default/register.jsp) for a **free** account and request permission from the data custodian. For a complete list of datasets and access level, visit the [NatureCounts datasets](https://www.birdscanada.org/birdmon/default/datasets.jsp) page or use the `meta_collection()` function. Here you can brows information on each dataset prior to requesting access. 

To make a data request, use the NatureCounts [Download Data query tool](https://www.birdscanada.org/birdmon/default/searchquery.jsp).  For step-by-step visual instructions, we encourage you to watch: [NatureCounts: An Introductory Tutorial](link to be provided). You will receive an email confirmation when your request has been approved, which will contain your `request_id`. This number will be used to download your newly acquired dataset into R. There is also a build in function that allows you to check the status of your request and retreive your `request_id`: 


```r
nc_requests(username="sample")
```

Here is sample code to download Access Level 3 or 4 data: 

```r
#This code is not functional and is here to serve as a structural example. You will need to insert your collection, request_id, username, and info in the code chunk below to make this work. 

my_data <- nc_data_dl(collections = "CBC",
                      request_id = 000000, username = "USER",
                      info = "MY REASON")
```
**Note: if you applied filters to the web portal data request (e.g., species, region, year), you will only receive the subset of the dataset you requested.** 

## Applying Filters {#Dowload4.2}

The filters applied in [Chapter 3](#Data3) when using the `nc_count` view function are also used for the `nc_data_dl` download function. Again, these options include: `collections`, `project_id`, `species`, `years`, `doy` (day-of-year), `region`, and `site_type`. The users may also wish to specify which fields/columns to return using the `field_set` and `fields` options in the `nc_data_dl` function. For help with this feature, see the github article ['Selecting columns and fields to download'](https://birdstudiescanada.github.io/naturecounts/articles/selecting-fields.html).   

Please review the resources provided on [filter metadata](#Data3.5) prior to proceeding. 

The users can specify up to 3 filter options in the download process and should try to limit redundancies in filters. In most cases, one of these options will be `collections`, since authorization is given independently for each dataset (i.e., collection). If the user chooses to select `species`, then only collections the user has *authorization* to access will be used to retrieve species-specific data. This differs from the `nc_count` function, which by default shows you *all* the records available in each collection. 

## Examples and Exercises {#Data4.3}

Here are a few examples and exercise for you to work through to become familiar with the `nc_data_dl` function.

*Example 1*: We will use the Ontario Whip-poor-will collection (WPWI) again for this example. After reviewing the online material, [here](https://www.birdscanada.org/birdmon/default/datasets.jsp?code=WPWI), you notice that the main survey ran from 2010 to 2012, but that additional surveys were conducted between 2009 and 2013. For your research, you only want data collected during the main survey window. Futher, the survey was Ontario-wide, but most effort and records are from southern Ontario. Let's further limit the data to those collected south of the Canadian Shield, which is approximated with [BCR](http://nabci-us.org/assets/images/bcr_map2.jpg) 13. 

 

```r
WPWI_filter<-nc_data_dl(collections="WPWI", years=c(2010, 2012), region=list(bcr="13"), username = "sample", info="test data download")
```
You will notice that the number of records in the filtered WPWI download (WPWI_filter = 754) is substantially less than the number of records in the full dataset (WPWI = 3012)

*Example 2*: Rather than using BCR 13 to approximate the study area, you are interested in just looking at records collected on the [Bruce Peninsula](https://en.wikipedia.org/wiki/Bruce_Peninsula) for the full time period. You decide to use [spatial data to filter observations](https://birdstudiescanada.github.io/naturecounts/articles/region-spatial.html). Specifically, you create a [bounding box](https://birdstudiescanada.github.io/naturecounts/articles/region-codes.html), using coordinated from Google Maps which reflects latitude and longitude limits to extract these data. 


```r
WPWI_bb<-nc_data_dl(collections="WPWI", region = list(bbox = c(left = -81.7, bottom = 44.5, 
                                right = -80.9, top = 45.3)), username = "sample", info="test data download")
```
You will notice there are now even fewer observation records (WPWI_bb = 72)

*Exercise 1*:  You (user "sample") are from the Northwest Territories and interested in learning more about breeding birds in your region. First, you identify the NatureCounts dataset most suitable for this exercise using the 'nc_count' function. Next, you decide to focus your download to only include Blackpoll Warbler data collected over the past 5 years (2015-20). How many observation records did you download? 

Answer: BBS50-CAN, 75

*Exercise 2*: You (user "sample") are birding in the 	*Beaverhill Lake* Important Bird Area (iba) in May. You think you hear a Bobolink! You are curious if this species is often detected here in the [month of May](https://www.esrl.noaa.gov/gmd/grad/neubrew/Calendar.jsp). You choose to download the records you have authorization to freely access from NatureCounts. How many observation records did you download? What year are these records from?    

Answer: 2 (or 3 if you including Feb 29 in the doy calculation), 1988 


