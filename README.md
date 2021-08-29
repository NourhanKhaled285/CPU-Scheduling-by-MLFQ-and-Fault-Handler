# CPU Scheduling by MLFQ and Fault Handler --> Operating System project


## CPU Scheduling by MLFQ
 The default scheduler in the FOS is round robin.
 
 Main drawback: favor processor-bound processes over I/O-bound processes, which results.
    
    1. in poor performance for I/O-bound processes,  
    
    2. inefficient use of I/O devices,  
    
    3. an increase in the variance of response time.
    
    Implement another scheduler algorithm which is the multilevel feedback queue MLFQ.  
    
    The main aim of the MLFQ is to establish a preference for shorter jobs by penalizing jobs that have been running longer.
    
    Scheduling is done on a preemptive (at time quantum) basis, and a dynamic priority mechanism is used.
    
    When a process first enters the system, it is placed in RQ0 (refer to Figure).
    
    After its first preemption, when it returns to the Ready state, it is placed in RQ1.
    
    Each subsequent time that it is preempted, it is demoted to the next lower-priority queue.
    
    A short process will complete quickly, without migrating very far down the hierarchy of ready queues.
    
    A longer process will gradually drift downward.
    
    Thus, newer, shorter processes are favored over older, longer processes.
    
    Within each queue, except the lowest-priority queue, a simple FIFO mechanism is used.
    
    Once in the lowest-priority queue, a process cannot go lower, but is returned to this queue repeatedly until it completes execution.
    
    Thus, this queue is treated in round-robin fashion.
    
   
   
   ## Fault Handler
   
Fault: is an exception thrown by the processor (MMU) to indicate that: 
  o A page can’t be accessed due to either it’s not present in the main memory OR.
  
  o A page table is not exist in the main memory (i.e. new table). (see the following figure).  
 

The first case (Table Fault) is already handled for you by allocating a new page table if it not exists.

Handle the page fault in FOS kernel by: 

 o Allocate a new page for this faulted page in the main memory.
 
 o Loading the faulted page back to main memory from page file if the page exists. 
 
   Otherwise if it is a stack page (i.e. new page), add it to the page file (for new STACK pages only). 
  
   If the faulted page is not a stack page, then the fault handling shall panic, since this means that the faulted address is wrong address. 
 
Handle the page fault in function:

 1. MODIFIED CLOCK with buffering.
   
 2. MODIFIED CLOCK without buffering. 
