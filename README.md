# OpenWeather
This collection was created for the API testing exercise.
It consists of 2 folders: positive test scenarios and negative test scenarios.
The positive test scenarios test: latitude and longitude coordinate validity, city and country data validity, weather condition validity.
The negative test scenarios test: Invalid API key, Invalid City name.
All scenarios have status code tests and response time tests. The response time tests are run from collection test. The status code tests are run from positive test scenario folder and seperately for each negative test scenarios.
All scenarios are tested with a city json data file that was taken from https://bulk.openweathermap.org/sample/ site and edited so it only has 4 locations that can be run through collection run. This file is also available in the repository

It also has the report json file and a readme file with instructions and descriptions (which are also available in the collection overview

## Positive Test Scenarios:

### Latitude and longitude validation:

In the pre-request script - variables are set for the GET request from city json file: longitude and lattitude.
In the tests the first thing to check for is longitude and lattitude validity: longitude should be between -180 and 180 degrees, enything beyond is invalid longitude coordinate, lattitude should be between -90 and 90 degrees, enything beyond is invalid lattitude coordinate.
Then the requested longitude and lattitude is checked against the responses longitude and lattitude. Since the response rounds a bit the longitude and lattitude and the rounding is inconsistent through out the responses, so a different approach was taken to test accuracy of the response - a tolerance was introduce to see if the response does not go far from the requested coordinates. Understandably that the difference could mean a whole new location so the tolerance was set to 0,01 so that the location would stay the same. This can be adjusted to get more accurate results.

### City and country data validation:

In the pre-request script - variables are set for the GET request from city json file: city and country code.
In the tests to check the city and country data validity in the response it was tested against the json data taken from open weather site. The following things were tested from the response against the request: city name, city Id and country code and country code validity as per REGEX (2-letter code).

### Weather condition validation:

In the pre-request script - city variable is set for the GET request from city json file.
In the test a weather condition code and main description dictionary was created to match the data in https://openweathermap.org/weather-conditions site and it was used to test the response given weather code and main match. For further exploration it would be good to create a more detailed file that would test all the weather condition response, including: weather condition ID, weather condition main, description, icon code. But since it was required only to validate weather condition - current approach was taken.


## Negative Test Scenarios:

### Invalid API key:

In the pre-request script - a wrong api key variable is set for the GET request.
In the test it was checked for the status code and message in the response.

### Invalid City name:

In the pre-request script - a wrong city variable is set for the GET request
In the test it was checked for the status code and message in the response.
All the scenarios have a response time validity test - not to exceed 200ms


### How to set up:

Before setting up, an API key is needed:
 - Navigate to https://openweathermap.org/
 - Create an account
 - Verify email (after email verification an email will be sent with an already generated API key, that will be available in couple hours, you can copy it from there or continue to next steps)
 - Navigate to https://openweathermap.org/
 - Click on your account and then on "My API keys"
 - Copy API key

But an environment variable for API key is already set and can be used for the test run.

In postman:

 - Open postman
 - Click on "Import" - a popup dialog window will appear
 - In the bottom click on "other sources" and choose github


