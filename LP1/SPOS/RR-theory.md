Definition
Round Robin (RR) is a:Preemptive CPU Scheduling Algorithm where each process gets CPU for a fixed amount of time called: Time Quantum

After quantum expires:process is interrupted moved to end of ready queue next process gets CPU

2. Theory Concepts Used
Concept	Meaning
Process	- Program under execution
CPU Scheduling- Selecting process for execution
Preemptive Scheduling -	CPU can be taken away
Ready Queue -	Queue of waiting processes
Time Quantum -	Fixed execution time
Context Switching	-Switching CPU between processes

3. Scheduling Parameters
Arrival Time (AT)
Definition
Time at which process enters ready queue.
Example:
P1 arrives at time 0


Burst Time (BT)
Definition
Total CPU execution time required by process.
Example:
P1 needs 5 ms CPU time


Completion Time (CT)
Definition
Time at which process finishes execution.


Turn Around Time (TAT)
Definition
Total time spent in system.
Formula:
TAT=CT−AT

Waiting Time (WT)
Definition
Time process waits in ready queue.
Formula:
WT=TAT−BT

Time Quantum
Definition
Fixed CPU execution slice given to each process.
Example:
Quantum = 2 ms





===============================
ROUND ROBIN SCHEDULING THEORY
===============================

1. IMPORT STATEMENT
-------------------

import java.util.*;

What is Package?
----------------
A Java package is a collection of related classes and interfaces.

Why java.util Package Used?
---------------------------
The java.util package contains utility classes required in this program.

Classes Used:
1. Scanner
2. Queue
3. LinkedList


==================================================

2. CLASS DECLARATION
--------------------

public class RoundRobin

Theory of Class
---------------
A class is a blueprint or template used to create objects and organize program structure.

Here:
RoundRobin → Class Name

public
------
Accessible from anywhere.

==================================================

3. MAIN FUNCTION
----------------

public static void main(String[] args)

Why main() Important?
---------------------
Program execution starts from main() function.

Breakdown of Terms
------------------

public
→ Accessible globally.

static
→ No object creation required to call main().

void
→ Function returns no value.

main
→ Entry point of Java program.

String[] args
→ Stores command-line arguments.


==================================================

4. SCANNER OBJECT
-----------------

Scanner sc = new Scanner(System.in);

Theory of Scanner
-----------------
Scanner is a predefined Java class used for taking runtime input from user.

Object Creation
---------------
new Scanner()

Creates Scanner object in memory.

System.in
---------
Represents keyboard input stream.


==================================================

5. NUMBER OF PROCESSES
----------------------

int n = sc.nextInt();

int
---
Used to store integer values.

nextInt()
---------
Reads integer input from keyboard.


==================================================

6. ARRAYS
---------

int[] at = new int[n];

What is Array?
--------------
An array is a collection of same datatype variables stored in contiguous memory locations.

Why Arrays Used?
----------------
Because multiple processes exist and each process has:
- Arrival Time
- Burst Time
- Waiting Time
- Turnaround Time

Array Indexing
--------------
If:
n = 4

Indexes are:
0 1 2 3


==================================================

7. TYPES OF ARRAYS USED
-----------------------

1. Arrival Time Array
---------------------

at[i]

Stores arrival time of process.

Example:
at[0] = Arrival time of P1


2. Burst Time Array
-------------------

bt[i]

Stores CPU burst time.


3. Remaining Time Array
-----------------------

rem[i]

Stores remaining CPU time after partial execution.


Why Remaining Time Needed?
--------------------------
Because Round Robin scheduling does not complete process in one attempt.

Process executes multiple times.


Example
-------

If:
BT = 10
Quantum = 3

Execution:

Turn                Remaining Time
----------------------------------
Start               10
After 1st Turn       7
After 2nd Turn       4
After 3rd Turn       1
After 4th Turn       0


==================================================

8. INPUT LOOP
-------------

for (int i = 0; i < n; i++)

Theory of for Loop
------------------
Used when number of repetitions is known.


Loop Components
---------------

Initialization:
int i = 0

Starts counter from 0.


Condition:
i < n

Loop runs until last process.


Increment:
i++

Moves to next process.


==================================================

9. REMAINING TIME INITIALIZATION
--------------------------------

rem[i] = bt[i];

Meaning
-------
Initially:
Remaining Time = Burst Time

Because process has not executed yet.


==================================================

10. TIME QUANTUM
----------------

int q = sc.nextInt();

What is Time Quantum?
---------------------
Fixed CPU time allocated to each process.


Importance of Quantum
---------------------
Quantum size determines:
1. Response time
2. Context switching overhead


Very Small Quantum
------------------

Example:
q = 1

Problem:
Too many context switches occur.


Very Large Quantum
------------------

Problem:
Round Robin behaves like FCFS scheduling.


==================================================

11. QUEUE
---------

Queue<Integer> queue = new LinkedList<>();

Why Queue Used?
---------------
Round Robin follows FIFO scheduling.


FIFO Meaning
------------
First process entering queue gets CPU first.


LinkedList
----------
Used to implement queue dynamically.


==================================================

12. BOOLEAN ARRAY
-----------------

boolean[] inQ = new boolean[n];

Why Needed?
------------
Without this:
- Same process may enter queue multiple times
- Duplicate scheduling occurs


==================================================

13. MAIN SCHEDULING LOOP
------------------------

while(done < n)

Meaning
-------
Continue scheduling until all processes complete execution.


==================================================

14. PROCESS ARRIVAL CHECK
-------------------------

if (at[i] <= time && rem[i] > 0 && !inQ[i])

Condition Explanation
---------------------

1. at[i] <= time
----------------
Checks whether process has arrived.

2. rem[i] > 0
--------------
Checks whether process is incomplete.

3. !inQ[i]
-----------
Checks whether process is absent from queue.


==================================================

15. ADD PROCESS TO QUEUE
------------------------

queue.add(i);

Meaning
-------
Adds process to ready queue.


==================================================

16. QUEUE EMPTY CONDITION
-------------------------

if(queue.isEmpty())

Meaning
-------
No process available currently.

CPU becomes IDLE.


==================================================

17. TIME INCREMENT
------------------

time++;

Meaning
-------
System clock advances by 1 unit.


==================================================

18. CONTINUE STATEMENT
----------------------

continue;

Meaning
-------
Skips remaining statements and restarts loop.


==================================================

19. REMOVE PROCESS FROM QUEUE
-----------------------------

int i = queue.poll();

poll()
------
Removes front process from queue for CPU execution.


==================================================

20. Math.min()
--------------

int run = Math.min(rem[i], q);

Why Needed?
------------
Suppose:

Remaining Time = 1
Quantum = 3

Process only needs:
1 unit

not full quantum.


==================================================

21. REDUCE REMAINING TIME
-------------------------

rem[i] -= run;

Meaning
-------
Subtracts executed CPU time from remaining burst time.


==================================================

22. UPDATE CURRENT TIME
-----------------------

time += run;

Meaning
-------
CPU clock moves ahead after execution.


==================================================

23. PROCESS COMPLETION CHECK
----------------------------

if(rem[i] == 0)

Meaning
-------
Process completely finished execution.


==================================================

24. COMPLETION TIME
-------------------

ct[i] = time;

Meaning
-------
Stores finishing time of process.


==================================================

25. TURNAROUND TIME
-------------------

tat[i] = ct[i] - at[i];

Formula:
--------
TAT = CT - AT

Meaning
-------
Total time process stayed inside system.

Includes:
1. Waiting Time
2. Execution Time


==================================================

26. WAITING TIME
----------------

wt[i] = tat[i] - bt[i];

Formula:
--------
WT = TAT - BT

Meaning
-------
Actual time process waited without CPU inside ready queue.


==================================================

27. REINSERT PROCESS
--------------------

queue.add(i);

Meaning
-------
If process unfinished:
- Return process to queue tail
- Wait for next turn


==================================================

28. AVERAGE WAITING TIME
------------------------

avgWT / n

Meaning
-------
Average CPU waiting delay of all processes.


==================================================

29. AVERAGE TURNAROUND TIME
---------------------------

avgTAT / n

Meaning
-------
Average total completion time of all processes.


==================================================

30. DEEP INTERNAL WORKING EXAMPLE
---------------------------------

Suppose:

Process     AT      BT
-----------------------
P1          0       5
P2          1       4
P3          2       2

Quantum = 2


Execution Sequence
------------------

Time        Process
-------------------
0-2         P1
2-4         P2
4-6         P3
6-8         P1
8-10        P2
10-11       P1


Observation
-----------
Each process gets fair CPU opportunity.


==================================================

31. WHY ROUND ROBIN BETTER THAN FCFS?
-------------------------------------

Problem in FCFS
---------------
Long process blocks short processes.

This problem is called:
Convoy Effect


Round Robin Solution
--------------------
Uses:
Time Slicing

Each process gets fixed CPU time.


==================================================

32. ADVANTAGES OF ROUND ROBIN
-----------------------------

1. Fair scheduling
2. Good response time
3. Suitable for multitasking
4. Prevents starvation


==================================================

33. DISADVANTAGES OF ROUND ROBIN
--------------------------------

1. More context switching
2. Quantum selection difficult
3. Too small quantum reduces efficiency


==================================================

34. IMPORTANT TERMS SUMMARY
---------------------------

AT  → Arrival Time
BT  → Burst Time
CT  → Completion Time
WT  → Waiting Time
TAT → Turnaround Time
RR  → Round Robin
CPU → Central Processing Unit
FIFO → First In First Out


==================================================

35. FINAL VIVA ANSWER
---------------------

Round Robin is a preemptive CPU scheduling algorithm in which each process gets fixed CPU time quantum in cyclic order using FIFO queue scheduling.

==================================================
