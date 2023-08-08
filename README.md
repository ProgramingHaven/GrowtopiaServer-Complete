# Growtopia Server ![Build Status](https://ci.appveyor.com/api/projects/status/github/GrowtopiaNoobs/GrowtopiaServer)
First Growtopia Private Server made with ENet, by GrowtopiaNoobs.

This project has been compiled with Visual Studio 2022 and newer versions of VS or other compilers weren't tested.

This project has been published under GNU AFFERO GPL license, so you need to **publish whole source code and citate orginal authors name, even if you are using your server as service**!

Before GrowtopiaNoobs left the community, GrowtopiaServer was made by him. That server source had errors, and a non completed to-do list.
I Decided to complete his to-do list and share it with you guys

[  ] Refactor whole code, it is very hard readable and there might be problems with maintaining it

[  ] Try get some normal DB working or atleast save all files as BSON or some binary format

[X] Write load balancer, it is very CPU expensive part because it calculates BCrypt hashes and access to database
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
[  ] Try possible to write multiple servers which only share between themselves possibly world list, player list and boardcast queue
