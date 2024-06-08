# OpenWeather
This collection was created for the API testing exercise.
It consists of 2 folders: positive test scenarios and negative test scenarios.
The positive test scenarios test: latitude and longitude coordinate validity, city and country data validity, weather condition validity.
The negative test scenarios test: Invalid API key, Invalid City name.
All scenarios have status code tests and response time tests. The response time tests are run from collection test. The status code tests are run from positive test scenario folder and seperately for each negative test scenarios.
All scenarios are tested with a city json data file that was taken from https://bulk.openweathermap.org/sample/ site and edited so it only has 4 locations that can be run through collection run. This file is also available in the repository

It also has the report json file and a readme file with instructions and descriptions (which are also available in the collection overview
