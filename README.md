# Endpoint Health Monitoring Script

This Python script monitors the health of multiple endpoints, tracking their availability and logging their status over time. It checks the health of each endpoint by sending HTTP requests and logs the cumulative availability percentage for each domain.

## Features

- Monitors multiple endpoints, specified in a configuration YAML file(test2.yaml).
- Tracks the response status code and response time.
- Logs the availability percentage for each domain.
- Prints cumulative availability every 15 seconds.
- Can be customized with additional headers and request bodies.

## Requirements

Before running the script, ensure you have the following Python packages installed:

- requests – for making HTTP requests.
- pyyaml – for reading the YAML configuration file.


## How the Script Works

Loading Configuration:

- The script loads the configuration from the test2.yaml file using the yaml.safe_load() function.

Health Check:

- The script checks each endpoint by sending an HTTP request (either GET or POST), depending on the configuration.

- For each request, the script records the status code and response time.

- The endpoint is considered "UP" if the response status code is in the 200-299 range and the response time is below 0.5 seconds. Otherwise, the endpoint is marked as "DOWN".

Logging Results:

- Every 15 seconds, the script prints the availability percentage for each domain. Availability is calculated as the ratio of "UP" responses to total responses for that domain.

Stopping the Monitoring:

- You can stop the monitoring at any time by pressing Ctrl+C in the terminal. The script will catch the KeyboardInterrupt and exit gracefully.



## Fields in test2.yaml:

Name: A human-readable name for the endpoint.

URL: The full URL of the endpoint to monitor.

Method: The HTTP method (GET, POST, etc, etc)

Content_type: This is set to application/json

Body: The body to send in a POST request, formatted as a JSON string. Set to null for GET requests.

Headers: Any custom headers needed for the request. Set to null if no headers are required.

**** There is no Authorazation needed to be stored in this yaml as this is only test environment*****

## Usage:

Save your endpoints configuration in a test2.yaml file.

Run the monitoring script by passing the path to the YAML configuration file as an argument.


## Command line to run Script

python Fetch_main.py test2.yaml


## Expected Ouput

example.com has 25% availability percentage

example.com has 30% availability percentage

## Changes made to code

- First thing I noticed was in line 14 there was no default method, so I added GET to be the default function
- Second thing I noticed was the job ran fine but the results kept printing out a steady 25% avability, then I realised this was because there was no response time added to logice. I added on line 23 to the if statement to include response time less than equal to 0.5.
- I then quickly realized I needed to create a variable response time and start time (this can be seen on line 19 and 21)
- 



