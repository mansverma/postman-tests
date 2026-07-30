# postman-tests

Postman collection tests for API testing using Newman.

## Prerequisites

```bash
npm install -g newman newman-reporter-htmlextra
```

## Run Tests

```bash
# Booking API
newman run collections/Booking.postman_collection.json

# User API
newman run collections/UserAPI.postman_collection.json
```

## Run Tests with Reports

```bash
# Booking API
newman run collections/Booking.postman_collection.json \
    -r cli,htmlextra,junit,json \
    --reporter-htmlextra-export results/booking-report.html \
    --reporter-junit-export results/booking-report.xml \
    --reporter-json-export results/booking-report.json

# User API
newman run collections/UserAPI.postman_collection.json \
    -r cli,htmlextra,junit,json \
    --reporter-htmlextra-export results/userapi-report.html \
    --reporter-junit-export results/userapi-report.xml \
    --reporter-json-export results/userapi-report.json
```

## View Reports

```bash
# HTML (opens in browser)
open results/booking-report.html
open results/userapi-report.html

# JSON
cat results/booking-report.json
cat results/userapi-report.json

# JUnit XML
cat results/booking-report.xml
cat results/userapi-report.xml

# Open results folder
open results/
```
