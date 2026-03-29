# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:**

process has its own memory space and system resources ,while thread is a smaller unit that run inside process and shares same memory with other thread,thread are lightweight and allow
faster context while process is heavy and require more overhead to creat an mange,we used thread because multiple task need to run conncurrently whie sharing same data structure
--> Thread thread = new Thread(process); we created thread by creat object and linking thread with process
---> processQueue.add(thread); put thread in ready queue to choose
 contextswitchcount++--> that means thread share same memory

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**
in Round ronin  when a process doesn't finish within its time quantum, process stop temporarily (preemption) and it return to ready queue and according to order cpu choose another process


Example from my output:
```
P1 executing quantum [5000ms]
  ? Quantum progress: [███████████████] 100%
  ? P1 completed quantum 5000ms │ Overall progress: [████████████░░░░░░░░] 63%
     Remaining time: 2900ms
  ? P1 yields CPU for context switch
```

**Explanation of example:**
p1 has time quantum=5000ms
it progress only 63% and has remainig time =2900ms so it return to ready queue and according to Round robin algorithm p1 will be  last one and cpu will choose another process in order 

---

## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**

[Write your answer here. For each state, explain when P1 enters that state during the simulation. Use your understanding of the code to trace through the lifecycle.]

1. **New**: P1 is i n new state -> after new process is called in addprocesstoqueue() creating the thread before it stats-new procees will be in queue before take it by cpu 

2. **Runnable**: p1 become runnable when currentthread.start() is called in the main scheduling loop,making it ready for cpu.

3. **Running**: p1 is running when operating system scheduler patches/select the p1 and begins executing the run() method,calculating run time and processing its quantum

4. **Waiting**: p1 is become in waiting state when thread.sleep(sleepTime) is called during execution to simulate work progress   
the main thread also wais via currentthread.join() for p1 to complete

5. **Terminated**: p1 is terminated whent the run() method return normally after completing its quantum or finishing entirely via runtocompletion()

---

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: web sever handling multiple requests 

**Description**: 
when web server receives many user requests at the same time for loading page,images or data .
each request is handled by separte thread and all thread need to cpu time to respone users 

**Why Round-Robin works well here**: 
(RR) scheduling gives each thread fixed time (quantum) ensuring that all requests handled quickly.this improve responsivness

### Example 2:Time sharing (os)

**Description**: 
multiple users run programs on the same system at the same time

**Why Round-Robin works well here**: 
it gives each user equal cpu time,ensuring fairness and quick respone without one user dominating the system

---

## Summary

**Key concepts I understood through these questions:**
1.how to apply RR and the cocept of Roud robin  
2. how linking the question one/two with example in my program 
3. the concept of context switching

**Concepts I need to study more:**
1. the diference between sjf,fcfs algorits
2. how accuratly calculate turnaround  
