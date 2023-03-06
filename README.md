# Readers_writers_starvation_free
The writers-readers problem is an synchronization problem.We have learned about the first readers-writers problem where readers given priority and also second readers problem where writers are given priority but here we are going to implement the starvation free readers-writers problem.
## Semaphores_used
    -> mutex (it ensures atomicity of read_cnt)
    -> s1 (it ensures mutual exclusion in writers problem) 
    -> s3 (it ensures that all reads are comppleted and it time for writers to execute)
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
