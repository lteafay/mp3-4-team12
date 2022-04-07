# Mini-Project 2

# Overview

In this mini-project, you will analyze multiple data sources, including the Environmental Protection Agency's Toxic Release Inventory, recent US Census data on race/ethnicity, health indicators, and historic redlining maps to profile a "fenceline community" in the United States. Fenceline communities are neighborhoods in close proximity to high-risk chemical facilities, and are often sites of environmental racism and other environmental justice concerns. Your report, written in RMarkdown, will include visualizations, maps, text, and images that convey the kinds of risks individuals in these communities are exposed to and the extent to which certain demographics are disproportionately exposed to those risks. Every standard we have covered in this course will be practiced in this final assignment.

# Learning Goals

* Navigate different forms of data documentation
* Access data from APIs
* Join and glean insights from multiple data tables
* Produce both point-based and polygon maps of geospatial data
* Understand the complexities of layering data recorded at different geographic scales
* Communicate data findings in writing and graphics
* Evaluate the ethical dimensions of data resources

# Detailed Instructions

## Get to know the Data Sources

1. Watch:

[![Toxic Release Inventory](http://img.youtube.com/vi/Fqjh6t6Hx6s/0.jpg)](http://www.youtube.com/watch?v=Fqjh6t6Hx6s)

[![TRI for Communities](http://img.youtube.com/vi/Hj3yGpe_s-8/0.jpg)](http://www.youtube.com/watch?v=Hj3yGpe_s-8)

2. Read about the Toxic Release Inventory Program [here](https://www.epa.gov/toxics-release-inventory-tri-program/what-toxics-release-inventory).

3. **Very Important**: Read Factors to Consider [memo] (https://www.epa.gov/system/files/documents/2022-02/factorstoconsider_approved-by-opa_1.25.22-copy.pdf)

4. Review the [data documentation](https://www.epa.gov/system/files/documents/2021-10/tri-basic-data-file-documentation-ry2020_100721.pdf). Specifically, the data dictionary for this dataset spans pages 5-18. To help you make sense of this data, I will note that the unit of observation in this dataset is a certain chemical release at a particular facility. If a facility reports on more than one chemical, that facility will appear multiple times in the dataset (once for each chemical reported). This means both the facility ID and the chemical ID are needed to uniquely identify each row.  

5. Review the About text for the [CDC's Places Dataset](https://chronicdata.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Census-Tract-D/cwsq-ngmh), and specifically the [Definitions](https://www.cdc.gov/places/measure-definitions/health-outcomes/index.html) the the data's health outcome measures. 

6. Review the [Mapping Inequality Project](https://dsl.richmond.edu/panorama/redlining/#loc=5/39.1/-94.58&text=intro). 

## Select and Research a US Fenceline Community

Some of you may know of examples of current or historic fenceline communities in the US, and others may wish to learn more about those communities. Here are some resources for researching fenceline communities:

* [Life at the Fenceline](https://ej4all.org/life-at-the-fenceline)
* [WHO’S IN DANGER? Race, Poverty, and Chemical Disasters](https://comingcleaninc.org/assets/media/images/Reports/Who's%20in%20Danger%20Report%20FINAL.pdf)

Ultimately, you should select one US **county** for your analysis for which we have [HOLC Maps](https://dsl.richmond.edu/panorama/redlining/#loc=5/39.1/-94.58&text=downloads) available. Read up about that county online. If you'd like to run your selected county by me, please feel free to do so. 

## Set up your environment

1. In RStudio, `File` > `New Project` > `Version Control` > `Git` and then copy the URL to this repo. Open `fenceline_analysis.Rmd` and add your group member's names to the header (lines 5, 7, and 9). 
2. Navigate to the [TRI Basic Data Files](https://www.epa.gov/toxics-release-inventory-tri-program/tri-basic-data-files-calendar-years-1987-present), and download the 2020 file for the state your county is located in. 
3. Move the CSV file into the `dataset` folder on your local machine. **Note that only one student in your group needs to do this.** The dataset can be pushed to other members of your group.
4. In `fenceline_analysis.Rmd`, read the CSV file you just downloaded into a data frame. Be sure to use a descriptive variable name for your data frame.
5. Install the Tidy Census package in `R` using:

* `install.packages("devtools")`
* `install.packages("remotes")`
* `remotes::install_github("walkerke/tidycensus")`.

6. Create an API Key for accessing census data [here](https://api.census.gov/data/create_success.html). The key will be emailed to you, and you must activate it with the link you receive in your email. **NOTE: It may take several minutes to activate. If you click on the link in your email, and it doesn't work, try again in a bit.** After activating your census key, enter the following into your console, replacing `KEY_HERE` with your census key. 

```
census_api_key("KEY_HERE", 
               overwrite = FALSE, 
               install = TRUE)
```

## Wrangle and Visualize the Data for the Fenceline Community

Follow the commented instructions in `fenceline_analysis.Rmd` to produce tables, plots, and maps for your community. Note that the steps in this file provide the baseline of computation you should complete for this final project. While not a requirement of the assignment, feel free to extend this project in whatever way you choose by adding additional plots, additional maps, or importing and visualizing additional data. 

## Write report

1. In 400-500 words, you should write up your findings:
  * Paragraph 1: Introduce the fenceline community
  * Paragraph 2: Report on findings from your analysis.
  * Paragraph 3: Summarize the key takeaway from your analysis and describe at least one ethical concern we should consider when analyzing this data. As a reminder of our ethics framework for this course:
    * What assumptions and commitments informed the design of these datasets?
    * Who has had a say in data collection and analysis regarding these datasets? Who has been excluded?
    * What are the benefits and harms of these datasets, and how are they distributed amongst diverse social groups?
2. Style your report. You may assign headers, fold code, add a table of contents, add images, etc. Be sure to cite any external sources if applicable. Knit your document. 

## Record standards and submit assignment

1. Open `standards.Rmd`, and under each heading, indicate how the work you completed for this project demonstrated fluency in that standard. Just 1-2 sentences per standard!
2. When you are done, you should save both .Rmd files, knit the documents, commit changes, and then push changes back to GitHub. That's it for submission. You don't need to submit anything on Moodle. 

# Evaluation 

You will be evaluated on the extent to which your mini-project demonstrates fluency in the following course learning dimensions:

* Pivoting Data
  * Have you successfully reshaped a data frame longer?
  * Have you successfully reshaped a data frame wider?
* Joining Data
  * Have you successfully joined two tables for further analysis?
* Acquiring API Data
  * Have you constructed a URL with query parameters for acquiring desired API data?
* Point Mapping
  * Have you produced maps that plot points by latitude and longitude?
  * Have you demonstrated effective binning when coloring points?
* Polygon Mapping
  * Have you successfully imported a shapefile?
  * Have you produced maps that plot polygons?
  * Have you demonstrated effective binning when coloring polygons?

You may also layer in any learning dimensions evaluated in the previous Mini-Project. 

