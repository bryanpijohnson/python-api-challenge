# Bryan Johnson's GWU Module 6 Pandas Assignment READ ME File

## The files for this assignment can be found at the following repo:
https://github.com/bryanpijohnson/python-api-challenge

## Within the repo link, you will find the following folders and files to be reviewed and graded:

- **README.md** - that is this file. :)
- **output_data** - where the output images and CSV file for the WeatherPy assignment are located
- **WeatherPy** - this is the folder where the following files live
    - **WeatherPy.ipnyb** - this is the WeatherPy assignment
    - **VacationPy.ipynb** - this is the VacationPy assignment
    - My API keys are stored in this folder, but ignored by the repo. ;)

## Here are the descriptions of each Jupyter Notebook file:

### **WeatherPy.ipnyb**

#### **Initial Setup**

I started off by picking a random set of 1500 latitudes and longitudes and then used the citipy library to find the nearest city to those coordinates. Keeping one copy of each of the cities found, we print out the number of unique cities found. Anecdotally, that number has always been somewhere between 550 and 650. 

Then, I called on the openweathermap API to find following weather facts for each of the cities found above:

- Latitude
- Longitude
- Maximum Temperature
- Humidity
- Cloudiness
- Wind Speed
- Country
- Date (in Unix for current date and time)

That information gets organized into a DataFrame (table) and then saved to an external CSV file for later analysis in the VacationPy.ipnyb file.

#### **Graphs and Analysis**

Using the city data I collected, I graphed the following attributes against the cities' latitude using scatter plots:

- Max Temperature
- Humidity
- Cloudiness
- Wind Speed

At this point, I then separated the data in two separate sets, based on whether it was in the Northern or Southern Hempisphere. I graphed the same plots again, one for each hemisphere, determining the line of best fit for each data set and if the metric has a relationship with the Latitude of the city.

To achieve this, I created the function *lin_plot()*, which takes the x-values, y-values, title of the graph, and the coordinates where to place the equation of the line of best fit. It then creates the scatter plot from the data, along with the line of best fit. Doing this made graphing the data each time, for all 8 graphs, much easier in the long run.

For each pair of graphs (Northern vs. Southern Hemisphere), I then gave a reason why the relationship was either strong or weak. In these cases, only the Temperature had a strong correlation to the Latitude; all others did not.

This concluded my analysis.

---

### **VacationPy.ipnyb**

#### **Initial Setup**

To begin, I imported the city data I exported from the WeatherPy activity to use for this activity. 

Then, I then created a map using the *Lng* and *Lat* columns as the Longitude and Latitude, respectively. I made the size of the circle to be proportional to the *Humidity* column value to show that visually on the map. I also colored each city individually, and set the transparency of each circle at 50%.

#### **Graphs and API Pull for Hotels**

Next, I filtered out all rows of data that had weather conditions that were not considered *ideal*. The assignment suggested using the following conditions:

- A max temperature lower than 27 degrees but higher than 21
- Wind speed less than 4.5 m/s
- Zero cloudiness

When I ran this the first time, I was only left with 7 data points. Since I wanted to have more than that in my final data set, I updated my conditions to the following:

- A max temperature between 20 and 30 degrees C
- Wind speed less than 6 m/s
- Zero cloudiness

Doing this gave me a data set of over 15 cities each time and so this was a better set to continue working with. I narrowed down the columns given to only a few left, so that I could focus on those columns.

Using the API Key for geoapify.com, I used the API along with its *filter* and *bias* parameter calls to be able to find the closest hotel to that latitude and longitude pair, within a 10K radius.

For each row, the newly found hotel was added to the narrowed down dataset. If a hotel wasn't found within that radius, then "No hotel found" was included instead. I then plotted each of the Lat/Lon pairs on a map again with the same attributes as before, but added in the Hotel Name I found as well as the country the city was in.

This concluded my analysis.

---

If you have any questions, please feel free to contact me.