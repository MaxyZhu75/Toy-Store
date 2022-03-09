# :elephant: Toy Store
This lab assignment is from UMass Amherst Computer Science department- COMPSCI677 Distributed & Operating System. You will see two programming parts as follows. In the first part, we design our own thread pool and use it to write a simple client-server online store that uses network sockets. This part we will show you how thread pools work internally. In the second part, we will use gRPC and built-in thread pool mechanisms to write the client-server online store. This part will show you how we use modern frameworks to write distributed applications, since most programmers simply use higher-level abstractions than lower-level abstractions in workplace.



# Part 1 - Implementation with Socket Connection and Handwritten Thread Pool
![ProducerConsumer](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/figures/part1/ProducerConsumer.jpg)

## Problem Statement
In this part, we implemented an online Toy store as a socket-based client-server application. Our design should be able multiple client processes making **concurrent requests to the server.** The main part of the assignment is to **implement our own ThreadPool** (not allowed to use a ThreadPool framework that are available by the language/libraries).

The server component should implement a single method Query, which takes a single string argument that specifies the name of the toy. The Query method returns the dollar price of the item (as a floating point value such as 25.99) if the item is in stock. It returns -1 if the item is not found and 0 if the item is found but not in stock. The client component should connect to the server using a socket connection. It should construct a message in the form of a buffer specifying the method name (e.g., string "Query") and arguments ("toyName"). The message is sent to the server over the socket connection. The return value is another buffer containing the cost of the item or an error code such as -1 and 0, as noted above.

## Way to Approach
Please check out the [Design Document](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/design/design%20document.pdf) for details.

## Tutorial
How to run and test our code? Here we provide you examples of functional test and load test. Please check out the [Outputs](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/outputs/output.pdf) for details.

## Evaluation
A simple load test and performance measurements have been performed by us. The goal here is understand how to perform load tests on distributed applications and understand performance. Deploy more than one more client process and have each one make concurrent requests to the server. The clients should be running on a different machine than the server. Measure the latency seen by the client for different types of requests, such as query and buy.

Please check out the [Evaluation Document](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/evaluation/evaluation%20document.pdf) for details.

![evaluation](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/figures/part1/evaluation.jpg)



# Part 2 - Implementation with gRPC and Built in Thread Pool
![gRPC](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/figures/part2/gRPC.jpg)

## Problem Statement
In this part, we implemented our online Toy store using **modern gRPC framework** and **built-in thread pool support**. Our design should be able multiple client processes making **concurrent requests to the server.**

The server component should implement two gRPC calls: (1) Query(itemName), which takes the string ItemName and returns the cost of the item and real-time stock indicating how many are in stock. (2) Buy(ItemName), which buys the item and reduces the stock of that item by 1. The method returns 1 if the call succeeds, 0 if the item is not in stock and -1 if an invalid item name is specified.

We use protobuf to create appropriate message structures for arguments and return values of both calls, and design rpc methods as noted above. Since the thread pool is dynamic, we should set an appropriate max limit on the maximum number of concurrent RPCs when starting our server. Use appropriate synchronization methods on the product catalog since querying and buying will read from and write to the catalog, which make it a shared data structure. And also implement appropriate error/exception handling as needed for our design (for example, an item may be in stock when queried but stock may run out by the time the client sends a buy request)

## Way to Approach
Please check out the [Design Document](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/design/design%20document.pdf) for details.

## Tutorial
How to run and test our code? Here we provide you examples of functional test and load test. Please check out the [Outputs](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/outputs/output.pdf) for details.

## Evaluation
A simple load test and performance measurements have been performed by us. The goal here is understand how to perform load tests on distributed applications and understand performance. Deploy more than one more client process and have each one make concurrent requests to the server. The clients should be running on a different machine than the server. Measure the latency seen by the client for different types of requests, such as query and buy.

Please check out the [Evaluation Document](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/evaluation/evaluation%20document.pdf) for details.

![evaluation](https://github.com/MaxyZhu75/Toy-Store/blob/main/summary/figures/part2/evaluation.jpg)



## :calling: Contact
Thank you so much for your interests. Note that this project can not straightforward be your course assignment solution. Do not download and submit my code without any change. Feel free to reach me out and I am happy to modify this online toy store further with you.
* Email: maoqinzhu@umass.edu or zhumaxy@gmail.com
* LinkedIn: [Max Zhu](https://www.linkedin.com/in/maoqin-zhu/)
