#numerics

**Optimize in a fixed order — measure, algorithm, memory access, per-operation cost, parallelism — because each stage bounds what the later ones can achieve: no parallelism rescues $O(n^2)$, no compiler rescues a cache-hostile access pattern.** Concepts are language-independent; tools differ by ecosystem.

# Reference

## 1. Measure

Profile before changing anything, at realistic sizes (hotspots move with scale). **Amdahl**: a section taking fraction $p$ of runtime caps the total speedup at

$$S_{\max} = \frac{1}{1 - p} \quad\text{(eliminated)}, \qquad S(N) = \frac{1}{(1-p) + p/N} \quad\text{($N$-way parallel)}.$$

Classify the bottleneck first — compute-bound, **memory-bound** (CPU waits for data; the common case in numerics), or I/O-bound — since the remedies are disjoint.

## 2. Algorithm

The only stage that compounds with all others. Checklist: $O(n^2) \to O(n\log n)$ substitutions (FFT convolution/correlation — [[Convolution]], [[FFT in Practice]]); exploitable structure ([[Sparse Matrices|sparsity]], symmetry sectors, low rank via truncated [[Singular Value Decomposition|SVD]], bandedness); recomputation → cache it, factor once and reuse (one factorization, many right-hand sides), or update incrementally (running statistics).

## 3. Memory access

Latency hierarchy register : L1 : L3 : RAM ≈ 1 : 4 : 20 : 200 cycles; hardware fetches 64 B cache lines and prefetches sequential access.

- **Traverse in storage order** — row-major (C/NumPy) vs column-major (Fortran/MATLAB/Julia); wrong-axis iteration of a 2D array = every access a cache miss, ~10× for nothing.
- **Contiguity** — strided/gathered access defeats prefetch; libraries silently copy non-contiguous input.
- **No allocation in hot loops** — preallocate, write in place; in GC languages allocation pressure also triggers pauses.
- **Tiling** — when the working set exceeds last-level cache (~tens of MB), process in cache-sized blocks (what optimized BLAS does internally).

## 4. Per-operation cost

- **Vectorize**, in both senses at once: SIMD (one instruction, 4–16 operands; needs branch-free loops over contiguous data) and array-language operations (compiled kernels replacing interpreted per-element dispatch: 10–100× in Python/MATLAB). Whole-array code is also what SIMD and BLAS digest.
- **Call the optimized kernels** — BLAS/LAPACK/FFTW run within percent of hardware limits and are already multithreaded; the common inefficiency is writing a triple loop where one `gemm` serves.
- **Compile the residue** — recurrences and branchy per-element logic that resist array form: JIT (Numba; Julia natively; JAX with tracing constraints) or a compiled kernel (C/Rust/Cython). Compile the hot 5%, leave the rest legible.
- **Precision**: float32 halves memory traffic and doubles SIMD width — near-2× for memory-bound code, when the [[Floating Point and Numerical Error|error analysis]] allows (accumulate in float64).
- Minor, real: division/transcendentals cost 5–20× a multiply (hoist invariants); branches in hot loops defeat pipelining (mask instead).

## 5. Parallelism

Classify before choosing machinery:

| class | example | tool | caveat |
|---|---|---|---|
| embarrassingly parallel | parameter sweeps, MC shots | process pools, job arrays | independent RNG streams per worker (`SeedSequence`-style spawning, never `seed(id)`); log seeds — [[Monte Carlo Methods]] |
| shared-memory threads | one large coupled computation | threads on shared arrays | races; false sharing (adjacent writes fight over one cache line); interpreter locks (Python GIL → use processes); check BLAS isn't already using all cores — nested parallelism oversubscribes |
| distributed | beyond one node | MPI | communication is now part of the algorithm |
| GPU | large dense arrays, batched small problems | CuPy/JAX/Julia | PCIe transfer dominates unless data stays resident; branchy scalar code does not port |

**Cross-cutting:** keep the slow obviously-correct implementation as an automated test — optimization bugs produce plausible wrong numbers, not crashes; version baseline timings; checkpoint long runs; memory-map datasets larger than RAM.

> [!question]- A simulation runs 40× below the machine's FLOP rate and the profiler shows time spread evenly across the main loop — no hotspot. Diagnosis?
> Uniform slowness is the signature of memory-bound or interpreter-bound execution: every iteration pays the same overhead (wrong-order traversal, non-contiguous access, per-element dispatch, in-loop allocation), and the FLOP estimate assumed compute-bound. Confirm by checking whether runtime tracks data size rather than operation count (or read cache-miss counters); then apply stages 3–4 — fix traversal order, move the loop into an array operation or compiled kernel, hoist allocations.

# Connections

- [[Sparse Matrices]] — structure exploitation at the algorithm stage
- [[Exact Diagonalization and Sparse Methods]] — these principles on Hilbert-space problems
- [[Floating Point and Numerical Error]] — the error analysis behind precision reduction
- [[FFT in Practice]] — the canonical $O(n\log n)$ substitution
- [[Monte Carlo Methods]] — the embarrassingly parallel workload and its RNG discipline

---
Source: Hennessy & Patterson, *Computer Architecture*, Ch. 2; Goedecker & Hoisie, *Performance Optimization of Numerically Intensive Codes*
