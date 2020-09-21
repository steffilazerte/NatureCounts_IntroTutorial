# Introduction {#intro1}




[NatureCounts](www.naturecounts.ca) is a website hosted and managed by [Birds Canada](www.birdscanada.org), Canada’s leading scientific non-government organization dedicated to increasing the understanding, appreciation and conservation of wild birds and their habitats . Birds Canada specializes in citizen science long-term monitoring programs using a partnership-based model.  Citizen science has been found to be the most cost-effective way to monitor bird populations across large geographic areas. In Canada, over 16,000 volunteers are currently involved in Birds Canada’s programs. 

Launched in January 2008, Nature Counts  is the first Canadian node of the [Avian Knowledge Network](www.avianknowledge.net). It serves as an online data dissemination portal to facilitate the collection, management and sharing of biological data.  NatureCounts hosts hundreds of datasets, representing well over 100 million occurrences of birds. These include virtually all of Birds Canada’s monitoring initiatives, such as Breeding Bird Atlases, eBird Canada, the Marsh Monitoring Program, Nocturnal Owl Surveys, as well as many other major initiatives to which Birds Canada contributes in some capacity (e.g., Canadian Migration Monitoring Program, Hawk Count and the Raptor Population Index, Monarch Knowledge Network, Breeding Bird Survey, Christmas Bird Count, Project FeederWatch). 

What can you do on the NatureCounts [webportal](www.naturecounts.ca)?

  -	You can explore the data resources of NatureCounts via interactive maps that allow you to view the distribution of bird populations during any time of the year and across a variety of different sources. 

  -	You can obtain and visualize information on long term population trends of Canadian birds.

  -	You can explore an individual species pattern of distribution or the species richness of a location via dynamically generated summary tables and graphs.

  -	Finally, much of the observational data can be downloaded for your own personal research!

## NatureCounts and R {#intro1.1}

The natuecounts R package was create to allow users to directly access and download data from NatureCounts into R. The goal of this online book is to show NatureCounts users how to use the [R](https://www.r-project.org/) statistical programming language  to access, filter, summarize, and visualize naturecounts data. Moving forward, we intend to create more advanced tutorials which explore analytical procedures suitable for various datasets. If you have suggestions for additional content, please let us know by emailing dethier@birdscanada.org

Throughout this book we use fictious and subsets real datasets to illustrate how to access, manage, explore and visualize NaturecCounts data in R. We recommend that you run through the sample code in each chapter with the sample dataset before doing the exercises or using own data. 

## Prerequisites {#intro1.2}

This book assumes that you have a basic understanding of R. We recommend that you become familiar with ['R for Data Science’](http://r4ds.had.co.nz/) by Garrett Grolemund and Hadley Wickham, which covers how to import, visualize, and summarize data in R using the [tidyverse](https://www.tidyverse.org/) collection of R packages. 

## Acknowledgements {#intro1.3}

Some text for this document was adapted from the [NatureCount Webpage](https://www.birdscanada.org/birdmon/default/main.jsp) and the [NatureCounts GitHub](https://github.com/BirdStudiesCanada/naturecounts) repository. The structure of this book follows that of the [Motus R Book](https://beta.motus.org/MotusRBook/index.html). Online [tutorials](https://birdstudiescanada.github.io/naturecounts/articles/index.html) are avaiable for the NatureCounts R-package, which are referenced throughout this document. Users are encourages to review these tutorials for additional examples and more advanced options.  

Many people have contrubuted to the NatureCounts web interface and the R package, including, Denis Lepage, Steffi LaZerte, and Catherine Jardine. The development of the NatureCounts web interface, R package, and accompanying online book were made possible by funding provided by Environment and Climate Change Canada and the generosity of donors to [Birds Canada](https://www.birdscanada.org/give/). Thank you!
