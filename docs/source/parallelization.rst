****************
Parallelization
****************

Two major types of parallel programming:

* Shared memory: Running on a simple computer with multiple CPU cores/threas.
  * All cores/threads have access to the same memory. One would need to spawn multiple threads and operate simultaneously.
  * All threads/cores work on their portion of the data and merge to the same memory at last.
  * One uses **OpenMP** for such case.
    
* Distributed memory: Running on a collection of computers connected by a high-speed networl.
  * Each task cannot directly see the memory of th other task
  * Exchanging information from one machine to the other requires high-speed network
  * One use **MPI** for such case.

  
OpenMP
=======

To use **OpenMP**, include the header file ``<omp.h>``:

.. code:: c++

   #include <omp.h>

Compile code that uses **OpenMP** with flag ``-fopenmp``

.. prompt:: bash

   g++ -fopenmp -o hello hello.cpp

To initialize OpenMP directive use ``#pragma omp``.

Some useful directives:

* ``#pragma omp parallel [clause[,]clause]...]``: creates a section for parallelization. Sections can have ``{}`` to indicate, but not a must for easy expressions.
* ``#pragma omp for [clause[,]clause]...]``: declared inside a ``#pragma omp parallel`` section, used on top of the for-loop
* ``#pragma omp critical``: forces the section to execute to single thread at a time.
* ``#pragma omp parallel for [clause[,]clause]...]``: used for a quick single for-loop
* ``#pragma omp single [clause[,]clause]...]``: forces the section to perform by only 1 of the thread.
* ``#pragma omp taskwait``: specifies a wait on the completion of child tasks of the current task.

Some useful clauses:

* ``shared(list)``: declares one or more times to be shared by tasks generaed by a `parallel` or `task`
* ``private(list)``: declares one or more list items to be private to a task
* ``firprivate(list)``: declares one or more list items to be private to a task, and initializes each of them with the value that the corresponding original item has when the construct is encountered.
* ``lastprivate(list)``: declares one or more list items to be rpivate to an implicit task, and causes the corresponding original item to be updated afer the endof the region.
* ``reduction(operator:list)``: declares accumulation into the list items using the indicated **associative** operator. Accumulation occurs into a private copy for each list item which is then combined with the original item.

  * Operators for Reduction: +, \*, -, ^, \|, &, &&, ||, max, min.
  

.. tip::
   To access the number of threads used for OpenMP, it accesses the global environment ``OMP_NUM_THREADS``:

   .. prompt:: bash

      export OMP_NUM_THREADS=4

   To specify the current instance use:

   .. prompt:: bash

      OMP_NUM_THREADS=4 ./exec
   


