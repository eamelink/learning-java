# Weather

The directory `weather` contains a file `weather.csv`. This file contains recorded weather information and was obtained from the Dutch Weather Institute KNMI.

The file contains a comments section at the top, with two main parts:

 * A list of the weather stations in NL and their code.
 * A list of the data fields in the file.

## Assignment 1

Parse the weather file with a CSV parser.

Print the date and the location of the hottest recorded moment.

Print the most beautiful day and location that was observed:

  * No precipitation
  * No wind gusts more than 8m/s
  * The Maximum temperature of the day must be between 22 and 28 degrees Celsius
  * Sort by highest amount of sun

Add tests where you see fit.

## Assignment 2

Parse the names of the stations from the CSV file header.

## Assignment 3

Setup a Postres database, and make a table for the data records, and a table for the stations. Add a foreign key constraint from the station id in the records table to the row in the stations table.

Load the CSV file data into the database, using JDBC.

Then, solve the same assignment as #1, but this time using a database query to find the most beautiful day.
