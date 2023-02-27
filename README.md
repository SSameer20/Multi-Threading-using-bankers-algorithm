# Multi-Threading-using-bankers-algorithm
Operating System

Q3. Write a multithreaded program that implements the banker's algorithm. Create n threads 
that request and release resources from the bank. The banker will grant the request only if it 
leaves the system in a safe state. It is important that shared data be safe from concurrent 
access.

To ensure safe access to shared data, you can use mutex locks.



Ensure:


1. The program should be dynamic such that the threads are created at run time based on 
the input from the user. 
2. The resources must be displaced after each allocation. 
3. The system state should be visible after each allocation
