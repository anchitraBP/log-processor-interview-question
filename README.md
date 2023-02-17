# Requirements
You are to design and implement a Scala program that processes multiple large Apache log files, sorts the logs based on certain criteria,
and then aggregate the processed logs for further analysis.

The log files are in the Apache format, with each line representing a single log entry.
Each log entry should be in the format:
```bash
[IP address] - - [timestamp] "request" [response code] - - "user agent" [response time]
```

An example of a log file content is shown below:
```bash
51.58.231.134 - - [18/Nov/2021:05:53:19] "DELETE /usr/admin HTTP/1.0" 404 - - "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_3) AppleWebKit/537.75.14 (KHTML, like Gecko) Version/7.0.3 Safari/7046A194A" 252
6.145.220.184 - - [28/Jan/2022:12:50:21] "DELETE /usr/register HTTP/1.0" 404 - - "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:84.0) Gecko/20100101 Firefox/84.0" 3974
150.126.201.66 - - [11/May/2021:05:36:30] "DELETE /usr/login HTTP/1.0" 304 - - "Mozilla/5.0 (Linux; Android 10; ONEPLUS A6000) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Mobile Safari/537.36" 478
```

The program should be designed using Object-Oriented Programming (OOP) concepts and also should have the following classes:

1. `LogProcessor`: This class should be responsible for reading and parsing the Apache log files, extracting relevant information and creating a Log object.
It should have a method `processLogs(file: File): List[Log]` that takes a single argument, the `file` which is a `java.io.File` object representing the file to read and returns a list of Log objects.
2. `LogSorter`: This class should be responsible for sorting the list of Log objects based on certain criteria (e.g. timestamp, Ip address, request type). 
It should have a method `sortLogs(logs: List[Log], criteria: String): List[Log]` that takes two arguments, the `logs` which is a list of Log objects, and `criteria` which is string representing the sorting criteria, and returns a list of Log objects sorted based on the given criteria.
3. `LogAggregator`: This class should be responsible for aggregating the sorted logs based on certain criteria (e.g. IP address, request type, response code, etc.) and generating statistics such as total number of requests and average response time. 
It should have a method `aggregateLogs(logs: List[Log], criteria: String): Map[String, Statistics]` that takes two arguments, the `logs` which is a list of Log objects, and `criteria` which is a string representing the aggregation criteria, and returns a map of statistics where the key is the criteria and the value is a Statistic object.
4. `Main`: This class should be responsible for creating an instance of `LogProcessor`, processing the log files, creating an instance of `LogSorter`, sorting the logs, creating a instance of `LogAggregator`, aggregating the logs, and finally displaying the statistics. The main method should accept three arguments as follows:
   1. arg1: absolute path to the directory containing log files, 
   2. arg2: criteria to sort,
   3. arg3: criteria to aggregate.

Additionally, your program should have the following goals:
1. Implement a mechanism to handle errors and exceptions in the log files and skipping invalid log entries.
2. Implement a multithreading mechanism in the `LogProcessor` class to improve the performance of processing large number of log files in parallel.
3. Implement a mechanism to handle log files compressed in gzip format and decompressing them before processing.
