## [ClockPetals Demo](https://va.tech.purdue.edu/vast2017/mc1 "ClockPetals")

## Introduction
ClockPetals is an online visual analytics system designed for traffic analysis. This project was submitted to [2017 IEEE Visual Analytics for Science and Technology (VAST) Challenge Mini-Challenge 1](http://vacommunity.org/VAST+Challenge+2017+MC1). A bit about the VAST challenge: it's an annual IEEE competition event aiming to advancing visual analytics idea, design, and techniques. It usually kick off in late April and ends by mid July.

Each year VAST challenge provides meticulously synthesized dataset and context story to participants from all over the world and asks them to investigate what the data can tell via visual analytics methods. Typically every challenge consists of 2-3 sub challenges (called "mini-challenge") and, maybe, a grand challenge when the mini challenges are connected or in the same context. The investigation result (solution) typically should answer 3-5 questions the challenge asks. For each question, the solution should presents about 5 visual evidence for supporting the patterns/anomalies the investigation finds.

In the summer of 2017 (also in 2016 but another story), I worked with two serial-competitor-and-awardee professors in VAST challenge, along with an undergrad developer, a data scientist PhD (remote),and three visual designers. We competed for two mini challenges in parallel. I was appointed as the team lead to

* manage the design and development iteration. Normally we had 1-2 weekly meetings to report the progress and to discuss/critique the design ideas and their implementation. Since the projects were driven by the solution and the design, we started by exploring and massaging the data in the first couple of weeks. Meanwhile we brainstormed a lot of design ideas. When a design plan including features and visualization forms were determined in the meetings, I setup goals and deadlines for both design and development so that we could present the practical-but-mocked-up progress in the next meeting.

>![Process](https://uploads-ssl.webflow.com/5b43c1ec7ab3d835fb006c5d/5b468b8276d89c85825d1b2b_vast-process.png)
(process flowmap courtesy by one of the designers Wenjie Wu)

* implement and code the design ideas for mini challenge one with the undergrad developer. I architected the tech stack, controlled the versions (OMG I really should've used Git but it was complicated...), and guidelined the code styles. My resolute choice on JavaScript and D3.js over PHP increased the performance and development efficiency indeed.

* morally support the team by organizing team lunch and activities such as canoeing and barbecues.


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
