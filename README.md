# Branch Target Buffer (BTB) Replacement policy Analysis

This project implements and evaluates three different replacement algorithms for the Branch Target Buffer (BTB) in a processor pipeline: **Least Recently Used (LRU)**, **Random**, and **First-In-First-Out (FIFO)**. The goal is to analyze their effectiveness in handling branch targets under different workloads and branch predictor configurations.

---

## Replacement Algorithms

### 1. LRU (Least Recently Used)
- Replaces the BTB entry that has not been accessed for the longest time.
- Exploits **temporal locality** by retaining recently used branch targets that are statistically more likely to be referenced again.
- Maintains a priority order of usage to efficiently determine the least recently used entry.

### 2. Random
- Selects a BTB entry for replacement **uniformly at random**.
- Offers a simple implementation with minimal hardware overhead.
- Does **not** consider access patterns or temporal behavior.

### 3. FIFO (First-In-First-Out)
- Replaces the **oldest BTB entry** based on insertion time.
- Treats the buffer as a **circular queue**, evicting entries in the order they were added.
- Ignores usage frequency, focusing purely on arrival order.

---

## Benchmark Evaluation

The replacement algorithms were evaluated using **four industry-standard benchmarks**:

1. **GCC** – Compiler workload  
2. **Anagram** – String manipulation  
3. **Go** – Game-playing algorithm  
4. **Compress** – Data compression  

To ensure a comprehensive analysis, **five different branch predictor configurations** were tested, providing insight into how each replacement algorithm interacts with various prediction strategies.

---

## Key Findings

- **LRU consistently outperforms both Random and FIFO** across all tested benchmarks and branch predictors.
- Its superior performance is attributed to its ability to exploit **temporal locality** in branch target patterns.
- Random and FIFO, while simpler to implement, fail to capture usage patterns effectively, resulting in higher miss rates in the BTB.

---

## Conclusion

For architectures relying on BTB for branch prediction, **LRU is the optimal replacement policy**, balancing performance with efficient retention of relevant branch targets. Random and FIFO can be considered for **low-complexity designs**, but they generally underperform compared to LRU.

---

## License

This project is licensed under the MIT License.  
