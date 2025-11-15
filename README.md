# OpenMP Programming Assignment - Sheet #02

## Task Decomposition with OpenMP

This repository contains implementations of 6 parallel programming tasks using OpenMP, demonstrating various task decomposition patterns and parallel programming techniques.

---

## 📋 Assignment Overview

### Tasks Implemented:

1. **Parallel Logical Evaluation** - Static task decomposition with sections
2. **Parallel Sorting (Merge Sort)** - Recursive task split
3. **Parallel File Compressor** - Task pipeline with dependencies
4. **Parallel Sudoku Solver** - Recursive task decomposition
5. **Parallel Game Tree Search** - Exploratory decomposition (Minimax)
6. **Parallel N-Queens Solver** - Recursive task exploration

---

## 📁 Project Structure

```
assignment-two/
├── Task1-Logical-Evaluation/
│   ├── logical_evaluation.c           # Interactive version
│   └── logical_evaluation_test.c      # Automated test suite
│
├── Task2-Parallel-Sorting/
│   ├── parallel_merge_sort.c          # Main implementation
│   ├── parallel_merge_sort_test.c     # Test suite
│   ├── demo_parallel_tasks.c          # Visual demo
│   ├── IMPLEMENTATION_SUMMARY.md      # Detailed documentation
│   ├── QUICK_START.md                 # Quick start guide
│   └── TASK2_COMPLETED.md             # Completion notes
│
├── Task3-File-Compressor/
│   ├── parallel_file_compressor.c     # Main implementation
│   ├── parallel_file_compressor_test.c # Test suite
│   ├── PARALLEL_FILE_COMPRESSOR_README.md
│   ├── TASK3_PARALLEL_COMPRESSOR_COMPLETED.md
│   └── [demo/test files]              # Test data files
│
├── Task4-Sudoku-Solver/
│   ├── sudoku_solver.c                # Main implementation
│   ├── sudoku_solver_test.c           # Test suite
│   ├── SUDOKU_SOLVER_README.md        # Documentation
│   ├── SUDOKU_IMPLEMENTATION_SUMMARY.txt
│   └── TASK4_SUDOKU_COMPLETED.md
│
├── Task5-Game-Tree-Search/
│   ├── game_tree_search.c             # Minimax AI implementation
│   ├── game_tree_search_test.c        # Test suite
│   ├── demo_game_tree.c               # Demo version
│   └── GAME_TREE_SEARCH_EXPLANATION.md
│
├── Task6-N-Queens-Solver/
│   ├── nqueens_solver.c               # Main implementation
│   └── nqueens_solver_test.c          # Test suite
│
├── Makefile                            # Build configuration
├── README.md                           # This file
└── Sheet #02.pdf                       # Assignment specification
```

---

## 🚀 Quick Start

### Compilation

**Compile all tasks:**

```bash
make all
```

**Compile individual tasks:**

```bash
# Task 1
gcc -fopenmp -o Task1-Logical-Evaluation/logical_evaluation.exe Task1-Logical-Evaluation/logical_evaluation.c

# Task 2
gcc -fopenmp -o Task2-Parallel-Sorting/parallel_merge_sort.exe Task2-Parallel-Sorting/parallel_merge_sort.c

# Task 3
gcc -fopenmp -o Task3-File-Compressor/parallel_file_compressor.exe Task3-File-Compressor/parallel_file_compressor.c

# Task 4
gcc -fopenmp -o Task4-Sudoku-Solver/sudoku_solver.exe Task4-Sudoku-Solver/sudoku_solver.c

# Task 5
gcc -fopenmp -o Task5-Game-Tree-Search/game_tree_search.exe Task5-Game-Tree-Search/game_tree_search.c

# Task 6
gcc -fopenmp -o Task6-N-Queens-Solver/nqueens_solver.exe Task6-N-Queens-Solver/nqueens_solver.c
```

### Running the Programs

```bash
# Task 1 - Logical Evaluation
.\Task1-Logical-Evaluation\logical_evaluation.exe

# Task 2 - Parallel Merge Sort
.\Task2-Parallel-Sorting\parallel_merge_sort.exe 50000

# Task 3 - File Compressor
.\Task3-File-Compressor\parallel_file_compressor.exe input.txt output.txt

# Task 4 - Sudoku Solver
.\Task4-Sudoku-Solver\sudoku_solver.exe

# Task 5 - Game Tree Search (Tic-Tac-Toe AI)
.\Task5-Game-Tree-Search\game_tree_search.exe

# Task 6 - N-Queens Solver
.\Task6-N-Queens-Solver\nqueens_solver.exe
```

---

## 📝 Task Details

### Task 1: Parallel Logical Evaluation

**Description:** Evaluates the logical expression `Y = (A == B) AND (C != D) AND (E OR F)` by assigning each comparison to a separate thread using OpenMP sections.

**Key Features:**

- Uses `#pragma omp parallel sections`
- Each comparison runs on a different thread
- Demonstrates static task decomposition

**OpenMP Concepts:**

- Parallel sections
- Thread identification
- Static workload distribution

---

### Task 2: Parallel Sorting (Task Split)

**Description:** Implements parallel merge sort using OpenMP tasks where each recursive call executes as a separate task.

**Key Features:**

- Recursive task creation with `#pragma omp task`
- Task synchronization with `#pragma omp taskwait`
- Adaptive threshold to avoid task overhead
- Performance comparison with sequential version
- Achieves 2-4x speedup on large arrays

**OpenMP Concepts:**

- Task parallelism
- Task synchronization
- Dynamic load balancing
- Shared and private data clauses

**Documentation:** See `Task2-Parallel-Sorting/IMPLEMENTATION_SUMMARY.md` for detailed explanation.

---

### Task 3: Parallel File Compressor (Task Pipeline)

**Description:** Creates a mini compressor with three pipeline stages (tasks):

- **Task 1:** Read file chunk
- **Task 2:** Compress it (RLE encoding)
- **Task 3:** Write to output

**Key Features:**

- Uses OpenMP task dependencies
- Simulates producer-consumer pipeline
- Run-Length Encoding (RLE) compression
- Chunk-based parallel processing

**OpenMP Concepts:**

- Task dependencies (`depend` clause)
- Pipeline parallelism
- Producer-consumer pattern

**Documentation:** See `Task3-File-Compressor/PARALLEL_FILE_COMPRESSOR_README.md`

---

### Task 4: Parallel Sudoku Solver

**Description:** Uses recursive task decomposition to solve Sudoku boards. Each recursive branch (placing a number) is a new task.

**Key Features:**

- Parallel backtracking with OpenMP tasks
- First solution wins approach
- Atomic flag for solution found
- Efficient pruning when solution discovered

**OpenMP Concepts:**

- Recursive task decomposition
- Atomic operations
- Early termination synchronization

**Documentation:** See `Task4-Sudoku-Solver/SUDOKU_SOLVER_README.md`

---

### Task 5: Parallel Game Tree Search (Exploratory Decomposition)

**Description:** Simulates a two-player minimax search for Tic-Tac-Toe. Each possible move spawns a new task exploring future game states.

**Key Features:**

- Minimax algorithm with alpha-beta pruning
- Task-based parallel exploration
- Dynamic pruning of search space
- Optimal AI that never loses
- Comprehensive statistics (nodes explored, branches pruned)

**OpenMP Concepts:**

- Exploratory decomposition
- Dynamic task spawning
- Load balancing
- Critical sections for shared state

**Documentation:** See `Task5-Game-Tree-Search/GAME_TREE_SEARCH_EXPLANATION.md`

---

### Task 6: Parallel N-Queens Solver

**Description:** Uses OpenMP tasks to explore possible placements of N queens on an NxN chessboard recursively.

**Key Features:**

- Parallel backtracking algorithm
- Each recursive call creates tasks for potential placements
- Counts all valid solutions
- Optional solution visualization
- Performance comparison with sequential version

**OpenMP Concepts:**

- Recursive task creation
- Critical sections for solution counting
- Adaptive task depth threshold

**Known Solutions:**
| N | Solutions |
|----|-----------|
| 4 | 2 |
| 5 | 10 |
| 6 | 4 |
| 7 | 40 |
| 8 | 92 |
| 10 | 724 |

---

## 🔧 Requirements

- **Compiler:** GCC with OpenMP support
- **OS:** Windows (with MinGW/MSYS2), Linux, or macOS
- **OpenMP Version:** 3.0 or higher (for task support)

### Installing GCC on Windows

**Option 1: MinGW-w64**

```bash
# Download from: https://www.mingw-w64.org/
```

**Option 2: MSYS2**

```bash
pacman -S mingw-w64-x86_64-gcc
```

---

## 🎯 Key OpenMP Features Demonstrated

### 1. Parallel Sections (Task 1)

```c
#pragma omp parallel sections num_threads(3)
{
    #pragma omp section
    { /* Thread 1 work */ }

    #pragma omp section
    { /* Thread 2 work */ }

    #pragma omp section
    { /* Thread 3 work */ }
}
```

### 2. Task Parallelism (Tasks 2-6)

```c
#pragma omp parallel
{
    #pragma omp single
    {
        #pragma omp task
        { /* Task work */ }

        #pragma omp taskwait  // Wait for completion
    }
}
```

### 3. Task Dependencies (Task 3)

```c
#pragma omp task depend(out: data)
{ /* Producer */ }

#pragma omp task depend(in: data)
{ /* Consumer */ }
```

### 4. Atomic Operations (Task 4)

```c
#pragma omp atomic write
solution_found = 1;
```

---

## 📊 Performance Results

### Task 2: Merge Sort

- **Array Size:** 100,000 elements
- **Speedup:** ~4.4x (on 8-core system)
- **Parallel Time:** 0.005 seconds
- **Sequential Time:** 0.022 seconds

### Task 5: Game Tree Search

- **Nodes Explored:** ~550,000
- **Branches Pruned:** ~89,000
- **Time:** 0.125 seconds (with 4 threads)

### Task 6: N-Queens (N=10)

- **Solutions Found:** 724
- **Speedup:** 2-3x with parallel version

---

## 🧪 Testing

Each task includes a test suite:

```bash
# Run all tests
.\Task1-Logical-Evaluation\logical_evaluation_test.exe
.\Task2-Parallel-Sorting\parallel_merge_sort_test.exe
.\Task3-File-Compressor\parallel_file_compressor_test.exe
.\Task4-Sudoku-Solver\sudoku_solver_test.exe
.\Task5-Game-Tree-Search\game_tree_search_test.exe
.\Task6-N-Queens-Solver\nqueens_solver_test.exe
```

---

## 🎓 Learning Objectives

This assignment demonstrates:

✅ **Static vs Dynamic Parallelism**

- Sections (static) vs Tasks (dynamic)

✅ **Task Decomposition Patterns**

- Recursive decomposition
- Pipeline parallelism
- Exploratory decomposition

✅ **Synchronization Techniques**

- Task dependencies
- Taskwait
- Atomic operations
- Critical sections

✅ **Performance Optimization**

- Adaptive thresholds
- Load balancing
- Minimizing overhead

✅ **Real-World Algorithms**

- Sorting (merge sort)
- Search (minimax, backtracking)
- Compression (RLE)

---

## 🐛 Troubleshooting

**Problem: "gcc is not recognized"**

- Install MinGW or MSYS2 with GCC

**Problem: "undefined reference to omp\_\*"**

- Ensure `-fopenmp` flag is used in compilation

**Problem: No speedup observed**

- Use larger problem sizes
- Check available CPU cores
- Verify OpenMP is enabled

---

## 📚 Additional Resources

- [OpenMP Official Documentation](https://www.openmp.org/)
- [Task Parallelism Tutorial](https://www.openmp.org/spec-html/5.0/openmpsu60.html)
- Each task folder contains detailed documentation

---

## 👤 Author

**Course:** High Performance Computing (HPC)  
**Assignment:** Sheet #02 - Task Decomposition  
**Semester:** Term 7 (Fall 2025)

---

## 📄 License

This project is for educational purposes as part of an HPC course assignment.

---

**Note:** For detailed implementation explanations, performance analysis, and usage examples, please refer to the README files within each task folder.
#   o p e n m p - t a s k - p a t t e r n s  
 