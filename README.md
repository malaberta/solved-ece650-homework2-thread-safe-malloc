Download Link: https://assignmentchef.com/product/solved-ece650-homework2-thread-safe-malloc
<br>
In this assignment, you are to implement two different thread-safe versions (i.e. safe for concurrent access by different threads of a process) of the malloc() and free() functions. Both of your thread-safe malloc and free functions should <strong>use the</strong> <strong>best fit allocation</strong> policy. You may implement it based on your code of project 1.

In version 1 of the thread-safe malloc/free functions, you may use lock-based synchronization to prevent race conditions that would lead to incorrect results.  These functions are to be named:

//Thread Safe malloc/free: locking version void *ts_malloc_lock(size_t size);

void ts_free_lock(void *ptr);




In version 2 of the thread-safe malloc/free functions, you may <strong>not </strong>use locks, with one exception. Because the sbrk function is not thread-safe, you may acquire a lock immediately before calling sbrk and release a lock immediately after calling sbrk.  These functions are to be named:

//Thread Safe malloc/free: non-locking version void *ts_malloc_nolock(size_t size); void ts_free_nolock(void *ptr);

To provide necessary synchronization for the locking version, you may use support from the pthread library and needed synchronization primitives (e.g. pthread_mutex_t, etc.).  Also, don’t forget about Thread-Local Storage — you may find that useful.

In order to exercise and test the thread-safe malloc routines, pthread-based multi-threaded sample programs will be provided. These programs will create threads which will make concurrent calls to the thread-safe malloc and free functions.  You are also strongly encouraged to create your own multi-threaded test programs to test your library code.  Recall that concurrent execution means that multiple threads will call the malloc and free functions, and thus may be concurrently reading and updating any shared data structures used by the malloc routines (e.g. free list information).

These test cases (and a sample Makefile for your thread-safe library code) are provided as homework2-kit.tgz.  The Makefile included in the test directory allows you to compile the tests to use either one of the two thread-safe versions (see the README.txt file for more details).

Note there is one test case that you will use for running experiments with the two different versions. This test case self-reports (1) the execution time of the test and (2) the allocation efficiency (i.e. the total size of the data segment after running the test).  You should experiment with this test in order to assess the tradeoffs in terms of performance and allocation efficiency between your locking and non-locking thread-safe versions.  This test case contains some randomized behavior, so you may need to run the test with each version several times to identify the typical behavior.

Your submitted code for the thread-safe malloc implementation will be tested against the provided sample test programs, as well as potentially additional tests. So you are encouraged to: 1) reason thoroughly through your implementation to ensure there are no race conditions, and 2) create your own additional test cases to further stress your thread-safe implementation.

As described below, you should include the source code in your submission.  Additionally, you will submit a report.  This first part of this report should describe your two thread-safe malloc implementations.  This should include a description of where your thread-safe implementation allows concurrency.  It should also describe any critical sections you identified, and your synchronization strategy to prevent race conditions.  The second part of this report should show and discuss results from your experiments with the thread_safe_measurement.c test. Based on these results, discuss any tradeoffs you identify between the two versions. <strong>Grading Rubrics </strong>

code correctness(60’), 20 test cases total code check(10’), in non-locking version, no lock except the lock for sbrk()

report(30’), description of thread-safe model, performance result presentation and comparison of locking vs. non-locking version