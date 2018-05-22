---
Description: 'Terminating a thread has the following results:Any resources owned by the thread, such as windows and hooks, are freed.The thread exit code is set.The thread object is signaled.If the thread is the only active thread in the process, the process is terminated. For more information, see Terminating a Process.'
ms.assetid: '633e5d0c-e9d8-4f9a-9411-17cbe9e2e6e4'
title: Terminating a Thread
---

# Terminating a Thread

Terminating a thread has the following results:

-   Any resources owned by the thread, such as windows and hooks, are freed.
-   The thread exit code is set.
-   The thread object is signaled.
-   If the thread is the only active thread in the process, the process is terminated. For more information, see [Terminating a Process](terminating-a-process.md).

The [**GetExitCodeThread**](getexitcodethread.md) function returns the termination status of a thread. While a thread is executing, its termination status is STILL\_ACTIVE. When a thread terminates, its termination status changes from STILL\_ACTIVE to the exit code of the thread.

When a thread terminates, the state of the thread object changes to signaled, releasing any other threads that had been waiting for the thread to terminate. For more about synchronization, see [Synchronizing Execution of Multiple Threads](synchronizing-execution-of-multiple-threads.md).

When a thread terminates, its thread object is not freed until all open handles to the thread are closed.

## How Threads are Terminated

A thread executes until one of the following events occurs:

-   The thread calls the [**ExitThread**](exitthread.md) function.
-   Any thread of the process calls the [**ExitProcess**](exitprocess.md) function.
-   The thread function returns.
-   Any thread calls the [**TerminateThread**](terminatethread.md) function with a handle to the thread.
-   Any thread calls the [**TerminateProcess**](terminateprocess.md) function with a handle to the process.

The exit code for a thread is either the value specified in the call to [**ExitThread**](exitthread.md), [**ExitProcess**](exitprocess.md), [**TerminateThread**](terminatethread.md), or [**TerminateProcess**](terminateprocess.md), or the value returned by the thread function.

If a thread is terminated by [**ExitThread**](exitthread.md), the system calls the entry-point function of each attached DLL with a value indicating that the thread is detaching from the DLL (unless you call the [**DisableThreadLibraryCalls**](base.disablethreadlibrarycalls) function). If a thread is terminated by [**ExitProcess**](exitprocess.md), the DLL entry-point functions are invoked once, to indicate that the process is detaching. DLLs are not notified when a thread is terminated by [**TerminateThread**](terminatethread.md) or [**TerminateProcess**](terminateprocess.md). For more information about DLLs, see [Dynamic-Link Libraries](base.dynamic_link_libraries).

The [**TerminateThread**](terminatethread.md) and [**TerminateProcess**](terminateprocess.md) functions should be used only in extreme circumstances, since they do not allow threads to clean up, do not notify attached DLLs, and do not free the initial stack. In addition, handles to objects owned by the thread are not closed until the process terminates. The following steps provide a better solution:

-   Create an event object using the [**CreateEvent**](base.createevent) function.
-   Create the threads.
-   Each thread monitors the event state by calling the [**WaitForSingleObject**](base.waitforsingleobject) function. Use a wait time-out interval of zero.
-   Each thread terminates its own execution when the event is set to the signaled state ([**WaitForSingleObject**](base.waitforsingleobject) returns WAIT\_OBJECT\_0).

 

 


