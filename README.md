# jaydenfont-covid19analysis

Analysis of COVID-19 Data

Sources:
https://github.com/nytimes/covid-19-data/blob/master/us-states.csv
https://covid19.nj.gov/#live-updates

This notebook plots the current COVID-19 stats in New Jersey. It uses the following libraries: Matplotlib, Numpy, Pandas, Selenium, and Datetime

Case data is taken from the New York Times COVID-19 repository. From this repository, the current and historic statewide data at the state and county level is used to plot the current data. Total case count over time, current county numbers, new cases per day (with rolling average), and trajectory of new cases are plotted using these data.

Hospitalization data is not reported in a clean format. The most reliable source is the NJ DOH website, which maintains interactive plots of the data. This script uses web-scraping to pull the data from this dashboard. Because the website is Javascript-heavy, I chose the Selenium API to perform the scraping. First, Hovering over each bar in the dashboard shows that day's data, but the bubble containing that information is hidden when a mouse is not hovering over the specific bar. To get around this, I used Chromedriver. The page takes some time to load, so the script contains an explicit wait which prevents further action until loading is complete. Once the page has loaded, a virtual mouse is scripted to hover over each day's hospitalization data, which reveals a bubble with the date and numbers. The script then scrapes the data from the HTML code containing the bubble, and saves it for later use. Moving left to right, the script hovers over each day and pulls the data from the bubble, and then plots the hospitalization data over time. 
