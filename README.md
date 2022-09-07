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
    • NumPy and pandas for data manipulation
    • Matplotlib and Seaborn for plotting
    • Bokeh for interactive visualizations
    
![image](https://user-images.githubusercontent.com/98846184/188969189-b663fcbd-a8b9-4e3b-9afe-524b5d029ff9.png) ![image](https://user-images.githubusercontent.com/98846184/188969208-1528f21e-284f-4785-b0b5-38bb97e1ef00.png)

![image](https://user-images.githubusercontent.com/98846184/188969268-c5a84040-ae27-45d5-80f4-f7f92abb9088.png)

![image](https://user-images.githubusercontent.com/98846184/188969284-ff5f5446-db2f-4e6d-8210-6aacbc8580ae.png)

![image](https://user-images.githubusercontent.com/98846184/188969298-f43a6e24-6408-4bb0-b764-47a75377c088.png)

![image](https://user-images.githubusercontent.com/98846184/188969310-6a0d38df-e560-434a-a205-4af5688f5cb1.png)

![image](https://user-images.githubusercontent.com/98846184/188969323-537a3dff-fb1e-4388-a58a-505f460a41c7.png)

![image](https://user-images.githubusercontent.com/98846184/188969333-86d0c19e-14dd-4f96-9cb5-818b14800f70.png)

![image](https://user-images.githubusercontent.com/98846184/188969338-0327adbf-7c95-41b3-8b6b-56c4284ab0b3.png)

![image](https://user-images.githubusercontent.com/98846184/188969345-3e33c88f-38ec-43ab-86aa-9825d0e98518.png)
