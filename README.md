# Bankers-algorithm
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







                    Banker’s Algorithm in Operating System

The banker’s algorithm is a resource allocation and deadlock avoidance algorithm that tests for safety by simulating the allocation for predetermined maximum possible amounts of all resources, then makes an “s-state” check to test for possible activities, before deciding whether allocation should be allowed to continue.


Why Banker’s algorithm is named so? 


Banker’s algorithm is named so because it is used in banking system to check whether loan can be sanctioned to a person or not. Suppose there are n number of account holders in a bank and the total sum of their money is S. If a person applies for a loan then the bank first subtracts the loan amount from the total money that bank has and if the remaining amount is greater than S then only the loan is sanctioned. It is done because if all the account holders comes to withdraw their money then the bank can easily do it.
In other words, the bank would never allocate its money in such a way that it can no longer satisfy the needs of all its customers. The bank would try to be in safe state always

.
Following Data structures are used to implement the Banker’s Algorithm:

Let ‘n’ be the number of processes in the system and ‘m’ be the number of resources types.
Available :  
 
It is a 1-d array of size ‘m’ indicating the number of available resources of each type.
Available[ j ] = k means there are ‘k’ instances of resource type Rj

Max : 
 

It is a 2-d array of size ‘n*m’ that defines the maximum demand of each process in a system.
Max[ i, j ] = k means process Pi may request at most ‘k’ instances of resource type Rj.


Allocation : 

It is a 2-d array of size ‘n*m’ that defines the number of resources of each type currently allocated to each process.
Allocation[ i, j ] = k means process Pi is currently allocated ‘k’ instances of resource type Rj.

Need : 
 
It is a 2-d array of size ‘n*m’ that indicates the remaining resource need of each process.
Need [ i,   j ] = k means process Pi currently need ‘k’ instances of resource type Rj
Need [ i,   j ] = Max [ i,   j ] – Allocation [ i,   j ]

Allocationi specifies the resources currently allocated to process Pi and Needi specifies the additional resources that process Pi may still request to complete its task.
Banker’s algorithm consists of Safety algorithm and Resource request algorithm
Safety Algorithm
The algorithm for finding out whether or not a system is in a safe state can be described as follows: 
 

1) Let Work and Finish be vectors of length ‘m’ and ‘n’ respectively. 
Initialize: Work = Available 
Finish[i] = false; for i=1, 2, 3, 4….n
2) Find an i such that both 
a) Finish[i] = false 
b) Needi <= Work 
if no such i exists goto step (4)
3) Work = Work + Allocation[i] 
Finish[i] = true 
goto step (2)
4) if Finish [i] = true for all i 
then the system is in a safe state 
 

Resource-Request Algorithm
Let Requesti be the request array for process Pi. Requesti [j] = k means process Pi wants k instances of resource type Rj. When a request for resources is made by process Pi, the following actions are taken:
 

1) If Requesti <= Needi 
Goto step (2) ; otherwise, raise an error condition, since the process has exceeded its maximum claim.
2) If Requesti <= Available 
Goto step (3); otherwise, Pi must wait, since the resources are not available.
3) Have the system pretend to have allocated the requested resources to process Pi by modifying the state as 
follows: 
Available = Available – Requesti 
Allocationi = Allocationi + Requesti 
Needi = Needi– Requesti
 

Example:
Considering a system with five processes P0 through P4 and three resources of type A, B, C. Resource type A has 10 instances, B has 5 instances and type C has 7 instances. Suppose at time t0 following snapshot of the system has been taken:
 

safety
