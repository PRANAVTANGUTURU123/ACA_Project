# Branch Target Buffer (BTB) Replacement Policy Analysis

This project implements and evaluates three different replacement algorithms for the Branch Target Buffer (BTB) in a processor pipeline: **Least Recently Used (LRU)**, **Random**, and **First-In-First-Out (FIFO)**. The objective is to analyze their performance under different workloads and branch predictor configurations.

**Note:** All modifications made to the source code files in this project are documented in **Code_changes.pdf** included in the repository.

---

## Replacement Algorithms

### 1. LRU (Least Recently Used)
- Replaces the BTB entry that has not been accessed for the longest duration.
- Leverages **temporal locality**, retaining recently used branch targets that are more likely to be accessed again.
- Maintains usage ordering to efficiently determine which entry to evict.

### 2. Random
- Selects an entry to replace **uniformly at random**.
- Very simple to implement with minimal hardware overhead.
- Does **not** consider temporal or spatial locality.

### 3. FIFO (First-In-First-Out)
- Replaces the **oldest entry** in the BTB based on insertion order.
- Treats the BTB as a **circular queue**, evicting entries chronologically.
- Ignores frequency or recency of access.

---

## Benchmarks Evaluated

The replacement algorithms were tested on four industry-standard benchmark applications:

1. **GCC** – Compiler workload  
2. **Anagram** – String manipulation  
3. **Go** – Game-playing algorithm  
4. **Compress** – Data compression  

Five different branch predictor configurations were used to provide a comprehensive evaluation across varying access patterns.

---

## Key Findings

- **LRU consistently outperforms Random and FIFO** across all benchmarks and predictor configurations.
- Its superior results stem from better exploitation of **temporal locality**.
- **Random** and **FIFO**, while simpler in design, fail to preserve frequently used branch targets effectively, resulting in higher BTB miss rates.

---

## Conclusion

For processor architectures that rely heavily on BTB for branch prediction, **LRU is the most efficient and reliable replacement policy**.  
Random and FIFO may be preferred in **low-complexity or hardware-constrained designs**, but generally deliver lower performance.

---

## License

This project is licensed under the **MIT License**.
