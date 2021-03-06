# Part 2: Parallel Programming using Intel Threading Building Blocks

In the last part of the course you learned how to write C++ programs
in a functional programing style. This allowed you to express your
algorithm in terms of the collective map/reduce operation, which was
then efficiently parallelised via a parallel implementation of
the `mapReduce` function.

To write efficient parallel C++ code you need to think of your algorithm
at this higher level of collective operations. Such 
higher-level abstractions are inherently easily parallelisable, 
and can be parallelised efficiently across large numbers of cores
of many-core and massively many-core processors (e.g. modern Xeon
or Xeon Phi processors). By structuring your program into algorithms
at this high level, you then make it easier to add efficient parallelism.

In this section we will explore how to actually write the parallel
code that lies behind these collective operations. You will need to know
this either because;

* you need to write your own implementation of a collective operation, like 
your own version of `mapReduce`, or
* you cannot express your algorithm cleanly as a set of collective operations, so
you need to parallelise your code at a lower level.

There are many tools to write low-level parallel code, i.e. OpenMP or MPI.

My personal favorite tool to add parallelism is 
[Intel's Threading Building Blocks (TBB)](https://www.threadingbuildingblocks.org).
TBB is a good choice,
as it implements an efficient task-based scheduler that supports
multi-level parallelism. While it has been written by Intel, TBB is
inherently portable and is a free (apache license), and is an excellent choice for adding
parallelisation to your C++ code. More importantly, it supports nested parallelism.
This means that you can write parallel code that itself calls functions that
involve parallel code, with you being safe in the knowledge that multiple
levels of parallelism will not overload your computer.

In this part of the course you will learn the basics of Intel's TBB.
You will then see how TBB can be used to write your own parallel `mapReduce`
function. We will then look at the underlying
technology of TBB, i.e. tasks, and the TBB task scheduler.

If you want to see how TBB has been used to parallelise a large application,
then take a look at [this talk](https://drive.google.com/file/d/0B_KkGMZ8ACfaT0RvVE5tX0JpUUE/view?usp=sharing).

* [tbb::parallel_for](parallel_for.md)
* [tbb::parallel_reduce](parallel_reduce.md)
* [Writing a parallel map/reduce](parallel_mapreduce.md)
* [What next?](whatnext.md)

***

# [Previous](mapreduce.md) [Up](README.md) [Next](parallel_for.md)


 
