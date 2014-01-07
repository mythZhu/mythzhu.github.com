---
layout: post
title: "Peterson's algorithm"
date: 2014-01-07 09:49
comments: true
categories: 
---

------

Peterson's algorithm is a concurrent programming algorithm for mutual exclusion
that allows two processes to share a single-use resource without conflict.
<!--more-->

------

## The algorithm ##

The following C code shows how Petersion's algorithm works. It uses the technique
*busy-waiting* or *spinning*.

```
#define FALSE 0
#define TRUE  1
#define N     2

int turn;
int interested[N];

void enter_region(int process) {
    int other;

    other = 1 - process;
    interested[process] = TRUE;
    turn = process;
    while (turn == process && interested[other] == TRUE);
}

void leave_region(int process) {
    interested[process] = FALSE;
}
```

------

## The proof ##

The algorithm does satisfy the three essential criteria to solve the critical section
problem, provided that changes to the turn, interested[0], and interested[1] variables
propagate immediately and atomically. The three criteria are mutual exclusion, progress,
and bounded waiting.

### Mutual exclusion ###

P0 and P1 can never be in the critical section at the same time: If P0 is in its critical
section, then interested[0] is true. In addition, either interested[1] is false (meaning
P1 has left its critical section), or turn is 0 (meaning P1 is just now trying to enter
the critical section, but graciously waiting), or P1 is going to set its turn (trying to
enter its critical section, after setting interested[1] to true but before setting turn to
0 and busy waiting). So if both processes are in their critical sections then we conclude
that the state must satisfy interested[0] and interested[1] and turn = 0 and turn = 1. No
state can satisfy both turn = 0 and turn = 1, so there can be no state where both processes
are in their critical sections.

### Progress ###

Progress is defined as the following: if no process is executing in its critical section
and some processes wish to enter their critical sections, then only those processes that
are not executing in their remainder sections can participate in making the decision as
to which process will enter its critical section next. This selection cannot be postponed
indefinitely. A process cannot immediately re-enter the critical section if the other process
has set its interested to say that it would like to enter its critical section.


### Bounded waiting ###

Bounded waiting means that "there exists a bound or limit on the number of times that other
processes are allowed to enter their critical sections after a process has made a request to
enter its critical section and before that request is granted". In Peterson's Algorithm, a
process will not wait longer than one turn for entrance to the critical section: After giving
priority to the other process, this process will run to completion and set its interested to 0,
thereby allowing the other process to enter the critical section.

