GCD
===

中央调度队列
About Dispatch Queues

Dispatch queues are an easy way to perform tasks asynchronously and concurrently in your application. A task is simply some work that your application needs to perform. For example, you could define a task to perform some calculations, create or modify a data structure, process some data read from a file, or any number of things. You define tasks by placing the corresponding code inside either a function or a block object and adding it to a dispatch queue.
调度队列使程序更加容易异步和并发。使得执行任务更加方便。比方说你定义一个任务来执行一些操作，创建或者修改一个数据结构。从文件中处理一些数据。你通过将相应的代码或者一个函数或块对象内并将其添加到一个调度队列定义任务。

A dispatch queue is an object-like structure that manages the tasks you submit to it. All dispatch queues are first-in, first-out data structures. Thus, the tasks you add to a queue are always started in the same order that they were added. GCD provides some dispatch queues for you automatically, but others you can create for specific purposes. Table 3-1 lists the types of dispatch queues available to your application and how you use them.
一个调度队列像一个对象结构管理你提交的任务。所有的队列都是先进先出数据结构。这造成你添加进队列中的任务总是按照添加的顺序来执行。GCD自动提供一些队列给你，但是其他用图你的需要自己创建，下面是系统提供的调度队列


Table 3-1  Types of dispatch queues 
Serial

Serial queues (also known as private dispatch queues) execute one task at a time in the order in which they are added to the queue. The currently executing task runs on a distinct thread (which can vary from task to task) that is managed by the dispatch queue. Serial queues are often used to synchronize access to a specific resource.
You can create as many serial queues as you need, and each queue operates concurrently with respect to all other queues. In other words, if you create four serial queues, each queue executes only one task at a time but up to four tasks could still execute concurrently, one from each queue. For information on how to create serial queues, see “Creating Serial Dispatch Queues.”

Concurrent

Concurrent queues (also known as a type of global dispatch queue) execute one or more tasks concurrently, but tasks are still started in the order in which they were added to the queue. The currently executing tasks run on distinct threads that are managed by the dispatch queue. The exact number of tasks executing at any given point is variable and depends on system conditions.
In iOS 5 and later, you can create concurrent dispatch queues yourself by specifying DISPATCH_QUEUE_CONCURRENT as the queue type. In addition, there are four predefined global concurrent queues for your application to use. For more information on how to get the global concurrent queues, see “Getting the Global Concurrent Dispatch Queues.”

Main dispatch queue

The main dispatch queue is a globally available serial queue that executes tasks on the application’s main thread. This queue works with the application’s run loop (if one is present) to interleave the execution of queued tasks with the execution of other event sources attached to the run loop. Because it runs on your application’s main thread, the main queue is often used as a key synchronization point for an application.
Although you do not need to create the main dispatch queue, you do need to make sure your application drains it appropriately. For more information on how this queue is managed, see “Performing Tasks on the Main Thread.”
