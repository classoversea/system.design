# Design ChatApp
- https://systeminterview.com/design-a-chat-system.php
- https://www.educative.io/courses/grokking-the-system-design-interview/B8R22v0wqJo
- https://www.algoexpert.io/systems/workspace/design-slack
- Weak Hire: service, database, storage, tables
- Hire: web socket, sharding, push notification
- Strong Hire: group chat, online status update

## Functional Requirement
- 1-on-1 chat, and group chat, text message
- user online status, lastSeen time
- message status: sent, delivered & read
- message sequence and persistence
- notification
- TODO: send image, voice and video
- TODO: ID-Generator, GraphDB
- TODO: Security

## Non-functional Requirement
- high reliability, message not lost
- high availability, 99.999%, 3600*24*365*0.001% = 5 min
- high scalability, 100M DAU
- low latency, real-time experience

## Capacity Estimation
- 100M DAU * 100 messages * 100 bytes = 1TB / day
- write: 100M * 100 / 10^5 = 100K QPS
- storage: 1TB * 2000 = 2PB / 5 years
- bandwidth: 100K QPS * 100 bytes = 10MBps
- memory: 1M concurrent * 10K / connection = 10GB
- connection: 100M / 500K = 200 chat servers

## System API
- boolean sendMessage(fromId, toType, toId, content, timestamp)
- List<Entity> getFriendList(fromId)
- List<Message> getMessage(lastMessageId)
  
## Database Design
- users(id, name, password)
- groups(id, name, createUserId)
- friends(fromId, toType, toId, lastChatTime)
- messages(id, fromId, toType, toId, content, timestamp)

## High-level Design

## Detail Design
- sharding web socket server by user ID
  
  
