# Badge status
Main Branch
![example workflow](https://github.com/uofu-emb/2024-lab5-samuel_bosch-varun/actions/workflows/main.yml/badge.svg)

Threads Branch
![example workflow](https://github.com/uofu-emb/2024-lab5-samuel_bosch-varun/actions/workflows/main.yml/badge.svg?branch=dev)

# Lab Activities:

## Activity 1
Below are the output responses for DELAY_MS = 1000 for task_delay.c, timer.c, and sleep.c

Formula for drift = |3600s - (3600[s] * 1/(2*DELAY_MS[s])) * T_avg [s]|

task_delay.c (Drift = |3600 - (3600 * 0.5) * (1.999998)| = 0.0036 s)

timer.c (Drift = |3600 - (3600 * 0.5) * (1.999998)| = 0.0036 s)

sleep.c (Drift = |3600 - (3600 * 0.5) * (1.999998)| = 0.0036 s)


For our busy-wait loop, we decided to use a for-loop that printed a single character to stdout 1024 times to simulate operations on one KB of data. Below are the modified task_delay.c, timer.c, and sleep.c

task_delay.c (Drift = |3600 - (3600 * 0.5) * (2.019996)| = 35.9928 s)

timer.c (Drift = |3600 - (3600 * 0.5) * (1.999998)| = 0.0036 s)

sleep.c (Drift = |3600 - (3600 * 0.5) * (2.010726)| = 19.3086 s)

Here is the same signal output by the function generator.
(Drift = |3600 - (3600 * 0.5) * (2.000016)| = 0.0288 s)

## Activity 2
The measured delay between the sync signal and the GPIO output was negligible in the first case with no delay added (pictured below are two overlapping signals at this time scale)

When we added a delay with the same busy loop, we found a time delay of delta_t = 5.0512 ms
