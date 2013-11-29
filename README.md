GCD
===

中央调度队列
About Dispatch Queues

Dispatch queues are an easy way to perform tasks asynchronously and concurrently in your application. A task is simply some work that your application needs to perform. For example, you could define a task to perform some calculations, create or modify a data structure, process some data read from a file, or any number of things. You define tasks by placing the corresponding code inside either a function or a block object and adding it to a dispatch queue.

A dispatch queue is an object-like structure that manages the tasks you submit to it. All dispatch queues are first-in, first-out data structures. Thus, the tasks you add to a queue are always started in the same order that they were added. GCD provides some dispatch queues for you automatically, but others you can create for specific purposes. Table 3-1 lists the types of dispatch queues available to your application and how you use them.
