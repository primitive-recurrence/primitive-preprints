# Primitive Research preprints

These working manuscripts examine how much a replay system must retain for a declared query and how wavelength selection and search affect thin-film thickness estimates. The PDFs preserve the version labels and credits printed in the original manuscripts.

| Manuscript | Credit and version | Results |
| --- | --- | --- |
| [What must an exact replay remember?](papers/Ohio_Exact_Replay.pdf) | Primitive AI · Preprint v1.1 · 18 November 2026 | A proof for the specified 81-state ternary machine gives 1, 8 or 24 distinguishable endpoint actions for a single active stream of known length at least four, depending on the span of queried vectors. A finite enumeration checks all 512 observation sets. The reported CPU kernel ran 35.57× faster with the group accumulator for 1,000 groups and one snapshot. Direct table replay was faster with 100 snapshots. A five-event example exhibits identical endpoints after policies accepted different events. |
| [Resolving fringe-order errors in thin-film reflectometry](papers/Primitive_Optical_Fringe_Preprint_2026-11-17.pdf) | Joshua Lee Pritchard · Preprint manuscript · 17 November 2026 | The 23-channel simulation recovered 593/600 thicknesses within 1 nm with selected channels and 590/600 with uniform channels. The paired gain was +0.5 percentage points (95% interval −0.5 to +1.5). Retrospective subsampling recovered 33/36 traces with selected channels and 29/36 with uniform channels within 20 nm of vendor references. The traces came from two specimens. In simulation, adjacent-fringe probes increased Fourier-initialized recovery from 124/600 to 294/600. An exploratory denser initializer recovered 572/600 without the probes. A +0.1% index perturbation reduced full-spectrum recovery from 120/120 to 19/120 on the paired subset. Physical instrument acquisition and broader specimen performance remain open. |

See the [reproduction instructions](REPRODUCE.md) and [SHA-256 checksums](SHA256SUMS).

Copyright remains with the respective rights holders. Reuse of the manuscripts is limited to rights available under applicable law and [GitHub's Terms of Service](https://docs.github.com/en/site-policy/github-terms/github-terms-of-service#5-license-grant-to-other-users). The linked datasets retain their own terms.
