---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
System - collecn of s/w &hardware components that work together to provide specific functionality to user or other system.

system design : 

scalability, maintainability - storing the info, compatibility, reliability - without failure the system should work , availability, latency - how much time it is taking to convert to desired o/p,

throughput - how many requests handling per sec,
fault tolerance - 

hld - big picture, like db, caching, how we managing edge cases, what apis, components, how to maintain system ed by high level profiles,availability, reliability, us


lld - oops concepts, focus more on implementation. 

CAP theorm - Consistency, Availability, partition tolerance.

A distributed system can fully guarantee only two out of these three at the same time when a network failure happens.

In a distributed system, during a network partition, you must choose between Consistency and Availability.

Consistency (C)

Every user gets the same latest data no matter which server they connect to.

Suppose you transfer ₹100 from Bank Account A.

After the update:

Every server immediately shows the new balance.
No server shows old data.

So:
✅ All nodes return the same result.

The system always responds to requests, even if some servers are down.

Example

You open a shopping app:

It always gives a response.
Even during failures, it still works.

But:

The data may sometimes be slightly outdated.

So:
✅ System remains operational.

3. Partition Tolerance (P)

The system continues working even when network communication between servers breaks.

This is what you asked specifically.


Example of Partition

Imagine 2 servers:

Server A → Hyderabad
Server B → US

Normally they sync data




Now internet connection between them fails.

This is called a network partition.

Both servers are now isolated.


interviews 

System design of "Book of my show" - steps we follow 

Requirments - core entities - APi - HLD - Data flow - Deep drive into system

1. Requirements 

   1. Funcq requirements - po will give , customer pov.

 *user should be able to search the events.
 *user should be able to view the event/tickects.
 *user should be able to book the ticket
 *user should be able to recieve the ticket email/sms.

   2. Non func requirements 

* while booking ticket, consistency >>Availability 
* while searching strongly available,
* handle peak events
* search should be fast.
* reads >> writes

2. core entities 

  user(id,name,)
  events (name,venue,date,performer,...)
  performer(id,name,...)
  venue(seats,loc,address)
  seats(booked/not booked, category, price)
  ticket(id, paymentid, seatno, user, ..)

3. API
   
  get,post,put,patch,delete

  get - when we want the data from the db
  post - when we want to post to db(create new entry).sends the complete object and                        replaces the existing resource.
  put - when we want to replace entire entry
  patch - when we want to append/modify to existing entry, partial update, update only specific entity, change only necessary
  delete - when we want to delete the entry.

GET/events?name={michael}&venue = {amb}....

GET/events/{eventid}

POST/updatebooking {seatno,}

POST/confirm {seatnp,paymentid}


4. HLD 

  
  user   <->     API Gateway             <->   Event CRUD         Primary DB
                                                                  *user
                *rate limiting                                      -id,-name, Events table(
                *Authentication                                                 -name,-id,-performer,date,venue
                *health checks                                     Seat (-booking status : free,pending,booked
                *routing                                           seatno, category,price)
                                                                   performer(id,name ,category)
                                                                   venue(address,id, seats ^PkUEml53

## Embedded Files
5da7f1612fb8f03686b6c8f533ce1ddd1e244c7e: [[shapes at 26-05-09 15.31.14.png]]

%%
## Drawing
```compressed-json
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
```
%%