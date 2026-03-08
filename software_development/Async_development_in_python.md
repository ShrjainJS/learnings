# Asynchronous Python development

`Asynchronous development is a program's ability to handle multiple things at once.`

- **Process**: Independent heavyweight instances of a program with each process having it's own sets of resources.
  - A Process is not a program, but _atleast one_ thread + resources set aside for that 'process' by the OS.
- **Thread**: Smallest units of execution in a process. All threads in a sub-process shares the same memory space

## Pyhton GIL - Global Interpreter Lock

1. In python, even when you have two threads in one process at the same time (process can have 2 or more cores as resources), it cannot run together.
2. For each process spawned Python creates a _key resource_ for the process, and when a thread is running it needs to acquire that said resource - **GIL**.
3. Python can launch multiple processes, each new process creates it's own **GIL**, it's own **thread**, and it is not easy for processes to share data between them but threads allows it.
4. _What does threads solve?_: It allows for the program to **reduce waiting time**. Ex: Having two threads with one taking a user input and print hello and another thread is for compute heacy math calculations.
   - If both the threads are compute tasks, then thread does not solve anything.
   - Since there is a user waiting period, during that time the **GIL** can be acquired by second thread, and when the input comes, **GIL** could be released by the 2nd thread and acquired by 1st User Input and Print Hello thread and then released again for the 2nd thread.
   - There is a slight compute addition by Process in accomodating the switching of threads, acquire and releasing of **GIL**, _but overall the execution of these two threads (+ overhead) would be faster than, if the two threads ran after one and another._
