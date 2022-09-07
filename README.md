# Analysis of Student Frequencies at New York Metro Stations

## Abstract
The goal of this project was to analyze best locations at New York metro to target students with advertising for student loan offerings provided by a fintech company. I worked with data provided by the Metropolitan Transportation Authority on turnstiles (entries at metro stations) and fares (metrocard swipes) data and included additional data on geographic location as well as metro lines published by State of New York to provide additional recommendation on metro lines ads. After combining and refining the data, I built an interactive map to visualize and communicate results using HTML output produced with Bokeh.

## Design
Project originates from the EDA course guideline to use mta turnstile data in combination with other datasets. Analyzing metro stations and lines to place ads for specific target groups may enable firms to effectively reach their target audience and boost their sales. Besides looking at absolute entry figures it may provide economically relevant to use relative figures (percentage share of students in all entries at certain stations) to find an appropriate balance between likely high prices for ads at stations with highest absolute numbers and likely lower prices for ads at stations with lower absolute but higher relative numbers. Due to data limitations, CUNY student metrocard swipes and High-School metrocard swipes were used as a proxy for total (prospective) student frequency at different stations/lines.

## Data
Three datasets were used for the analysis:
1)	MTA turnstile contains 4-hourly entries at turnstiles and stations for 2021, in total 11,107,728 records
2)	MTA fares contains weekly swipes of different metrocard categories (e.g. CUNY students) at stations for 2021, in total 24,834 records
3)	NYC Transit Subway Entrance and Exit contains coordinates (longitude & latitude) and line names for different stations, in total 1,868 records

## Algorithms
### Data Preparation and Feature Engineering
Turnstile and fare data was loaded to an SQL database using SQLAlchemy, NYC transit data was loaded via api request. In fare data, percentage shares of CUNY- and High-School-metrocard swipes were calculated for each week. Since fare data contained records by station on a weekly basis only, each record was assigned a corresponding calendar week and merged on turnstile dataset with the latter being preprocessed to contain daily entry sums per station. Coordinate and line data was preprocessed to account for divergent name strings of stations and was subsequently merged on mta turnstile/fare data. The combined dataset was grouped to station & monthly levels and percentage shares of CUNY and High-School metrocards was applied to total entries figure to obtain an approximation of student entries.

### Analysis
The combined dataset was filtered for each CUNY and High-School to show (1) share of top 10 stations of total entries in 2021; (2) top 10 stations by total and %-share; (3) monthly development of top 3 stations by total and %-share; (4) top 10 lines by total and %-share. For line data, frequencies were linearly divided by the number of different lines at each station which may be a limitation to the results on best metro line. Key assumptions include that CUNY frequencies in city areas are representative for general student population in New York, that focus year 2021 is representative for future periods and fare data on metrocard swipes appropriately catches focus groups (CUNY and High-School).

## Tools
    •	NumPy and pandas for data manipulation
    •	Matplotlib and Seaborn for plotting
    •	Bokeh for interactive visualizations
