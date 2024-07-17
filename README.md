# Twin Cities Station Mapping


## Research Question

Which demographic groups are impacted by light rail openings in the
United States?

## Research Context

We’re focused on the “Twin Cities”, Minneapolis and St. Paul, Minnesota
and the impact of the opening of the METRO Blue and METRO Green lines.

Timeline: 2000-2008

Hypothesis: Light rail openings decrease the pollution around stations

- Reasoning: While light rail openings gather commuters, only two of the
  stations have parking, so on average, the net PM2.5 pollution should
  in theory be lower. In addition, many of these commuters are electing
  to use the light rail instead of their own transportation, further
  contributing to a reduction in PM2.5

- Confounding Factors:

  - Power Plants

  - Recycling Centers

  - Refineries

  - Factories

  - Heating Plants

  - Paper Mills

  - Meteorological Factors

  - Local/Federal/State Policies

``` r
library("knitr")
figure1 <- read.csv("Sources of Pollution - Twin Cities - Sheet1 (2).csv")
kable(figure1)
```

| Factories                                                | Notes                                                                   | Location                                   |
|:---------------------------------------------------------|:------------------------------------------------------------------------|:-------------------------------------------|
| Northern Metal Recycling, Becker, MN                     | Known for past violations related to particulate emissions.             | North Minneapolis                          |
| Flint Hills Resources Line Bend Refinery, Rosemount, MN  | Major source of industrial emissions, including various air pollutants. | Rosemount                                  |
| Xcel Energy’s Allen S. King Plant, Bayport, MN           | A coal-fired power plant contributing to emissions.                     | St. Croix River                            |
| Gerdau Ameristeel, St Paul, MN                           | A steel production facility scrutinized for particulate emissions.      | St. Paul                                   |
| 3M Cottage Grove                                         | Produces various chemicals, emitting VOCs and other pollutants          | Cottage Grove                              |
| Hennepin Energy Recovery Center (HERC)                   | A waste-to-energy facility known for emissions from burning waste.      | Minneapolis                                |
| Koch Industries (Flint Hills Resources), Minneapolis, MN | Another significant contributor from its refining operations.           | Rosemount                                  |
| Xcel Energy High Bridge Plant, St Paul, MN               | A natural gas-fired power plant contributing to air pollutants.         | St. Paul                                   |
| University of Minnesota Heating Plant, Minneapolis, MN   | Emits pollutants from burning fuel for campus energy needs.             | Minneapolis                                |
| Federal Premium Ammunition, Anoka, MN                    | Ammunition manufacturing contributing to localized air pollution.       | Anoka                                      |
| Certain Teed Corporation, Shakopee, MN                   | Produces building materials, contributing to emissions.                 | Shakopee                                   |
| UPM Blandin Paper Mill, Grand Rapids, MN                 | Paper production conributing to air emissions.                          | Grand Rapids (nearby the Twin Cities area) |

## Green & Blue Line Stations

Below is a list of all 37 stations for the METRO Green and Blue Lines.

``` r
figure2 <- read.csv("Twin Cities Stations - Sheet1.csv")
kable(figure2)
```

| Stations                             | Opening.Dates     | Address                                                                                               | Parking |
|:-------------------------------------|:------------------|:------------------------------------------------------------------------------------------------------|:--------|
| 10th Street                          | June 14, 2014     | Keefe Co. Parking 10th Street Lot 215 E 10th St Downtown St Paul, MN 55101                            | FALSE   |
| 30th Avenue                          | December 4, 2004  | 8100 30th Avenue South Bloomington, Minnesota                                                         | TRUE    |
| 38th Street                          | June 26, 2004     | 2902 38th Street East Minneapolis, Minnesota                                                          | FALSE   |
| 46th Street                          | June 26, 2004     | 3660 46th Street East Minneapolis, Minnesota                                                          | FALSE   |
| 50th Street / Minnehaha Park         | June 26, 2004     | 5010 Minnehaha Avenue Minneapolis, Minnesota                                                          | FALSE   |
| American Boulevard                   | December 12, 2009 | 34th Avenue South & East American Boulevard Bloomington, Minnesota                                    | FALSE   |
| Bloomington Central                  | December 4, 2004  | 8101 31st Avenue South Bloomington, Minnesota                                                         | FALSE   |
| Capitol / Rice Street                | June 14, 2014     | 130 University Avenue West Saint Paul, Minnesota                                                      | FALSE   |
| Cedar-Riverside                      | June 26, 2004     | 613 15th Avenue South Minneapolis, Minnesota                                                          | FALSE   |
| Central                              | June 14, 2014     | 56 Fifth Street East Saint Paul, Minnesota                                                            | FALSE   |
| Dale Street                          | June 14, 2014     | 616 University Avenue West (Eastbound) 641 University Avenue West (Westbound) Saint Paul, Minnesota   | FALSE   |
| East Bank                            | June 14, 2014     | 551 Washington Avenue Minneapolis, Minnesota                                                          | FALSE   |
| Fairview Avenue                      | June 14, 2014     | 1863 University Avenue West Saint Paul, Minnesota                                                     | FALSE   |
| Fort Snelling                        | June 26, 2004     | 6053 Minnehaha Avenue Fort Snelling, Minnesota                                                        | TRUE    |
| Franklin Avenue                      | June 26, 2004     | 1808 Franklin Avenue East Minneapolis, Minnesota                                                      | FALSE   |
| Government Plaza                     | June 24, 2004     | 352 South 5th Street Minneapolis, Minnesota                                                           | FALSE   |
| Hamline Avenue                       | June 14, 2014     | 1324 University Avenue West (Eastbound) 1359 University Avenue West (Westbound) Saint Paul, Minnesota | FALSE   |
| Lake Street / Midtown                | June 26, 2004     | 2310 Lake Street East Minneapolis, Minnesota                                                          | FALSE   |
| Lexington Parkway                    | June 14, 2014     | 1100 University Avenue West (Eastbound) 1117 University Avenue West (Westbound) Saint Paul, Minnesota | FALSE   |
| Mall of America                      | December 4, 2004  | 8240 24th Avenue South Bloomington, Minnesota                                                         | FALSE   |
| Nicollet Mall                        | June 26, 2004     | 35 South 5th Street Minneapolis, Minnesota                                                            | FALSE   |
| Prospect Park                        | June 14, 2014     | 319 29th Avenue Minneapolis, Minnesota                                                                | FALSE   |
| Raymond Avenue                       | June 14, 2014     | 2305 University Avenue West Saint Paul, Minnesota                                                     | FALSE   |
| Robert Street                        | June 14, 2014     | 613 Robert Street North Saint Paul, Minnesota                                                         | FALSE   |
| Saint Paul Union Depot               | June 14, 2014     | 214 Fourth Street East Saint Paul, Minnesota United States                                            | FALSE   |
| Snelling Avenue                      | June 14, 2014     | 1572 University Avenue West (Eastbound) 1595 University Avenue West (Westbound) Saint Paul, Minnesota | FALSE   |
| Stadium Village                      | June 14, 2014     | 2301 University Avenue Minneapolis, Minnesota                                                         | FALSE   |
| Target Field                         | November 14, 2009 | 5th Street & 3rd Avenue North Minneapolis, Minnesota                                                  | FALSE   |
| Terminal 1 - Lindbergh               | December 4, 2004  | 6450 Glumack Drive Fort Snelling, Minnesota                                                           | FALSE   |
| Terminal 2 - Humphrey                | December 4, 2004  | 7115 Humphrey Drive Fort Snelling, Minnesota                                                          | FALSE   |
| U.S. Bank Stadium                    | June 26, 2004     | 429 Park Ave South Minneapolis, Minnesota                                                             | FALSE   |
| VA Medical Center                    | June 26, 2004     | 5504 Minnehaha Avenue Fort Snelling, Minnesota                                                        | FALSE   |
| Victoria Street                      | June 14, 2014     | 844 University Avenue West (Eastbound) 875 University Avenue West (Westbound) Saint Paul, Minnesota   | FALSE   |
| Warehouse District / Hennepin Avenue | June 26, 2004     | 23 North 5th Street Minneapolis, Minnesota                                                            | FALSE   |
| West Bank                            | June 14, 2014     | 275 Cedar Avenue Minneapolis, Minnesota                                                               | FALSE   |
| Western Avenue                       | June 14, 2014     | 358 University Avenue West (Eastbound) 401 University Avenue West (Westbound) Saint Paul, Minnesota   | FALSE   |
| Westgate                             | June 14, 2014     | 2646 University Avenue West (Eastbound) 2671 University Avenue West (Westbound) Saint Paul, Minnesota | FALSE   |

## Station Information

This code reads the data from csv files we created that contains the
names of each station . The METRO Blue and Green lines in total have 37
stations. This file has the name of each station, their addresses,
opening dates, and whether or not they have parking.

``` r
library("tidyverse")
library("ggmap") 

station_data <- read.csv("Twin Cities Stations - Sheet1.csv") %>%
  mutate(Station2=paste(Stations, "Station Metro Transit, Minnesota"))
```

This next segments use a Google API key in order to get the locations of
each station of the light rail in latitude/longitude coordinates, then
fixes a few select points where the Google API failed to get a precise
location.

``` r
register_google(key = "GoogleAPIKey", write = TRUE)

addr.geo <- mutate_geocode(station_data, location = Station2, output = "latlona")
```

``` r
geo <- addr.geo %>%
  mutate(lat2 = ifelse(address=="bloomington, mn, usa", 44.85639, lat)) %>%
  mutate(lon2 = ifelse(address=="bloomington, mn, usa", -93.22628, lon)) %>%
  mutate(lat2 = ifelse(address=="minnesota, usa", 44.95648, lat2)) %>%
  mutate(lon2 = ifelse(address=="minnesota, usa", -93.17874, lon2)) %>%
  mutate(lat2 = ifelse(Station2=="Western Avenue station Metro Transit, Minnesota", 44.95586, lat2)) %>%
  mutate(lon2 = ifelse(Station2=="Western Avenue station Metro Transit, Minnesota", -93.11708, lon2))
```

## Plotting the Stations

This next code segment plots each of the station locations (in
latitude/longitude) we extracted in the previous stage

``` r
library("terra")
geo <- read.csv("stations_with_locations.csv")

sample_coords <- cbind(geo$lon2, geo$lat2)
lr_stations <- vect(sample_coords)
crdref <- "+proj=longlat +datum=WGS84"
pts <- vect(sample_coords, crs=crdref)
plot(pts)
```

![](README_files/figure-commonmark/unnamed-chunk-6-1.png)

## Plotting the Stations (Part 2)

This code chunk displays the station locations on top of a real map with
a 500m buffer circle around each station location. These buffers and
their sizes are to help to later extract the average PM2.5 and control
data for each of the stations individually while limiting the influence
of potential other sources of PM2.5 as well as overlap with other
stations. In addition, these buffers are necessary to get an average
reading of all the data near the station rather than relying on a single
point, which could lead to outliers.

``` r
library("terra")
library("maptiles")
geo <- read.csv("stations_with_locations.csv")

pts_buffer <- buffer(pts, width = 500) # Width is measured in meters
plot(pts_buffer)
```

![](README_files/figure-commonmark/unnamed-chunk-7-1.png)

``` r
#writeVector(pts_buffer, "Station_Buffers.shp")

tc_lr <- vect("lr_1km_buff/lr_1km_buff.shp")
tc_lr_line <- aggregate(tc_lr, dissolve = TRUE)
lr_project <- project(tc_lr_line, "+proj=longlat + ellps = WGS84 +datum = WGS84 + nodefs")

lrc <- centroids(lr_project, inside = FALSE)

pts_buffer1 <- buffer(lrc, width = 10000)
extent <- buffer(pts, width = 600)

bg <- get_tiles(ext(extent))
plot(bg)
points(pts)
lines(pts_buffer1, col = "blue")
lines(pts_buffer, col = "red")
```

![](README_files/figure-commonmark/unnamed-chunk-7-2.png)

## Find Sources of Pollution near Light Rail Routes and its Addresses

This file has the name of each factory, their addresses, opening dates,
and whether or not they have parking.

``` r
library("tidyverse")
library("ggmap") 

factory_data <- read.csv("Sources of Pollution - Twin Cities - Sheet1 (2).csv") %>%
  mutate(Factory2=paste(Factories, "Factory, Minnesota"))
```

This next segments use a Google API key in order to get the locations of
each station of the light rail in latitude/longitude coordinates, then
fixes a few select points where the Google API failed to get a precise
location.

``` r
register_google(key = "GoogleAPIKey", write = TRUE)

addr.geo <- mutate_geocode(factory_data, location = Factory2, output = "latlona")
```

``` r
geo2 <- addr.geo %>%
  mutate(lat2 = ifelse(Factories=="Flint Hills Resources Line Bend Refinery, Rosemount, MN", 44.76432, lat)) %>%
  mutate(lon2 = ifelse(Factories=="Flint Hills Resources Line Bend Refinery, Rosemount, MN", -93.03947, lon)) %>%
  mutate(lat2 = ifelse(Factories=="Koch Industries (Flint Hills Resources), Rosemount, MN", 44.76424, lat2)) %>%
  mutate(lon2 = ifelse(Factories=="Koch Industries (Flint Hills Resources), Rosemount, MN", -93.03943, lon2))

write.csv(geo2, "pollution_locations.csv")
```

## Plotting the Factory Sources of Pollution

``` r
library("terra")
geo <- read.csv("stations_with_locations.csv")
geo2 <- read.csv("pollution_locations.csv")

sample_coords <- cbind(geo$lon2, geo$lat2)
lr_stations <- vect(sample_coords)
crdref <- "+proj=longlat +datum=WGS84"
pts <- vect(sample_coords, crs=crdref)

pol_coords <- cbind(geo2$lon2, geo2$lat2)
crdref <- "+proj=longlat +datum=WGS84"
pol_pts <- vect(pol_coords, crs=crdref)

library("maptiles")

plot(pts)
```

![](README_files/figure-commonmark/unnamed-chunk-11-1.png)

``` r
pts_buffer <- buffer(pts, width = 500) # Width is measured in meters
plot(pts_buffer)
```

![](README_files/figure-commonmark/unnamed-chunk-11-2.png)

``` r
lrc <- centroids(lr_project, inside = FALSE)

pts_buffer1 <- buffer(lrc, width = 10000)
extent <- buffer(pts, width = 600)

bg <- get_tiles(ext(extent))
plot(bg)
points(pts)
points(pol_pts, col = "purple", cex = 1.5)
lines(pts_buffer1, col = "blue")
lines(pts_buffer, col = "red")
```

![](README_files/figure-commonmark/unnamed-chunk-11-3.png)

## Plotting Meteorology Data

``` r
library("terra")
library("tidyverse")

#makes of list of files in that folder
files<-dir("G:/Shared drives/2024 FIRE Light Rail/DATA/GLDAS/")

for(i in 1:3288){
  r<-rast(paste0("G:/Shared drives/2024 FIRE Light Rail/DATA/GLDAS/", files[i]))

  names(r)
  #variables in page 19 of manual
  #https://hydro1.gesdisc.eosdis.nasa.gov/data/GLDAS/GLDAS_CLSM025_D.2.0/doc       /README_GLDAS2.pdf
  #Snowf_tavg<-r[[6]]
  #plot(Snowf_tavg)

  station_buffers<-vect("Station_Buffers.shp")

  #crops raster to contain only buffers around stations
  int<-crop(r, station_buffers,
            snap="in",
            mask=TRUE)
  plot(int)

  #convert cropped raster into dataframe and find average value
  metdf<-terra::extract(int, sta, fun="mean", na.rm=TRUE)  %>% 
    summarise(across(where(is.numeric), ~ mean(.x, na.rm = TRUE))) %>%
    select(-ID)

  metdf$date<-files[i]
  
  write.csv(metdf, paste0("TC_Meteorology_Data/", files[i],".csv"), row.names = F)

}
```

## Combining the data

This code combines all of the previous data we’ve gathered into a single
dataframe, along with adding in some additional variables. This
dataframe includes each station name, each station id, the date, PM2.5,
meteorological variables, the month, day of the week, and whether or not
the day is a holiday.

``` r
library("dplyr")
library("data.table")
path<-"C:/Users/rygel/Documents/team-twin-cities/TC_Meteorology_Data/"
days<-dir(path) #makes a vector of folder names

setwd("C:/Users/rygel/Documents/team-twin-cities/TC_Meteorology_Data/")

combined_files <- bind_rows(lapply(days, fread))

setwd("C:/Users/rygel/Documents/team-twin-cities/")

write.csv(combined_files, "Full_Meteorology_Data.csv")

stations <- read.csv("Station Names and IDs.csv")

path<-"C:/Users/rygel/Documents/team-twin-cities/Twin_Cities_PM25/"
months<-dir(path) #makes a vector of folder names

setwd("C:/Users/rygel/Documents/team-twin-cities/Twin_Cities_PM25/")


combined_files <- bind_rows(lapply(months, fread))

write.csv(combined_files, "Full_PM25_Data.csv", row.names = F)

setwd("C:/Users/rygel/Documents/team-twin-cities/")

PM25 <- read.csv("Full_PM25_Data.csv")
Holidays <- read.csv("major_holidays_2000_2025.csv")
Holidays = subset(Holidays, select = -year)
Weather <- read.csv("Full_Meteorology_Data.csv")
Weather = subset(Weather, select = -X)
Weather = subset(Weather, select = -V1)
stations = read.csv("Station Names and IDs.csv")

weather_fixed_date <- Weather %>%
  mutate(date = stringr::str_extract(date, "[0-9]{4}[0-9]{2}[0-9]{2}")) %>%
  mutate(date = paste(substr(date, 1, 4), "-", substr(date, 5, 6), "-", substr(date, 7, nchar(date)), sep = ""))

pm25_fixed_date <- PM25 %>%
  mutate(date = stringr::str_extract(date, "[0-9]{4}[0-9]{2}[0-9]{2}")) %>%
  mutate(date = paste(substr(date, 1, 4), "-", substr(date, 5, 6), "-", substr(date, 7, nchar(date)), sep = ""))

pm25_stations = merge(pm25_fixed_date, stations, by = "station_num")

add_weather = merge(pm25_stations, weather_fixed_date, by = "date", all.x = TRUE, all.y = FALSE)

add_holidays = merge(add_weather, Holidays, by = "date", all.x = TRUE, all.y = FALSE)

full_fixed_cols <- add_holidays %>%
  mutate(holiday = ifelse(is.na(holiday), FALSE, TRUE)) %>%
  mutate(day_of_week = weekdays(as.Date(date))) %>%
  mutate(month = months(as.Date(date)))

date_stations_sorted <- full_fixed_cols[order(full_fixed_cols$date, full_fixed_cols$station_num),]

write.csv(date_stations_sorted, "Mega_Dataframe.csv", row.names = F)
```

## Plotting PM2.5 of the different stations over time

This code plots a boxplot for the PM2.5 on each date from 2000-2008 for
each station as well as finds the differences in average PM2.5 before
and after the opening of the METRO Blue Line on June 14th, 2004. Using
this data as well as factoring in parking and other pollution sources,
we have decided to remove stations 1, 16, 28, and 34 from our data.

``` r
library(ggplot2)

all_data = read.csv("Mega_Dataframe.csv")
half_data = head(all_data, 120398)
truncated_data = head(all_data, 60199)
truncated_data2 = head(tail(all_data, -60199), 60199)

ggplot(data = half_data, aes(x = station_num, y = pm25)) +
  geom_boxplot(outlier.shape = NA, aes(group = station_num, color = factor(station_num))) +
  ylim(0, 25)
```

![](README_files/figure-commonmark/unnamed-chunk-14-1.png)

``` r
#ggplot(data = truncated_data, aes(x = station_num, y = pm25)) +
  #geom_boxplot(outlier.shape = NA, aes(group = station_num, color = #factor(station_num))) +
  #ylim(0, 25)

#ggplot(data = truncated_data2, aes(x = station_num, y = pm25)) +
  #geom_boxplot(outlier.shape = NA, aes(group = station_num, color = #factor(station_num))) +
  #ylim(0, 25)

before_mean<- aggregate(x=truncated_data$pm25,
                      # Specify group indicator
                      by = list(truncated_data$station_num),      
                      # Specify function (i.e. mean)
                      FUN = mean)

after_mean<- aggregate(x=truncated_data2$pm25,
                      # Specify group indicator
                      by = list(truncated_data2$station_num),      
                      # Specify function (i.e. mean)
                      FUN = mean)


b = before_mean$x
a = after_mean$x
```

## Setting Relevant Dates

The following code sets a list of dates for the relevant start and end
dates for the period of interest (June 2000 - June 2008), the opening of
the Metro Blue Line, the date when construction on the Blue Line began,
and a list of dates when relevant policies that might impact the level
of PM2.5 were enacted.

These policies include the Heavy-Duty Engine and Vehicle Standards,
which mandated reductions in particulate matter emissions from diesel
engines (EPA’s Heavy-Duty Engine and Vehicle Standards, 2001), the
Nonroad Diesel Rule, which set stringent emission standards for nonroad
diesel engines (Nonroad Diesel Rule, 2004), the Minnesota Mercury
Reduction Act, which aimed to reduce mercury and other pollutants from
power plants (Minnesota Mercury Reduction Act, 2006), the Next Gen
Energy Act, which set aggressive targets for reducing greenhouse gas
emissions and included measures to increase energy efficiency and the
use of renewable energy sources (Next Generation Energy Act, 2007), the
2030 Regional Development Framework, which promoted sustainable
development and reduced sprawl (2030 Regional Development Framework,
2004), the Clean Air Minnesota Initiative, which worked to reduce air
pollution through voluntary measures (Clean Air Minnesota Initiative,
2005), the Minnesota Renewable Energy Standard, which mandated that 25%
of the state’s electricity must come from renewable sources by 2025
(Minnesota Renewable Energy Standard, 2007), and the vehicle emissions
inspection and maintenance programs, which were aimed at reducing
smog-forming pollutants and ensuring vehicles were properly maintained
and efficient (Vehicle Emissions Inspection and Maintenance Programs,
2001).

``` r
library("tidyverse")
```

``` r
df <- read.csv("Mega_Dataframe.csv")
```

``` r
df2 <- df %>%
  mutate(date = as.Date(date, format = '%Y-%m-%d'))
```

``` r
# Period of Analysis
startdate <- as.Date("2000-06-01", format = '%Y-%m-%d')
enddate <- as.Date("2008-06-01", format = '%Y-%m-%d')
opendate <- as.Date("2004-06-14", format = "%Y-%m-%d")
conststart <- as.Date("2001-01-17", format = "%Y-%m-%d")
#Heavy-Duty Engine and Vehicle Standards
HD_Engine <- as.Date("2007-01-01", format = "%Y-%m-%d")
#Nonroad Diesel Rule
NR_Diesel <- as.Date("2004-06-29", format = "%Y-%m-%d")
#Minnesota Mercury Reduction Act
MC_Reduction <- as.Date("2006-05-11", format = "%Y-%m-%d")
#Next Gen Energy Act
NG_Energy <- as.Date("2007-05-25", format = "%Y-%m-%d")
#2030 Regional Development Framework
RDF <- as.Date("2004-01-01", format = "%Y-%m-%d")
#Clean Air Minnesota Initiative
CA_Init <- as.Date("2003-01-01", format = "%Y-%m-%d")
#Minnesota Renewable Energy Standard
RE_Standard <- as.Date("2001-01-01", format = "%Y-%m-%d")
#Vehicle Emissions Inspection and Maintenance Programs
VE_Programs <- as.Date("2001-04-05", format = "%Y-%m-%d")
```

## Adding DB-OLS Variables

The following code limits the data to the aforementioned period of
interest and adds dummy variable columns for the day of the week fixed
effects, the opening date of the metro, the start of construction date,
the temperature, humidity, and wind speed and their lag polynomials, the
time in days and its polynomials, and finally a column for each of the
relevant policies from the previous section. The time and weather
polynomials are to replicate the methodology of (Chen, 2012).

``` r
df3 <- df2 %>%
  filter(date>=startdate & date <= enddate) %>%
  mutate(MetroOpen = ifelse(date >= opendate, 1, 0)) %>%
  mutate(dow = wday(date)) %>%
  mutate(construction = ifelse(date > conststart & date < opendate, 1, 0)) %>%
  group_by(station_num) %>%
  arrange(station_num, date) %>%
  mutate(t = as.numeric(date-startdate)) %>%
  mutate(t2 = t^2, t3 = t^3, t4 = t^4) %>%
  mutate(l_tair = lag(Tair_f_tavg)) %>%
  mutate(l_tair_2 = l_tair^2) %>%
  mutate(l_tair_3 = l_tair^3) %>%
  mutate(l_tair_4 = l_tair^4) %>%
  mutate(l_qair = lag(Qair_f_tavg)) %>%
  mutate(l_qair_2 = l_qair^2) %>%
  mutate(l_qair_3 = l_qair^3) %>%
  mutate(l_qair_4 = l_qair^4) %>%
  mutate(l_wind = lag(Wind_f_tavg)) %>%
  mutate(l_wind_2 = l_wind^2) %>%
  mutate(l_wind_3 = l_wind^3) %>%
  mutate(l_wind_4 = l_wind^4) %>%
  mutate(CA_Init = ifelse(date >= CA_Init, 1, 0)) %>%
  mutate(HD_Engine = ifelse(date >= HD_Engine, 1, 0)) %>%
  mutate(MC_Reduction = ifelse(date >= MC_Reduction, 1, 0)) %>%
  mutate(NG_Energy = ifelse(date >= NG_Energy, 1, 0)) %>%
  mutate(NR_Diesel = ifelse(date >= NR_Diesel, 1, 0)) %>%
  mutate(RDF = ifelse(date >= RDF, 1, 0)) %>%
  mutate(RE_Standard = ifelse(date >= RE_Standard, 1, 0)) %>%
  mutate(VE_Programs = ifelse(date >= VE_Programs, 1, 0))
```

## Running Regression Models

The following code blocks run various regression models including
different control factors each time. The results from these regressions
have been collected into the table below:

| X                        | log.PM2.5.   | X.1   | X.2           | X.3           | X.4           | X.5           | X.6           |
|:-------------------------|:-------------|:------|:--------------|:--------------|:--------------|:--------------|:--------------|
| MetroOpen                | 0.020 \*\*\* | 0.009 | -0.074 \*\*\* | -0.074 \*\*\* | -0.183 \*\*\* | -0.239 \*\*\* | -0.232 \*\*\* |
| Regulation Dummies       |              |       |               |               |               | x             | x             |
| Weather Polynomials      |              |       | x             | x             | x             | x             | x             |
| Construction Dummy       |              | x     | x             | x             | x             | x             | x             |
| Month FE                 |              | x     | x             | x             | x             | x             | x             |
| Day of Week FE           |              | x     | x             | x             | x             | x             | x             |
| Holiday Dummy            |              |       |               | x             | x             | x             | x             |
| t, t^2, t^3, t^4         |              |       |               |               | x             | x             | x             |
| Exclude outlier stations |              |       |               |               |               |               | x             |

This code block runs a simple regression without any of the control
factors (Column “log.PM2.5” in table).

``` r
summary(m1 <- lm(log(pm25) ~ MetroOpen, data = df3))
```

This code block runs a regression with the construction, month fixed
effects, and day fixed effects added (Column “X.1” in table).

``` r
summary(m1 <- lm(log(pm25) ~ MetroOpen +
                   construction +
                   as.factor(month) +
                   as.factor(dow)
                   , data = df3))
```

This regression adds the weather polynomials to the previous one (Column
“X.2” in table).

``` r
summary(m1 <- lm(log(pm25) ~ MetroOpen +
                   construction +
                   Tair_f_tavg +
                   l_tair +
                   l_tair_2 +
                   l_tair_3 +
                   l_tair_4 +
                   Qair_f_tavg +
                   l_qair +
                   l_qair_2 +
                   l_qair_3 +
                   l_qair_4 +
                   Wind_f_tavg +
                   l_wind +
                   l_wind_2 +
                   l_wind_3 +
                   l_wind_4 +
                   as.factor(month) +
                   as.factor(dow)
                   , data = df3))
```

This block adds the holiday control variable into the regression (Column
“X.3” in table).

``` r
summary(m1 <- lm(log(pm25) ~ MetroOpen +
                   construction +
                   Tair_f_tavg +
                   l_tair +
                   l_tair_2 +
                   l_tair_3 +
                   l_tair_4 +
                   Qair_f_tavg +
                   l_qair +
                   l_qair_2 +
                   l_qair_3 +
                   l_qair_4 +
                   Wind_f_tavg +
                   l_wind +
                   l_wind_2 +
                   l_wind_3 +
                   l_wind_4 +
                   holiday +
                   as.factor(month) +
                   as.factor(dow)
                   , data = df3))
```

This block adds the time polynomials into the regression (Column “X.4”
in table).

``` r
summary(m1 <- lm(log(pm25) ~ MetroOpen +
                   construction +
                   Tair_f_tavg +
                   l_tair +
                   l_tair_2 +
                   l_tair_3 +
                   l_tair_4 +
                   Qair_f_tavg +
                   l_qair +
                   l_qair_2 +
                   l_qair_3 +
                   l_qair_4 +
                   Wind_f_tavg +
                   l_wind +
                   l_wind_2 +
                   l_wind_3 +
                   l_wind_4 +
                   holiday +
                   t +
                   t2 +
                   t3 +
                   t4 +
                   as.factor(month) +
                   as.factor(dow)
                   , data = df3))
```

This block adds the relevant policies for PM2.5 into the regression
(Column “X.5” in table).

``` r
summary(m1 <- lm(log(pm25) ~ MetroOpen +
                   construction +
                   Tair_f_tavg +
                   l_tair +
                   l_tair_2 +
                   l_tair_3 +
                   l_tair_4 +
                   Qair_f_tavg +
                   l_qair +
                   l_qair_2 +
                   l_qair_3 +
                   l_qair_4 +
                   Wind_f_tavg +
                   l_wind +
                   l_wind_2 +
                   l_wind_3 +
                   l_wind_4 +
                   holiday +
                   t +
                   t2 +
                   t3 +
                   t4 +
                   CA_Init +
                   HD_Engine +
                   MC_Reduction +
                   NG_Energy +
                   NR_Diesel +
                   RDF +
                   RE_Standard +
                   VE_Programs +
                   as.factor(month) +
                   as.factor(dow)
                   , data = df3))
```

Finally, this block removes the stations which were determined to be
outliers (1, 16, 28, 34) into the regression (Column “X.6” in table).

``` r
df4 <- df3 %>%
  filter(station_num != 1 & station_num != 16 & station_num != 28 & station_num != 34)

summary(m1 <- lm(log(pm25) ~ MetroOpen +
                   construction +
                   Tair_f_tavg +
                   l_tair +
                   l_tair_2 +
                   l_tair_3 +
                   l_tair_4 +
                   Qair_f_tavg +
                   l_qair +
                   l_qair_2 +
                   l_qair_3 +
                   l_qair_4 +
                   Wind_f_tavg +
                   l_wind +
                   l_wind_2 +
                   l_wind_3 +
                   l_wind_4 +
                   holiday +
                   t +
                   t2 +
                   t3 +
                   t4 +
                   CA_Init +
                   HD_Engine +
                   MC_Reduction +
                   NG_Energy +
                   NR_Diesel +
                   RDF +
                   RE_Standard +
                   VE_Programs +
                   as.factor(month) +
                   as.factor(dow)
                   , data = df4))
```

## Timeline

This graph shows the average PM2.5 across all 37 stations over time
along with relevant events plotted as vertical lines.

``` r
df5 <- df3 %>%
  group_by(date) %>%
  summarise(pm25 = mean(pm25))
ggplot(data = df5, aes(x = date, y = pm25)) +
  geom_line(col = "lightblue") +
  geom_vline(aes(xintercept = opendate, col = "Opening Date")) + 
  geom_vline(aes(xintercept = conststart, col = "Construction Date")) + 
  geom_vline(aes(xintercept = CA_Init, col = "CA")) +
  geom_vline(aes(xintercept = HD_Engine, col = "HD")) +
  geom_vline(aes(xintercept = MC_Reduction, col = "MC")) +
  geom_vline(aes(xintercept = NG_Energy, col = "NG"))
```

![](README_files/figure-commonmark/unnamed-chunk-28-1.png)

## References

Sources of Data

1.  Li, B., H. Beaudoing, and M. Rodell, NASA/GSFC/HSL (2020), GLDAS
    Catchment Land Surface Model L4 daily 0.25 x 0.25 degree GRACE-DA1
    V2.2, Greenbelt, Maryland, USA, Goddard Earth Sciences Data and
    Information Services Center (GES DISC), Accessed: 06/17/2024,
    [10.5067/TXBMLX370XX8](https://doi.org/10.5067/TXBMLX370XX8)

2.  Di, Q., Y. Wei, A. Shtein, C. Hultquist, X. Xing, H. Amini, L.
    Shi, I. Kloog, R. Silvern, J. Kelly, M. B. Sabath, C. Choirat, P.
    Koutrakis, A. Lyapustin, Y. Wang, L. J. Mickley, and J. Schwartz.

    2021. Daily and Annual PM2.5 Concentrations for the Contiguous
          United States, 1-km Grids, v1 (2000 - 2016). Palisades, New
          York: NASA Socioeconomic Data and Applications Center (SEDAC).
          <https://doi.org/10.7927/0rvr-4538>. Accessed 06/17/2024.

3.  Di, Q., H. Amini, L. Shi, I. Kloog, R. Silvern, J. Kelly, M. B.
    Sabath, C. Choirat, P. Koutrakis, A. Lyapustin, Y. Wang, L. J.
    Mickley, and J. Schwartz. 2019. An Ensemble-based Model of PM2.5
    Concentration Across the Contiguous United States with High
    Spatiotemporal Resolution. Environment International 130: 104909.
    <https://doi.org/10.1016/j.envint.2019.104909>.

Sources for Relevant Policies:

1.  Minnesota Public Utilities Commission. (2007). Renewable Energy
    Standard. Retrieved from
    [https://mn.gov/puc/activities/economic-analysis/renewable-environmental-dockets/#:~:text=Renewable%20energy%20goals%20were%20passed,%2C%20the%20state’s%20largest%20utility](https://mn.gov/puc/activities/economic-analysis/renewable-environmental-dockets/#:~:text=Renewable%20energy%20goals%20were%20passed,%2C%20the%20state's%20largest%20utility)

2.  Vehicle Emissions Inspection and Maintenance (I/M): Policy and
    technical guidance \| US EPA. (2024, February 2). US EPA.
    <https://www.epa.gov/state-and-local-transportation/vehicle-emissions-inspection-and-maintenance-im-policy-and-technical>

3.  Final Rule for Control of Air Pollution from New Motor Vehicles:
    Heavy-Duty Engine and Vehicle Standards and Highway Diesel Fuel
    Sulfur Control Requirements \| US EPA. (2024, May 17). US EPA.
    <https://www.epa.gov/regulations-emissions-vehicles-and-engines/final-rule-control-air-pollution-new-motor-vehicles>

4.  Proposed Rule and Correction for control of Air pollution from new
    motor vehicles: In-Use Testing for Heavy-Duty Diesel Engines and
    Vehicles \| US EPA. (2023, July 11). US EPA.
    <https://www.epa.gov/regulations-emissions-vehicles-and-engines/final-rule-control-air-pollution-new-motor-vehicles-heavy>

5.  Final rule for control of emissions of air pollution from nonroad
    diesel engines and fuel \| US EPA. (2024, February 6). US EPA.
    <https://www.epa.gov/regulations-emissions-vehicles-and-engines/final-rule-control-emissions-air-pollution-nonroad#:~:text=Rule%20Summary%20In%202004%2C%20EPA%20finalized%20Tier,nonattainment%20areas%20to%20improve%20their%20air%20quality>.

6.  Reducing mercury releases \| Minnesota Pollution Control Agency.
    (n.d.). Minnesota Pollution Control Agency.
    <https://www.pca.state.mn.us/air-water-land-climate/reducing-mercury-releases>

7.  Clean Cars Minnesota. (n.d.). Conservation MN.
    <https://www.conservationminnesota.org/clean-cars-minnesota>

8.  2030 Regional Development Framework - Metropolitan Council. (n.d.).
    Metropolitan Council.
    <https://metrocouncil.org/Planning/Thrive-2040/2030-Regional-Development-Framework.aspx>

9.  Environmental Initiative. (2024, April 19). Clean Air Minnesota -
    Environmental Initiative.
    <https://environmental-initiative.org/our-work/clean-air-minnesota/>

Sources for Confounding Sources of Pollution:

1.  Minnesota Pollution Control Agency. (n.d.). Northern Metal
    Recycling: Air Quality Permit Violations. Retrieved 2024, from
    <https://www.pca.state.mn.us/news-and-stories/northern-metals-pays-12000-for-violating-air-quality-regulations-at-its-becker-facility#:~:text=state.mn.us-,Northern%20Metals%20pays%20%2412%2C000%20for%20violating%20air%20quality%20regulations%20at,particulate%20matter%20>(PM10%20and%20PM2.

2.  St Anthony, N., & Tribune, S. (2022, February 13). Flint Hills’ Pine
    Bend refinery produces more fuel with less pollution. Star Tribune.
    <https://www.startribune.com/flint-hills-pine-bend-refinery-produces-more-fuel-with-less-pollution/600146396/>

3.  Xcel Energy. (n.d.).
    <https://mn.my.xcelenergy.com/s/about/newsroom/press-release/xcel-energy-takes-major-step-toward-replacing-coal-fired-king-plant-with-clean-e-MCQ6MJVC5VIZCSLMVOCUPTC5KMQM>

4.  AIR EMISSION PERMIT. (2008). In epa.gov (No. 12300055–004).
    Environmental Protection Agency.
    <https://www.epa.gov/system/files/documents/2021-12/gerdauameristeel_12300055-004.pdf>

5.  Minnesota Department of Health. (2004). Public health assessment for
    perfluorochemical contamination at a hazardous waste site in
    Minnesota. In Minnesota Department of Health Report.
    <https://www.health.state.mn.us/communities/environment/hazardous/docs/sites/washington/3mcg0205.pdf>

6.  Hennepin County wrestles with future of Minneapolis waste
    incinerator. (2023, September 21). MPR News.
    <https://www.mprnews.org/story/2023/09/21/hennepin-county-wrestles-with-future-of-minneapolis-waste-incinerator>

7.  APA Citation: KOCH REFINING CO./N-REN CORP. \| Superfund Site
    Profile \| Superfund Site Information \| US EPA. (n.d.).
    <https://cumulis.epa.gov/supercpad/SiteProfiles/index.cfm?fuseaction=second.cleanup&id=0503686>

8.  APA Citation: Hillesheim, D. V. & Xcel Energy. (2023). Revised
    Petition for Alternative Operational Limits for Continuous
    Compliance Demonstration under 40 C.F.R. Part 63, Subpart YYYY. In
    U.S. Environmental Protection Agency \[Report\].
    <https://www.epa.gov/system/files/documents/2023-09/Xcel%20Energy%20High%20Bridge_05-22-2023.pdf>

9.  Rademacher, N. (n.d.). Meet the Main Energy Plant: a hidden world
    reducing University emissions. The Minnesota Daily.
    <https://mndaily.com/257087/news/acenergyplant/>

10. ANOKa \| Federal Ammunition \| Minnesota Pollution Control Agency.
    (n.d.). Minnesota Pollution Control Agency.
    <https://www.pca.state.mn.us/local-sites-and-projects/anoka-federal-ammunition>

11. Sfiecke. (2006, September 8). EPA cites CertainTeed for clean air
    violations. SWNewsMedia.com.
    <https://www.swnewsmedia.com/shakopee_valley_news/news/epa-cites-certainteed-for-clean-air-violations/article_ad8d6f3b-44f5-59ab-8451-c3860538a7a9.html>

12. EJMap. (n.d.).
    <https://ejmap.org/displayfacility-74250.htm?giFacilityid=74250&gsTable=facility>
