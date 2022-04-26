# Twitter Snowflake Approach
- https://en.wikipedia.org/wiki/Snowflake_ID
- https://blog.twitter.com/engineering/en_us/a/2010/announcing-snowflake
- sign 1 bit, not used, always 0 as positive number
- timestamp 41 bits + datacenter 5 bits + machine 5 bits + seq 12 bits
