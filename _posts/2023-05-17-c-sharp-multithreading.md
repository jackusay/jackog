---
published: true
---
## C# Multithreading

```c#
// C# program to illustrate the
// concept of multithreading
using System;
using System.Threading;

public class GFG {

	// static method one
	public static void method1()
	{

		// It prints numbers from 0 to 10
		for (int I = 0; I <= 10; I++) {
			Console.WriteLine("Method1 is : {0}", I);

			// When the value of I is equal to 5 then
			// this method sleeps for 6 seconds
			if (I == 5) {
				Thread.Sleep(6000);
			}
		}
	}

	// static method two
	public static void method2()
	{
		// It prints numbers from 0 to 10
		for (int J = 0; J <= 10; J++) {
			Console.WriteLine("Method2 is : {0}", J);
		}
	}

	// Main Method
	static public void Main()
	{

		// Creating and initializing threads
		Thread thr1 = new Thread(method1);
		Thread thr2 = new Thread(method2);
		thr1.Start();
		thr2.Start();
	}
}
```

result:
```c#
Method1 is : 0
Method1 is : 1
Method1 is : 2
Method1 is : 3
Method2 is : 0
Method2 is : 1
Method2 is : 2
Method2 is : 3
Method2 is : 4
Method2 is : 5
Method2 is : 6
Method2 is : 7
Method2 is : 8
Method2 is : 9
Method2 is : 10
Method1 is : 4
Method1 is : 5
Method1 is : 6
Method1 is : 7
Method1 is : 8
Method1 is : 9
Method1 is : 10
```

```c#
using System;
using System.Threading;
 
class Program
{
    static void Main()
    {
        // create a new thread
        Thread t = new Thread(Worker);
 
        // start the thread
        t.Start();
 
        // do some other work in the main thread
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine("Main thread doing some work");
            Thread.Sleep(100); // main thread
        }
 
        // wait for the worker thread to complete
        t.Join();
 
        Console.WriteLine("Done");
    }
 
    static void Worker()
    {
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine("Worker thread doing some work");
            Thread.Sleep(100); // worker thread
        }
    }
}
```

result:
```c#
Main thread doing some work
Worker thread doing some work
Main thread doing some work
Worker thread doing some work
Worker thread doing some work
Main thread doing some work
Main thread doing some work
Worker thread doing some work
Main thread doing some work
Worker thread doing some work
Main thread doing some work
Worker thread doing some work
Main thread doing some work
Worker thread doing some work
Main thread doing some work
Worker thread doing some work
Worker thread doing some work
Main thread doing some work
Worker thread doing some work
Main thread doing some work
Done
```

In this example, the Worker method is executed in a separate thread while the main thread is doing some other work.

---

ThreadPool class, which manages a pool of threads and can be used to execute tasks asynchronously.
```c#
using System;
using System.Threading;

class Program
{
	static void Main()
	{
		// queue a work item to the thread pool
		ThreadPool.QueueUserWorkItem(Worker, "Hello, world!");

		// do some other work in the main thread
		for (int i = 0; i < 10; i++)
		{
			Console.WriteLine("Main thread doing some work");
			Thread.Sleep(100);
		}

		Console.WriteLine("Done");
	}

	static void Worker(object state)
	{
		string message = (string)state;

		for (int i = 0; i < 10; i++)
		{
			Console.WriteLine(message);
			Thread.Sleep(100);
		}
	}
}
```

result:
```c#
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Hello, world!
Main thread doing some work
Done
```

The ThreadPool.QueueUserWorkItem method is used to queue the work item to the thread pool. The state object can be used to pass data to the worker method.

ref
https://www.geeksforgeeks.org/c-sharp-multithreading/

## Types of Threads in C#

* Foreground Threads: A foreground thread can be created by calling the Thread.Start() method.
* Background Threads: A background thread can be created by calling the Thread.Start() method and then setting the IsBackground property of the thread to true before starting it.

### Foreground Thread

Foreground thread does not care whether the main thread is alive or not, it completes only when it finishes its assigned work.

```c#
// C# program to illustrate the
// concept of foreground thread
using System;
using System.Threading;

class GFG {

	// Main method
	static void Main(string[] args)
	{

		// Creating and initializing thread
		Thread thr = new Thread(mythread); 
		thr.Start();  // foreground thread
		Console.WriteLine("Main Thread Ends!!");
	}

	// Static method
	static void mythread()
	{
		for (int c = 0; c <= 3; c++) {

			Console.WriteLine("mythread is in progress!!");
			Thread.Sleep(1000);
		}
		Console.WriteLine("mythread ends!!");
	}
}
```

result:
```c#
Main Thread Ends!!
mythread is in progress!!
mythread is in progress!!
mythread is in progress!!
mythread is in progress!!
mythread ends!!
```

## How to create Threads in C#

```c#
using System;
using System.Threading;

class Program {
	static void Main() {
		// You can use ThreadStart constructor for initializing a new instance.
		Thread thread = new Thread(new ThreadStart(Worker));
        // Or create and initialize the thread object
        // Thread thread = new Thread(Worker);
		thread.Start();

		// Do some work in the main thread
		for (int i = 0; i < 5; i++) {
			Console.WriteLine("Main thread: {0}", i);
			Thread.Sleep(100); // main thread
		}

		// Wait for the worker thread to finish
		thread.Join();
	}

	static void Worker() {
		// Do some work in the worker thread
		for (int i = 0; i < 5; i++) {
			Console.WriteLine("Worker thread: {0}", i);
			Thread.Sleep(100); // work thread
		}
	}
}
```

## How to Terminate a Thread in C#

thr.Abort();

## How to check whether a thread is alive or not in C#

```c#
// C# program to illustrate the 
// use of IsAlive property
using System;
using System.Threading;
  
public class GFG {
  
    // Main Method
    static public void Main()
    {
        Thread thr;
  
        // Get the reference of main Thread
        // Using CurrentThread property
        thr = Thread.CurrentThread;
  
        // Display the current state of 
        // the main thread Using IsAlive
        // property
        Console.WriteLine("Is main thread is alive"+
                            " ? : {0}", thr.IsAlive);
        // result: Is main thread is alive ? : True
    }
}
```

## How to check current state of a thread

thr.ThreadState // Running / Unstarted / WaitSleepJoin

## Joining Threads in C#

```c#
        Thread t1 = new Thread(() => Console.WriteLine("Thread 1"));
        Thread t2 = new Thread(() => Console.WriteLine("Thread 2"));
 
        t1.Start();
        t2.Start();
 
        t1.Join();
        t2.Join();
 
        Console.WriteLine("Main Thread");
```

or

```c#
Task.WaitAll(t1, t2);
```

## Lifecycle and States of a Thread in C#

https://www.geeksforgeeks.org/lifecycle-and-states-of-a-thread-in-c-sharp/