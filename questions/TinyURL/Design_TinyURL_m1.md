# Functional Requirements
- user can input a URL with any length
- the system return a short URL, as short as possible
- the short URL is human-readable, e.g. t.com/agt7f
- inactive URLs should be cleaned after 30 days

# Non-functional Requirements
- high reliability, no incorrect/missing data
- high available, 99.99% online
- high scalability, 1M DAU, 1 write / 10 reads
- low latency, redirect in 200 ms

# Capacity Estimation
- Write: 1M / 24 / 3600 ~= 1M / 10^5 = 10 QPS
- Read: 100 QPS
- Capacity: 1M * 365 * 10 = 4B
- Storage: 100 bytes * 1M * 365 * 10 = 400 GB

# TinyURL Service - Hash with Collision
- MD5(longURL) → 128 bytes
- get the first 10 chars, retry if collision
- Base62 [A-Za-z0-9], Log4B/Log62

# TinyURL Service - auto-increased ID encoding
- ID generator, from 1 to 4,000,000,000
- a. generate in real time, simple
- b. pre-generate ID, better performance
- 1 = 1, 
- Base62, 10,000 = x * 62^2 + y * 62 + z * 1 = xyz

# TinyURL - duplicate URL
- introduce cache, bloom filter
- check if the long URL in bloom filter
- create short URL if non-exists
- try cache if it exists
- else try database

# Cache Eviction
- LRU

# Clean Service
- another bloom filter

# Database Design
- urls (
     id, 
     shortURL
    longURL
    lastAccessTime)
- ids(id, used)
- NoSQL, no need ACID

# System API
- JSON shortenURL(String longURL)
             if check_in_bloom_filter(longURL):
                    xxxx
             else:
                  return ...

- return { success: true, shortURL: abc, errorMsg: xyz }
- 1. check if the long URL in bloom filter
- 2. create short URL if not existing in bloom filter, and store in DB
- 3. try cache if it exists
- 4. read existing short URL from database if created previously but not in cache
- 5. return shortURL in JSON
- JSON restoreURL(String shortURL)
