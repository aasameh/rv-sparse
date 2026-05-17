# rv-sparse

In-progress CSR-only sparse linear algebra library with scalar and RISC-V RVV kernels.

## Scope
- Formats: CSR only (no CSC/COO in this PR)
- SpMV: scalar + RVV (accum-style kernel)
- SpMM: scalar + RVV (accum-style kernel)

## Build and run
Requirements:
- GCC for native tests
- RISC-V GNU toolchain (`riscv64-linux-gnu-gcc`) and QEMU (`qemu-riscv64-static`) for RVV targets

Commands:
```sh
make test_native
./test_native

make test_riscv
make run_test

make bench_riscv
make run_bench

make bench_spmm_riscv
make run_bench_spmm
```

## Notes
- "Accum" refers to the RVV kernel style (vector accumulation + single reduction), not accumulation semantics. Outputs overwrite: $y = A x$ and $C = A B$.

## Layout
- include/rv_sparse.h: public API surface
- src/matmul/: CSR utilities, SpMV, SpMM, tests, benchmarks

## Results
See RESULTS.md for benchmark numbers and theoretical speedup notes.
