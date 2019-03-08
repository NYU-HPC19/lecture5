# Last Class

+ Flynn's taxonomy (SISD, SIMD, MIMD, MISD)
+ Shared memory vs Distributed memory (and Hybrid model)
+ Amdahl's law (speedup < 1/(s + (1-s)/p))
+ Load balancing (static vs dynamic)
+ Scalability (strong and weak)
+ Reasons for poor scalability (Amdahl's law, load imbalance)
+ Shared memory model (OpenMP, POSIX, PGAS)
  - process vs thread
  - Symmetric multiprocessing vs CC-NUMA
  - Race conditions: multiple threads accessing the same memory location when at least one thread is writing
+ OpenMP
  - fork-join model
  - pragmas (#pragma omp <parallel, for, sections, section, master, single, critical, berrier>)
  - additional options: schedule(static/dynamic/guided/runtime), reduction(+:sum), nowait
  - functions (#include <omp.h>, omp_get_max_threads(), omp_get_num_threads(), omp_get_thread_num(), omp_set_num_threads())
  - environment variables (OMP_NUM_THREADS, )
+ Git: config, clone, add, commit, pull, push


# This Class

+ Advanced OpenMP
  - False sharing (cacheline)
  - CC-NUMA (sockets, cores, NUMA-nodes, first-touch)
  - Nested parallelism, parallel for collapse(2)
  - Memory models (weak sequential consistency)
  - Synchronization: atomic, flush, locks (omp_lock_t)
  - Thread affinity: OMP_PLACES=(cores/socket), OMP_PROC_BIND=(close/spread), OMP_DISPLAY_ENV=true)
+ Git: merging
+ Makefile: variables, rules, targets, dependency list, make -j

## Git


### Basic commands

```
git init                         # initialize a directory as a new repository
git add <file-name>              # add new file or changes to an existing file to be commited (also called staging)
git commit -m '<commit-message>' # commit staged changes
git pull                         # pull changes from the remote repository
git push                         # push changes to a remote repository

git clone <repo-path>            # clone a repository

git status                       # show current status of the repository
git diff                         # show unstaged changes in the repository
git diff --cached                # show staged changes in the repository
git diff <file-name>             # show changes to a particular file

```


### Mergin (two ways)

#### Stash, pull and commit

```
git add <files>
git stash
git pull
git stash pop
# resolve any merge conflicts
git stash clear
git add <files>
git commit 'merged'
```

#### Commit, pull and commit

```
git add <files>
git commit -m 'message'
git pull
# resolve any merge conflicts
git add <files>
git commit
```


### ```git log```

```
> git log

commit 2b3ba91d4ad98c33aade864c46a705e96f6c2985
Author: Dhairya Malhotra <dmalhotra@ices.utexas.edu>
Date:   Thu Jan 19 15:46:39 2017 -0600

    Add .gitignore

commit 7b81413e6bec668af4b4aa52a8774784c778e2c8
Author: Dhairya Malhotra <dmalhotra@ices.utexas.edu>
Date:   Thu Jan 19 15:41:19 2017 -0600

    Minor changes

commit bb89504a2cb24767ad68b1ae611baa8e2da0865f
Author: Dhairya Malhotra <dmalhotra@ices.utexas.edu>
Date:   Thu Jan 19 15:07:05 2017 -0600

    Initial commit

```

```
alias gg='git log --oneline --abbrev-commit --all --graph --decorate --color'

> gg
*   4481a65 (HEAD, master) merged
|\
| * 7fa895c (origin/master, origin/HEAD) more text
* | 3264c75 some more
|/
* 5ecb7e0 add text
* f6f082b add readme

```

GUI view
```
gitk [options]
```




