# Growtopia Server ![Build Status](https://ci.appveyor.com/api/projects/status/github/GrowtopiaNoobs/GrowtopiaServer)
First Growtopia Private Server made with ENet, by GrowtopiaNoobs.

This project has been compiled with Visual Studio 2022 and newer versions of VS or other compilers weren't tested.

This project has been published under GNU AFFERO GPL license, so you need to **publish whole source code and citate orginal authors name, even if you are using your server as service**!

Before GrowtopiaNoobs left the community, GrowtopiaServer was made by him. That server source had errors, and a non completed to-do list.
I Decided to complete his to-do list and share it with you guys

# Growtopia Noobs's To-Do List

**-Refactor whole code, it is very hard readable and there might be problems with maintaining it**
(Not Yet)

**-Try get some normal DB working or atleast save all files as BSON or some binary format**
(Not Yet)

**-Write load balancer, it is very CPU expensive part because it calculates BCrypt hashes and access to database**
```
Usage:
  // Create a load balancer with a certain number of worker threads
    LoadBalancer loadBalancer(4);
 ```

```
// Simulate incoming requests
    for (int i = 0; i < 10; ++i) {
        loadBalancer.addTask([]() {
            // Simulate CPU-intensive work (e.g., BCrypt hashing)
            // and database access here
            std::this_thread::sleep_for(std::chrono::seconds(2));
            std::cout << "Task completed by thread: " << std::this_thread::get_id() << std::endl;
        });
    }
 ```

```
 // Allow some time for tasks to complete
    std::this_thread::sleep_for(std::chrono::seconds(15));
```
**-Try possible to write multiple servers which only share between themselves possibly world list, player list and boardcast queue**
(Not Yet)

**-Extend data which are saved now - there should be saved current clothes, inventory, login time, register time and maybe tracing hashes if you want to do proper ban system also in worlds there should be saved block extras (enabled, water, fire, etc.) and dropped items**
(Not Yet)

**-Write event pool - this is used to delay actions**
Include:
```
EventPool eventPool;
```
Add Event:
```
   eventPool.addEventListener<MyEvent>([]() {
        std::cout << "MyEvent triggered!" << std::endl;
        // Simulate heavy computation
        std::this_thread::sleep_for(std::chrono::seconds(2));
        std::cout << "MyEvent processing complete." << std::endl;
    });
```
Start Event:
```
   eventPool.startEventProcessingThreads(2);
```
Trigger Event:
```
   eventPool.triggerEventAsync<MyEvent>();
```
Sleep Action:
```
   std::this_thread::sleep_for(std::chrono::seconds(1));
```
Stop Event:
```
   eventPool.stopEventProcessingThreads();
```
**-Make heavy events asynchronous with possibly some good thread count (probably one or two) and connect them to event pool or use callbacks**
(Done, in event pool)
**-Daily news (Growtopia Gazzete) should be saved to external file and not in source for easier modifying**
(Done, news.txt)
