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

- `requests` – for making HTTP requests.
- `pyyaml` – for reading the YAML configuration file.


