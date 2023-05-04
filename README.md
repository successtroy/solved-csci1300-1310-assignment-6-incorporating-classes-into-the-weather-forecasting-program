Download Link: https://assignmentchef.com/product/solved-csci1300-1310-assignment-6-incorporating-classes-into-the-weather-forecasting-program
<br>



<ol>

 <li>Apply the concept of program decomposition.</li>

 <li>Define a class managing multiple files for the header, methods and driver.</li>

 <li>Apply the concept of private vs public variables and functions.</li>

</ol>




This assignment builds on the previous assignment by incorporating classes into your program. The data file you will use is the same, it’s the boulderData file on Moodle. If you downloaded that file and changed its format for Assignment 5, you are welcome to use your same file for this assignment.




​       The <em>boulderData</em>​ file contains comma-delimited information about the weather forecast for the current and the next three days.




The first day in the file is January 26, 2016 and the last day in the file is September 29, 2016. The format for each line in the file is as follows:




<table width="0">

 <tbody>

  <tr>

   <td width="53">Day</td>

   <td width="73">Forecas t day</td>

   <td width="53">High temp</td>

   <td width="53">Low temp</td>

   <td width="79">Humidity</td>

   <td width="52">Avg. wind</td>

   <td width="58">Avg. winddirect.</td>

   <td width="52">Max. wind</td>

   <td width="58">Max. winddirect.</td>

   <td width="59">Preci p</td>

  </tr>

  <tr>

   <td width="53">1-26-2016</td>

   <td width="73">1-26-20 16</td>

   <td width="53">H:40</td>

   <td width="53">L:26</td>

   <td width="79">43</td>

   <td width="52">6</td>

   <td width="58">WNW</td>

   <td width="52">10</td>

   <td width="58">WNW</td>

   <td width="59">0.0</td>

  </tr>

 </tbody>

</table>




<strong>Day:</strong> The current day​




<strong>Forecast day:</strong> The day that the forecast is for. In this example, the day and forecast​     day are the same, which means it’s the forecast for 1-26-2016 on 1-26-2016. There are other lines in the file that show the forecast for a future day. For example, if the day were 1-26-2016 and forecast day were 1-27-2016, it would be the forecast for 1-27-2016 issued on 1-26-2016.




<strong>High temp:</strong>​ The forecasted high temp for the forecast day.




<strong>Low temp:</strong>​ The forecasted low temp for the forecast day.




<strong>Humidity:</strong>​ The forecasted humidity for the forecast day.




<strong>Avg. wind:</strong>​ The forecasted average wind speed for the forecasted day.




<strong>Avg. wind direction:</strong>​ The forecasted average wind direction for the forecasted day.




<strong>Max. wind:</strong>​ The forecasted maximum wind speed for the forecasted day. <strong>Max. wind direct.:</strong>​ The forecasted direction for the maximum wind speed for the forecasted day.




<strong>Precip.:</strong>​ The forecasted precipitation.




<h1>Assignment Details</h1>

There is a .hpp file on Moodle that provides a definition for a ​<em>WeatherForecaster</em> class. The functionality for that class is similar to the functionality you implemented in Assignment 5, with a few additional functions. Instead of using an array of <em>structs</em>​ and functions to process the array, you will create one ​       ​<em>WeatherForecaster</em> object that includes the array of ​<em>structs</em> as a private variable and public methods to process the data.




The struct for this assignment has an additional member called ​    ​<em>forecastDay</em>, you will need to store all of the data this time.




struct ForecastDay{      string day; string forecastDay;

int highTemp;      int lowTemp;      int humidity;      int avgWind;      string avgWindDir;      int maxWind;      string maxWindDir;      double precip;

};













​6

<h2>Methods in the WeatherForecaster class</h2>




void addDayToData(ForecastDay);

<ul>

 <li>Takes a ForecastDay as an argument and adds it to the private array stored in the WeatherForecaster object.</li>

 <li>Use the private index variable to control where ForecastDay is added to the array.</li>

</ul>




void printForecastForDay(string);

<ul>

 <li>Take a date as an argument and shows the forecast for that day.</li>

</ul>

<h3>(when day == forecastDay)</h3>




void printFourDayForecast(string);

<ul>

 <li>Takes a date as an argument and shows the forecast issued on that date and for the next three days (see expected output below). For example, for a date of 1-26-2016, you would show the forecast for 1-26-2016 issued on 1-26-2016 as well as the forecast for 1-27, 1-28, and 1-29 issued on 1-26.</li>

</ul>




double calculateTotalPrecipitation();

<ul>

 <li>Returns the sum of the precipitation in the data set. The accumulator is modified only when forecastDay is the current day (<em>day == forecastDay)</em>​ .</li>

</ul>




void printLastDayItRained();

<ul>

 <li>Shows the date of the last measureable precipitation.</li>

</ul>

<h3>(when day == forecastDay)</h3>




void printLastDayAboveTemperature(int);

<ul>

 <li>Takes an integer (temperature) as an argument and shows the date for the last day above that temperature. If no days are above the temperature, prints “No days above that temperature.”</li>

</ul>

<h3>(when day == forecastDay)</h3>




void printTemperatureForecastDifference(string);

<ul>

 <li>Takes a date as an argument and shows the temperature forecast for that date using the three days leading up to the date and the day-of forecast.</li>

</ul>




string getFirstDayInData();

<ul>

 <li>Returns the first date in the data with a day-of forecast, i.e. day</li>

</ul>

= forecastDay




string getLastDayInData();

<ul>

 <li>Returns the last date in the data with a day-of forecast, i.e. day</li>

</ul>

= forecastDay













<h2>Functionality in main()</h2>




In your <em>main()</em>​ function, you will need to open the file, read in the data, and create an instance of WeatherForecaster. Once you’ve populated a ForecastDay instance, you add it to your WeatherForecaster instance using the addDayToData method.




Once you’re confident that the array data is correct, call the methods to analyze the data and print the results. Your output should look like this:




Forecast statistics:

Last day it rained: &lt;date of last rain event&gt;

Total rainfall: &lt;sum of precipitation&gt;

First date in data: &lt;date&gt;

Last date in data: &lt;date&gt;




Your main function should prompt the user for a date and pass that date as an argument to the <em>printForecastForDay</em>​ and <em>printFourDayForecast</em>​ methods to display the information. If the date is not found in the file, your program should print “Date not found.”




WeatherForecaster wf; cout&lt;&lt;”Enter a date:”; getline(cin, date); wf.printForecastForDay(date);




Information displayed in <em>printForecastForDay</em>​ :




Forecast for &lt;date&gt;:

H: &lt;high temp&gt;

L: &lt;low temp&gt;

Humidity: &lt;humidity&gt;

Avg. wind: &lt;avg wind speed&gt;

Avg. wind direction: &lt;avg wind direction&gt;

Max wind: &lt;max wind speed&gt;

Max wind direction: &lt;max wind direction&gt;

Precipitation: &lt;precip&gt;




For <em>printFourDayForecast</em>​ , repeat information for all four days.




Information displayed for <em>getFirstDayInData</em>​ :




1-26-2016




Information displayed for <em>getLastDayInData</em>​ :




9-29-2016




Information displayed for <em>printTemperatureForecastDifference</em>​ :




Forecast for &lt;date 1&gt; issued on &lt;date 2&gt;

H:&lt;high temp&gt;

L:&lt;low temp&gt;

Forecast for &lt;date 1&gt; issued on &lt;date 3&gt;

H:&lt;high temp&gt;

L:&lt;low temp&gt;

Forecast for &lt;date 1&gt; issued on &lt;date 4&gt;

H:&lt;high temp&gt;

L:&lt;low temp&gt;

Actual forecast for &lt;date 1&gt;

H:&lt;high temp&gt;

L:&lt;low temp&gt;




Information for <em>calculateTotalPrecipitation</em>​ :

Total rainfall: &lt;double&gt; inches




Information for <em>printLastDayItRained</em>​ :

Last day it rained: &lt;date&gt;




Information for <em>printLastDayAboveTemperature</em>​ :

It was above &lt;temperature&gt; on &lt;date&gt;


