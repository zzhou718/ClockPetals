## [Demo](https://va.tech.purdue.edu/vast2017/mc1 "ClockPetals") - **2017 IEEE VAST Challenge Multi-Challenge Award for Aesthetic Design**

## Introduction
This project was submitted to [2017 IEEE Visual Analytics for Science and Technology Challenge Mini-Challenge 1](http://vacommunity.org/VAST+Challenge+2017+MC1).

## Simplified Problem Statement
### Context
The synthetic data came from the vehicle sensors installed at major visiting sites, road conjunctions, entrances, and gates in a fictional natural perserve park. Each vehicle that visited and **entered** the park would be assigned a unique <em>car ID</em>. The sensor would record the <em>car ID</em> and the <em>timestamp</em> when the vehicle passed by the sensor. So, each vehicle passed by a sensor would generate a row of record in the dataset. The dataset contained 170,000+ entries over 13 months. 

### Data

* A 200 x 200 bitmap 

![park map](https://va.tech.purdue.edu/vast2017/mc1/original_data_from_vast/Lekagul%20Roadways.bmp). 

White pixels for the roads and black pixels for the park land. All the sensor locations were tagged by pixel in colors and labeled accordingly. Map description can be found [here](https://va.tech.purdue.edu/vast2017/mc1/original_data_from_vast/Lekagul%20Preserve%20Description.docx).

* Sensor data in CSV format. 

Same vehicle entered the park multiple times maintained the <em>car ID</em>. There were seven types of vehicles in total. Data description can be found [here](https://va.tech.purdue.edu/vast2017/mc1/original_data_from_vast/Data%20Descriptions%20for%20MC1%20v2.docx).

|Timestamp|car-id|car-type|gate-name|
|---|---|---|---|
|2015-05-01 00:15:13|20151501121513-39|2|entrance4|
|2015-05-01 00:32:47|20151501121513-39|2|entrance2|
|2015-05-01 01:12:42|20151201011242-330|5|entrance0|
|2015-05-01 01:14:22|20151201011242-330|5|general-gate1|
|2015-05-01 01:17:13|20151201011242-330|5|ranger-stop2|
|2015-05-01 01:20:36|20151201011242-330|5|ranger-stop0|
|2015-05-01 01:24:11|20151201011242-330|5|general-gate2|
|2015-05-01 01:46:16|20151201011242-330|5|entrance2|
|2015-05-01 01:55:25|20155501015525-264|1|entrance0|
|2015-05-01 01:56:53|20155501015525-264|1|general-gate1|
|2015-05-01 01:59:27|20155501015525-264|1|ranger-stop2|
|2015-05-01 02:02:27|20155501015525-264|1|ranger-stop0|
|2015-05-01 02:05:39|20155501015525-264|1|general-gate2|

## Data visualization design

### Preprocessing
* A Python module to process the bitmap park map to
  * clean the grey noises;
  * enlarge the map for human reading.
* Imported the data to MySQL database and restructured to four tables.
  * A table with all records, adding index, total times of visit, and the temporal order of each visit.
  * A table compressed the visits from the same vehicle, showing total number of records, earliest and latest record time, and total times of visit.
  * A table with rows showing each visit segmenet based on temporal order.
  * A table specifically with rows indicating the duration of vehicles staying on camping sites.
  
### Design
The design ideas and iterations can be found [here](https://va.tech.purdue.edu/vast2017/presentation/Purdue-Zhou-Tang-Wu-Multi-final.pptx) or [here](https://vimeo.com/242499465).

### [Finding](http://www.cs.umd.edu/hcil/varepository/VAST%20Challenge%202017/challenges/Mini-Challenge%201/entries/Purdue%20University/)

## License
This document is licensed under the [Creative Commons Attribution Share Alike 4.0 International](https://choosealicense.com/licenses/cc-by-sa-4.0/), and the underlying source code used to create this document is licensed under the [MIT license](LICENSE.md).
