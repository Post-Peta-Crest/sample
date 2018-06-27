# Process-in-Process (PiP)

## What if PiP

Process-in-Process, or PiP in short, is a library which provides you
another parallel execution mode.  Now, multi-core and many-core CPUs
are getting quite common, and people are writing and running parallel
programs on those CPUs. There are two widely used parallel execution
models; multi-process and multi-thread. The typical multi-process
model can be found in MPI programs. And the typical multi-thread model
can be found in OpenMP programs. 

A parallel program consists of several (or many) execution entities,
processes or threads, and most importantly, they communicate and/or
interact with the others. In the multi-process model, each process has
itw own virtual address space and it is not allowed to access the data
owned by the other process. In the multi-thread model, threads share
the same virtual address space, but all statically allocated variables
are shared among the thread. 

In the multi-process model, nothing is shared. This makes
inter-process communication hard. In the multi-thread model, everything
is shared. The shared variables and data must be protected to avoid
race conditions. The pros of a model can be the cons of the other
model.  There is no race condition happens on variables and data since
each process has its own variable and data in the multi-process
model. Threads can easily interact and communicate woth the thread,
since they share the same virtual address space.

There is the 3rd execution mode, which has no name yet, to
take the best of the  two worlds; multi-process and multi-thread. In
this model, variables are privatized so that each task has its own
variable set and tasks share the same virtual address space.  Here the
execution entity in this model is called *task* since it does not
follow the definitions of process and thread.  Tasks can interact and
communicate with others easily and race conditions can only happens on
the *explicitly* shared variables and/or data. Since tasks run in the
same virtual address space, any data owned by the tasks can be
accessed if the addresses of the variables and/or data are known. In
this way, the cons of the conventional models trun into the pros.

This ides is not new. However, the implementations of the 3rd
execution model requires dedicated OS kernel or specialize language
processing system consisting of compilers, linker, runtime systems,
and debugger. None of them is not easy to try and deploy. PiP is
the first implementation as a user-level library, no need of dedicated
OS kernel nor language system. Thus, PiP is very portable and easy to
try and deploy.

## Do you want to try PiP ?

We are working to make the PiP library open right now. It will be
available at https://github.com/RIKEN-SysSoft.

## Reference

_Process-in-Process: Techniques for Practical Address-Space Sharing_,
Atsushi Hori, Min Si, Balazs Gerofi, Masamichi Takagi, Jai Dayal,
Pavan Balaji and Yutaka Ishikawa. ACM HPDC 2018
The 27th International Symposium on High-Performance Parallel and
Distributed Computing Tempe, Arizona, USA - June 11-15, 2018. (winner
of the Karsten Schwan Best Paper Award)
