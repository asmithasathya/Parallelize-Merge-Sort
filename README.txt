CONTRIBUTIONS

I worked on this project by myself.

REPORT

Test run with threshold 2097152
real	0m0.384s
user	0m0.374s
sys	0m0.007s

Test run with threshold 1048576
real	0m0.230s
user	0m0.387s
sys	0m0.022s

Test run with threshold 524288
real	0m0.156s
user	0m0.422s
sys	0m0.024s

Test run with threshold 262144
real	0m0.143s
user	0m0.544s
sys	0m0.062s

Test run with threshold 131072
real	0m0.145s
user	0m0.550s
sys	0m0.063s

Test run with threshold 65536
real	0m0.147s
user	0m0.564s
sys	0m0.083s

Test run with threshold 32768
real	0m0.150s
user	0m0.567s
sys	0m0.122s

Test run with threshold 16384
real	0m0.160s
user	0m0.603s
sys	0m0.155s

As shown by the results, as the threshold decreases, the real time generally decreases as well, which is what was expected. However, the time increases again at the last two thresholds of 32768 and 16384 showing that a possible point of diminishing returns has been hit. A possible explanation for these results is related to CPU cores. As child processes are created with fork, they can be scheduled by the OS kernel in parallel on different CPU crores. This explains the decreasing times since lower thresholds allow for increase parallelization which results in a decreased time. However, if the threshold is too low, the system hits a point where running more processes concurrently is more difficult, which is where the parallelization doesn't work as efficiently and the time increases again. This system has 4 CPU cores, meaning there can be at most 4 processes running in parallel. Once the threshold reaches around 32768 and below, it is not longer efficient to be running that many processes on the 4 CPU cores, leading to the increase in time.
