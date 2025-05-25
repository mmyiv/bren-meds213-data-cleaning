## Cleaning Shorebird Survey Data Metadata

This metadata is created as part of coursework for [EDS 213, Databases and Data Management](https://ucsb-library-research-data-services.github.io/bren-eds213/). This class is part of the [Master of Environmental Data Science Program](https://bren.ucsb.edu/masters-programs/master-environmental-data-science), at the UC Santa Barbara Bren School of Environmental Science and Management.

![](https://goodmenproject.com/wp-content/uploads/2019/06/iStock-672774802-1.jpg)

Data were not collected every year at all sites. Studies of the population ecology of these birds included nest-monitoring to determine the timing of reproduction and reproductive success; live capture of birds to collect blood samples, feathers, and fecal samples for investigations of population structure and pathogens; banding of birds to determine annual survival rates; resighting of color-banded birds to determine space use and site fidelity; and use of light-sensitive geolocators to investigate migratory movements.

Data on climatic conditions, prey abundance, and predators were also collected. Environmental data included weather stations that recorded daily climatic conditions, surveys of seasonal snowmelt, weekly sampling of terrestrial and aquatic invertebrates that are prey of shorebirds, live trapping of small mammals (alternate prey for shorebird predators), and daily counts of potential predators (jaegers, falcons, foxes). Detailed field methods for each year are available in the ASDN_protocol_201X.pdf files. All research was conducted under permits from relevant federal, state, and university authorities.

For the original metadata regarding this dataset, please see \`01_ASDN_Readme.txt' at the [EDS 213 Data Repository](https://github.com/UCSB-Library-Research-Data-Services/bren-eds213-data).

### Data and File Overview

#### 1. File List: Repository Structure

```         
├── data
│   ├── processed
│   │   ├── snow_cover.csv
│   │   ├── snow_cover_fixed_MichelleYiv.csv
│   ├── raw
│   │   ├── 01_ASDN_Readme.txt
│   │   ├── ASDN_Daily_species.csv
│   │   ├── ASDN_Snow_survey.csv
├── docs
│   ├── data-cleaning_files/libs
│   │   ├── bootstrap
│   │   │   ├── bootstrap-icons.css
│   │   │   ├── bootstrap-icons.woff
│   │   │   ├── bootstrap.min.css
│   │   │   ├── bootstrap.min.js
│   │   ├── clipboard
│   │   │   ├── clipboard.min.js
│   │   ├── quarto-html
│   │   │   ├── anchor.min.js
│   │   │   ├── popper.min.js
│   │   │   ├── quarto-syntax-highlighting.css
│   │   │   ├── quarto.js
│   │   │   ├── tippy.css
│   │   │   ├── tippy.umd.min.js
│   └── data-cleaning.html
├── .Rprofile
├── .gitignore
├── README.md
├── eds213_data_cleaning_assign_YIVMICHELLE.qmd
└── bren-meds213-data-cleaning.Rproj
```

#### 1. File List: Description

The data folder contains two additional folders for raw and processed data. This folder pertains to the field data of arctic shorebirds described above. The raw folder contains data about snow survey and species presence as it was originally collected, along with the original metadata. The processed folder contains updated .csv files for snow cover with data cleaning and analysis. These procedures will be described in detail below, and work can be seen in the `eds213_data_cleaning_assign_YIVMICHELLE.qmd`, and the process will be described below.

The docs folder contains files that were generated from rendering the visuals and documents from this assignment. They are not related to the data cleaning and analysis process.

The final `eds213_data_cleaning_assign_YIVMICHELLE.qmd` contains the workflow process of cleaning the data to generate a final, cleaned .csv file.

The main steps of cleaning will be detailed here:

-   Checking for non-numeric values (n/a and unk in this case), checking their places in the dataset, and assigning to a real `NA` value.

-   Checking for negative values or values over 100, as all numbers for all cover variables (`snow_cover`, `land_cover`, `water_cover`) should be between 0 and 100. After checking its context in the dataset, these values were turned into `NA`.

-   Converting the cover columns to numeric and checking that all values fell between 0 and 100.

    Then, I checked to ensure that the cover columns (`snow_cover`, `land_cover`, `water_cover`) totaled up to 100 as seen in the `total_cover` column.

-   Therefore, whenever one of the variables was missing (NA value), the other two variables were subtracted from the `total_cover` column (which should always equal 100).

-   Then, I checked to see if all values in the `total_cover` column were between 0-100. As some columns fell outside this range, likely due to typos, I removed those columns from the dataset as it was too ambiguous to try and determine the real values.

-   Finally, I saved the cleaned dataset to a new, cleaned file called `snow_cover_fixed_MichelleYiv.csv`.

#### 2. File relationship

The raw folder contain raw, unprocessed data that was used in the cleaning process document of `eds213_data_cleaning_assign_YIVMICHELLE.qmd`. The output of this file is stored in the processed data folder as `snow_cover_fixed_MichelleYiv.csv`.

#### 3. Additional Related Data

The data used here is part of a greater data set. More data about these can be found at the full metadata described above. These additional data files are housed at the [Arctic Shorebirds Demographics](https://arcticdata.io/catalog/view/doi:10.18739/A2222R68W) page.

-   Arctic_Shorebird_Demographics.xml

-   ASDN_Invert_biomass.csv

-   ASDN_Bird_sexes.csv

-   ASDN_protocol_2010.pdf

-   ASDN_Weather_Hobo.csv

-   ASDN_Bird_nests.csv

-   ASDN_Pred_nests.csv

-   ASDN_Camp_staff.csv

-   ASDN_Weather_snow_manual.csv

-   ASDN_Weather_precip_manual.csv

-   ASDN_protocol_2014.pdf

-   ASDN_Pred_point_counts.csv

-   ASDN_Daily_species_effort.csv

-   ASDN_protocol_2012.pdf

-   ASDN_Lemming_trap.csv

-   ASDN_Camp_info.csv

-   ASDN_Lemming_nests.csv

-   ASDN_Daily_pred_lemm.csv

-   ASDN_Snow_survey.csv

-   ASDN_Bird_captures.csv

-   ASDN_Surface_water.csv

-   ASDN_protocol_2013.pdf

-   ASDN_protocol_2011.pdf

-   01_ASDN_Readme.txt

-   ASDN_Geodata.csv

-   ASDN_Bird_eggs.csv

-   ASDN_Lemming_counts.csv

-   ASDN_Bird_resights.csv

-   ASDN_Daily_species.csv

**Associated Authors include:**

-   Barrow

    -   Rick Lanctot ([richard_lanctot\@fws.gov](mailto:richard_lanctot@fws.gov))

    -   Sarah Saalfeld ([sarah_saalfeld\@fws.gov](mailto:sarah_saalfeld@fws.gov))

-   Burntpoint

    -   Rod Brook ([rod.brook\@ontario.ca](mailto:rod.brook@ontario.ca))

    -   Kim Bennet ([Kim.Bennett\@ontario.ca](mailto:Kim.Bennett@ontario.ca))

    -   Ken Abraham

-   Bylot Island

    -   Joël Bêty ([joel_bety\@uqar.ca](mailto:joel_bety@uqar.ca))

    -   Jean-Francois Lamarre ([jflamarre\@gmail.com](mailto:jflamarre@gmail.com))

-   Cape Krusenstern

    -   Megan Boldenow ([mboldenow\@gmail.com](mailto:mboldenow@gmail.com))

-   Canning River

    -   Stephen Brown ([sbrown\@manomet.org](mailto:sbrown@manomet.org))

    -   David Payer

-   Chaun, Ikpikpuk, Prudhoe

    -   Rebecca Bentzen ([rbentzen\@wcsc.org](mailto:rbentzen@wcsc.org))

    -   Steve Zack

    -   Joe Liebezeit

    -   Martin Robards

-   Churchill

    -   Erica Nol ([ericanol2000\@gmail.com](mailto:ericanol2000@gmail.com))

    -   Nathan Senner ([n.r.senner\@rug.nl](mailto:n.r.senner@rug.nl))

    -   Andrew Johnson

    -   Johanna Perz

    -   Laura Koloski

    -   Laura McKinnon

-   Coats Island

    -   Paul Smith ([PaulAllan.Smith\@ec.gc.ca](mailto:PaulAllan.Smith@ec.gc.ca))

-   Colville

    -   David Ward ([dward\@usgs.gov](mailto:dward@usgs.gov))

-   East Bay

    -   Paul Smith ([PaulAllan.Smith\@ec.gc.ca](mailto:PaulAllan.Smith@ec.gc.ca))

    -   Grant Gilchrist

-   Igloolik

    -   Nicolas Lecomte ([nicolas.lecomte\@umoncton.ca](mailto:nicolas.lecomte@umoncton.ca))

    -   Marie-Andrée Giroux ([marie.a.giroux\@gmail.com](mailto:marie.a.giroux@gmail.com))

-   Lower Khatanga River

    -   Mikhail Soloviev ([mikhail-soloviev\@yandex.ru](mailto:mikhail-soloviev@yandex.ru))

-   Mackenzie Delta

    -   Jennie Rausch ([jennie.rausch\@ec.gc.ca](mailto:jennie.rausch@ec.gc.ca))

    -   Paul Woodard ([paul.woodard\@ec.gc.ca](mailto:paul.woodard@ec.gc.ca))

-   Nome

    -   Brett K. Sandercock ([bsanderc\@ksu.edu](mailto:bsanderc@ksu.edu)): study years 1993-1995, 2010-2014

    -   David B. Lank ([dlank\@sfu.ca](mailto:dlank@sfu.ca)): study years 1996-1998, 2008-2013

    -   Willow English ([willowenglish1\@gmail.com](mailto:willowenglish1@gmail.com)): primary contact for Red-necked Phalarope data.

    -   Eunbi Kwon

    -   Samantha Franks

    -   Rick Lanctot

#### 4. Multiple versions

There is an updated version from from Barrow/Utqiagvik, including corrected and more recent data. The data is housed [here](https://arcticdata.io/catalog/view/doi:10.18739/A2VT1GP7Q).

### Data Specific Information

1.  Number of Variables
    
    10
    
2.  Number of rows

    471141 (including NA rows)

3.  Variable List

    ### Variable Descriptions

    | Variable | Description |
    |----------------------------------------------|--------------------------|
    | **Site** | The 4-letter abbreviation code used by the Arctic Shorebirds Demographics Network to denote the site location where data was collected. |
    | **Year** | The year in which the data point was collected. |
    | **Date** | The full date in which the data point was collected, in the original format it was collected. |
    | **Plot** | Name of study plot on which survey was conducted. |
    | **Location** | The year in which the data point was collected. *(Note: duplicate of "Year")* |
    | **Snow_cover** | Percent cover of snow, including slush. |
    | **Water_cover** | Percent cover of water. |
    | **Land_cover** | Percent cover of exposed land. |
    | **Total_cover** | The total amount of coverage on a plot of snow, water, or land. This number should always be 100, as it is the sum of the Snow_cover, Water_cover, and Land_cover columns. |
    | **Observer** | The personnel abbreviation of the person who collected the data point. |
    | **Notes** | Any additional notes taken by the Observer at the time of data collection. |

4.  Missing Data Codes


All null variables are categorized as NA


5.  Specialized formats

    Nome used or noted aboce.

### Sharing and Access information

**1. Licenses/restrictions placed on the data:**

This work is licensed under the Creative Commons Attribution 4.0 International License. To view a copy of this license, visit <http://creativecommons.org/licenses/by/4.0/>.

**2. Links to publications that cite or use the data:**

-   Chagnon‐Lafortune et al. (2024). A circumpolar study unveils a positive non‐linear effect of temperature on arctic arthropod availability that may reduce the risk of warming‐induced trophic mismatch for breeding shorebirds. Global Change Biology, 30. [doi:10.1111/gcb.17356](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Perkins, Marie et al. (2023). Factors influencing mercury exposure in Arctic-breeding shorebirds. Ecotoxicology, 32, 1062–1083. [doi:10.1007/s10646-023-02708-w](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Lagassé, Benjamin J. et al. (2022). Migratory network reveals unique spatial-temporal migration dynamics of Dunlin subspecies along the East Asian-Australasian Flyway. PLOS ONE, 17, e0270957. [doi:10.1371/journal.pone.0270957](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Clemens Küpper, et al. (2021). Reply to ‘Commentary CeutaOPEN, individual-based field observations of breeding snowy plovers Charadrius nivosus’. [doi:10.32942/osf.io/uqnvf](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Emily L Weiser, et al. (2020). Annual adult survival drives trends in Arctic-breeding shorebirds but knowledge gaps in other vital rates remain. The Condor, 122. [doi:10.1093/condor/duaa026](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Lagassé, Benjamin J, et al. (2020). Dunlin subspecies exhibit regional segregation and high site fidelity along the East Asian–Australasian Flyway. The Condor, 122. [doi:10.1093/condor/duaa054](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Eberhart-Phillips, et al. (2020). CeutaOPEN, individual-based field observations of breeding snowy plovers Charadrius nivosus. Scientific Data, 7. [doi:10.1038/s41597-020-0490-y](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Weiser, Emily L, et al. (2020). Annual adult survival drives trends in Arctic-breeding shorebirds but knowledge gaps in other vital rates remain. The Condor, 122. [doi:10.1093/condor/duaa026](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Weiser, Emily L., et al (2018). Effects of leg flags on nest survival of four species of Arctic‐breeding shorebirds. Journal of Field Ornithology, 89, 287–297. [doi:10.1111/jofo.12264](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Weiser, Emily L., et al. (2018). Life‐history tradeoffs revealed by seasonal declines in reproductive traits of Arctic‐breeding shorebirds. Journal of Avian Biology, 49. [doi:10.1111/jav.01531](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Weiser, Emily L., et al. (2018). Environmental and ecological conditions at Arctic breeding sites have limited effects on true survival rates of adult shorebirds. The Auk, 135, 29–43. [doi:10.1642/auk-17-107.1](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Weiser, Emily L., et al. (2018). Life‐history tradeoffs revealed by seasonal declines in reproductive traits of Arctic‐breeding shorebirds. Journal of Avian Biology, 49. [doi:10.1111/jav.01531](https://github.com/jorb1/bren-meds213-data-cleaning/blob/main)

-   Weiser, Emily L., et al. (2018). Effects of environmental conditions on reproductive effort and nest success of Arctic‐breeding shorebirds. Ibis, 160, 608–623. <doi:10.1111/ibi.12571>

-   Kwon, Eunbi, et al. (2017). Delayed egg‐laying and shortened incubation duration of Arctic‐breeding shorebirds coincide with climate cooling. Ecology and Evolution, 8, 1339–1351. <doi:10.1002/ece3.3733>

**3. Links to other publicly accessible locations of the data:**

No other locations known.

**4. Links/relationships to ancillary data sets:**

-   See above for list of ancillary data sets related to the data used in this analysis. ASDN_Daily_species.csv and ASDN_Snow_survey.csv are the two files processed in the cleaning analysis performed in this repository.

-   ASDN_Daily_species.csv has columns including Site and Observer. These columns are directly referencing these ancillary tables, specifically ASDN_Camp_staff.csv and ASDN_Bird_nests.csv.

-   ASDN_Snow_survey.csv has columns including Site, Observer, and Plot. These columns are directly referencing these ancillary tables, specifically ASDN_Camp_staff.csv and ASDN_Bird_nests.csv.

-   Tables mentioned here can be found at the [Arctic Data Center](https://arcticdata.io/).

**5. Was data derived from another source? If yes, list source(s):**

Data was not derived from another source.

**6. Recommended citation for the project:**

Lanctot, RB, SC Brown, and BK Sandercock. 2017. Arctic Shorebird Demographics Network. NSF Arctic Data Center. <https://doi.org/10.18739/A2222R68W>
