# Readers_writers_starvation_free
The writers-readers problem is a synchronization problem.We have learned about the first readers-writers problem where readers given priority and also second readers problem where writers are given priority but here we are going to implement the starvation free readers-writers problem.
## Semaphores_used
    -> mutex (it ensures atomicity of read_cnt)
    -> s1 (it ensures mutual exclusion in writers problem) 
    -> s3 (it ensures that all reads are completed and it's time for writers to execute)
## Initialisation_of_semaphores_and_variables
    -> mutex    = 1
    -> s1       = 1
    -> s3       = 1
    -> read_cnt = 0
    -> wrt_cnt  = 0
## Wait_and_signal_declarations
``` cpp
    WAIT(S){
                      while(S->value<=0){
                           ; //no-operation
                      }
                       S->value--;
                 }
                                             
     SIGNAL(S){
                     S->value++;
                 }
```
# Solution_of_starvation_free
We are implementing it using two queues,one for writers and other for readers if readers queue is empty then we add write process to writers queue and vice versa.This resolves the problem of the starvation as we are considering all readers coming at a time as one unit and executing at a time and then writers so no one starves.Hence the problem of starvation is resolved.s3 makes sure that of all readers are completed and now its time for writers to execute simillarly the reverse for s1.
## Pseudo-code_for_writers 
``` cpp
    wait(s1);

wrt_cnt++;

if(wrt_cnt == 1) wait(s3);

   .........

    //writing is performed 

   .........

wrt_cnt--;

if(wrt_cnt == 0) signal(s3);

signal(s1);
```
## Pseudo-code_for_readers
``` cpp
    wait(s3);

read_cnt++;

if (read_cnt == 1) wait(s1);

signal(mutex);

signal(s3);

    ........

//reading is performed

    ........

wait(mutex);

read_cnt--;

if (read_cnt == 0) signal(s1);

signal(mutex);
```
