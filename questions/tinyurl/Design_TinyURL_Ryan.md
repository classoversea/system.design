# Design_TinyURL
- https://www.educative.io/courses/grokking-the-system-design-interview/m2ygV4E81AR
- https://systeminterview.com/unlock.php
- https://www.youtube.com/watch?v=He-V_RuHwek

## Steps
- functional/non-functional requirements, 5 min
- capacity estimation, 5 min
- high level and data flow, 5 min
- database design, 5 min
- System API, 5 min
- detail and trade off, 10 min
- optimization and monitor, 3 min
- summary, 2 min
- ref: https://jishuin.proginn.com/p/763bfbd6a6d3

## Estimate
- 1, K, M, G, T, P
- 1, 3, 6, 9, 12, 15
- 1 day = 3600 * 24 ~= 10^5 seconds
- 5 years = 365 * 4 ~= 2*10^3 days

## Functional Requirement
- input a URL and get a short URL
- visit the short URL and redirect to the original URL
- short URL must be random
- short URL must be unique
- short URL must be human-readable
- all URLs will expire if inactive
- stored for 5 years 
- recaptcha to avoid heavy use

## Non-functional Requirement
- high reliability, no data lost/incorrect
- high availability, 99.99% 
- high scalability, 100M visits / day
- low latency, reponse time <= 100ms

## Capacity Estimation

## System API

## Database Design

## High-level Design

## Detail Design
