# Week 02 – Inter-Process Communication (IPC)

## Module: Operating Systems
## Topic: Pipes, Named Pipes, Signals, and File-Based IPC

---

## Evidence Notice

All practical evidence for this week is provided separately in the **/screenshots** directory.
The screenshots demonstrate terminal output and correct execution of each task described below, including pipes, named pipes, signal handling, and file-based IPC.

---

## 1. Introduction

This week focused on understanding **Inter-Process Communication (IPC)** mechanisms in Unix-based operating systems. IPC enables independent processes to exchange data and coordinate execution safely. Through a series of practical tasks, I implemented and tested **pipes**, **named pipes (FIFOs)**, **process signals**, **signal handling**, and a **file-based producer–consumer model**. The attached screenshots provide evidence of correct implementation and expected behaviour.

---

## 2. Task 1.1 – Pipes and Redirection

Standard streams (`stdin`, `stdout`, `stderr`) were explored using redirection operators and pipes. Output redirection was used to write and append data to files, while error redirection captured error messages for debugging purposes.

Pipes (`|`) were used to connect multiple commands together, allowing the output of one process to become the input of another. Examples included filtering directory listings, counting running processes, and processing system files. These exercises demonstrated how Unix systems support efficient process cooperation and data flow without intermediate files.

---

## 3. Task 1.2 – Named Pipes (FIFOs)

Named pipes were created using the `mkfifo` command to enable communication between unrelated processes in different terminals. Writing to a FIFO was observed to block until a reader was available, demonstrating built-in synchronisation.

A producer–consumer pattern was implemented using a named pipe, where one process generated data items and another consumed them in real time. This highlighted the difference between anonymous pipes, which are temporary and command-based, and named pipes, which persist as filesystem objects.

---

## 4. Task 1.3 – Process Signals

Process signals were explored to understand how the operating system communicates with running processes. Signals such as `SIGTERM`, `SIGKILL`, and job control signals (`SIGTSTP`, `bg`, `fg`) were used to manage process execution.

These experiments demonstrated the difference between graceful termination and forced termination, as well as how processes can be suspended and resumed. This task reinforced the importance of understanding process lifecycle management.

---

## 5. Signal Handling in Robust Applications

A signal handling script was implemented using the `trap` command to catch `SIGINT` and `SIGTERM`. The script demonstrated how a running process can intercept signals and terminate gracefully while performing cleanup actions.

Signal handling is critical in robust applications because processes may be interrupted unexpectedly. Without proper handling, resources such as lock files may remain, causing deadlocks or preventing other processes from continuing.

---

## 6. Task 1.4 – File-Based IPC (Producer–Consumer Model)

A file-based IPC system was implemented using two Bash scripts:

- A **producer** script that writes timestamped data items to a shared file
- A **consumer** script that monitors the file in real time

A lock file was used to enforce mutual exclusion, ensuring that only one process could write to the shared file at a time. This prevented race conditions and ensured data integrity. The consumer used `tail -f` to display new data as it was written.

---

## 7. Synchronisation and Race Conditions

A race condition occurs when multiple processes access shared resources without coordination. In the file-based IPC example, the lock file mechanism prevented concurrent writes and ensured safe access to shared data. This approach reflects real operating system synchronisation techniques such as mutexes and semaphores.

---

## 8. Importance of Signal Handling

Signal handling ensures that applications can respond safely to interruptions. By cleaning up resources and releasing locks before termination, signal handling improves system reliability and prevents deadlocks. This is especially important in concurrent and multi-process environments.

---

## 9. Conclusion

This week provided practical insight into how Unix-based operating systems manage inter-process communication and synchronisation. By implementing pipes, named pipes, signal handling, and file-based IPC, I gained a deeper understanding of process cooperation, race conditions, and robustness. These concepts form a strong foundation for more advanced IPC mechanisms such as message queues, shared memory, and sockets.

---

## 📁 Evidence Location

All screenshots demonstrating the successful execution of the above tasks are provided in the **/screenshots** directory.

---

✅ **Week 02 completed**
