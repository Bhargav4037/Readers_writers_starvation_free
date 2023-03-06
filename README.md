# Readers_writers_starvation_free
The writers-readers problem is an synchronization problem.We have learned about the first readers-writers problem where readers given priority and also second readers problem where writers are given priority but here we are going to implement the starvation free readers-writers problem.
## Semaphores_used
-> mutex (it ensures atomicity os read_cnt)
-> s1 (it ensures mutual exclusion in writers problem)
-> s3 (it ensures that all reads are comppleted and it time for writers to execute)
