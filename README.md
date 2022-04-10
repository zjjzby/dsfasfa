## Cache Simulation

[10 points] Consider the following C code:

```
int load(int *array, int i) {
    // read int (4 bytes) at given index
    return array[i];
}

void access_pattern(int *array, int size) {
    // i = 0, 3, 6, ...
    for (int i = 0; i < size-3; i += 3) {
        // read integers at i, i+2, i+3
        load(array, i);
        load(array, i+2);
        load(array, i+3);
    }
}
```

Assuming:
- a direct-mapped cache (K=1 ways)
- N=2 blocks in the cache (also, S=N since K=1)
- B=8 bytes stored in each block
- a very large `array` starting at address 0x0

Consider the first 2 iterations of the loop which will perform 6 memory accesses.
Indicate the sequence of hits and misses that will occur in each iteration.
(e.g., `Iteration i=0: H H H`)

To receive partial credit, give a *brief* explanation for each iteration.
(Each answer is worth 2 points, wrong answers are -2.)

```
Iteration i=0: M H H
Iteration i=3: H M H
```

```
Explanation: Because we have 2 blocks and each block has 8 bytes, we have 16 bytes in total. An int takes 4 bytes, so we can store 4 ints in the cache. We only have 1 line of cache and this is only an array, we can go to the next element by spatial locality until the cache misses and evicts.  
```
