# Reproduction

## Verify the manuscript files

Run the checksum check from the repository root.

```sh
sha256sum -c SHA256SUMS
```

On macOS, use `shasum -a 256 -c SHA256SUMS`. This checks the PDF bytes. The scientific checks below use separate data or code.

## Exact replay

The proof and executable check concern the specified ternary transition. To reconstruct the finite enumeration from the PDF, generate all four-control words over {0, 1, 2}. Apply each word to the two basis vectors in the active plane using (x, y) → (−y, x + ky) modulo three. Group words by their ordered pair of basis images. Use one representative per group, then count distinct ordered response tuples for each of the 512 subsets of the nine spatial vectors. The expected numbers of subsets of rank 0, 1 and 2 are 2, 24 and 486, with 1, 8 and 24 endpoint classes respectively. The proof in the manuscript extends the classification to every known length of at least four.

If you have the separate `Ohio_Exact_Replay_Review.zip` research archive, its README gives the complete C++20, Lean 4.24.0 and Python commands. From its root, verify the archive and rerun the deterministic Python checks.

```sh
sha256sum -c SHA256SUMS
python3 checks/observation.py > observation-fresh.json
diff -u checks/certificate.json observation-fresh.json
python3 checks/mirror.py > mirror-fresh.json
diff -u checks/mirror.json mirror-fresh.json
python3 god_pod/bridge.py > gate-fresh.json
diff -u god_pod/results.json gate-fresh.json
```

For the kernel comparison, compile `replay/compare.cpp` from the archive's `replay/` directory with `g++ -O3 -std=c++20 -march=x86-64 compare.cpp -o compare`, run `./compare > fresh.csv`, and compare the checksums with the archived `timing.csv`. Timing ratios depend on the host and workload. The sensor replay uses a pinned processed copy of [UCI Air Quality](https://doi.org/10.24432/C59K5F) (CC BY 4.0) and compares replay implementations on controls derived from that series.

## Thin-film reflectometry

The measured inputs are the [University of Sheffield dataset, version 1](https://doi.org/10.15131/shef.data.23285603.v1) (CC BY 4.0), attributed to N. Sánchez Arriaga, D. Tiwari, W. Hutabarat, A. Leyland and A. Tiwari. The [associated instrument paper](https://doi.org/10.3390/s23115326) reports the vendor reference thicknesses. The silicon optical constants come from the [Aspnes and Studna tabulation in RefractiveIndex.INFO](https://refractiveindex.info/?shelf=main&book=Si&page=Aspnes) (CC0).

If you have the separate `Primitive_Optical_Fringe_Preprint_Replay_2026-11-17.zip` research archive, run these commands from its root with Python 3.12.

```sh
sha256sum -c SHA256SUMS
python3 -m pip install -r requirements.txt
OPENBLAS_NUM_THREADS=1 OMP_NUM_THREADS=1 python3 benchmark.py --output replay
OPENBLAS_NUM_THREADS=1 OMP_NUM_THREADS=1 python3 engineering_controls.py --input replay/cases.csv --output replay/cases_with_controls.csv
python3 analyze.py --input replay/cases_with_controls.csv --output replay --figures replay/figures
python3 verify.py replay/cases_with_controls.csv
```

The simulation and bootstrap seeds are 2026111727 and 2026111777. `PROTOCOL.md` describes the prespecified contrast and exploratory controls. The verifier compares saved case results without elapsed times. The archive's separately built PDF has its own checksum. Use this repository's manifest to identify the preprint PDF.

The separate research archives are required for the packaged benchmark commands. This repository contains the manuscripts and documentation.
