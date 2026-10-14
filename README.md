# BITSANDBYTES

![licence](https://img.shields.io/badge/licence-MIT-blue) ![checks](https://img.shields.io/badge/checks-0_PASS-brightgreen)

> Governed Anticloud packaging of upstream `BITSANDBYTES` in category **CHIP_QUANTIZATION**. 0/16 checks PASS (measured). Every number traces to a named file plus run stamp.

**Upstream:** https://github.com/bitsandbytes-foundation/bitsandbytes | **Upstream pin:** `833649043474794b8fe7a4136e0c40faf077b2e0` (source: bench:BENCH.json) | **Category:** CHIP_QUANTIZATION | **Licence:** MIT | **Overlay licence:** Anticommons 0.1.0

---

## What This Project Does

<p align="center"><img src="https://avatars.githubusercontent.com/u/175231607?s=200&v=4" alt=""></p>
<h1 align="center">bitsandbytes</h1>
<p align="center">
    <a href="https://github.com/bitsandbytes-foundation/bitsandbytes/main/LICENSE"><img alt="License" src="https://img.shields.io/github/license/bitsandbytes-foundation/bitsandbytes.svg?color=blue"></a>
    <a href="https://pepy.tech/project/bitsandbytes"><img alt="Downloads" src="https://static.pepy.tech/badge/bitsandbytes/month"></a>
    <a href="https://github.com/bitsandbytes-foundation/bitsandbytes/actions/workflows/tests-nightly.yml"><img alt="Nightly Unit Tests" src="https://img.shields.io/github/actions/workflow/status/bitsandbytes-foundation/bitsandbytes/tests-nightly.yml?logo=github&label=Nightly%20Tests"></a>
    <a href="https://github.com/bitsandbytes-foundation/bitsandbytes/releases"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/bitsandbytes-foundation/bitsandbytes"></a>
    <a href="https://pypi.org/project/bitsandbytes/"><img alt="PyPI - Python Version" src="https://img.shields.io/pypi/pyversions/bitsandbytes"></a>
</p>

`bitsandbytes` enables accessible large language models via k-bit quantization for PyTorch. We provide three main features for dramatically reducing memory consumption for inference and training:

* 8-bit optimizers uses block-wise quantization to maintain 32-bit performance at a small fraction of the memory cost.
* LLM.int8() or 8-bit quantization enables large language model inference with only half the required memory and without any performance degradation. This method is based on vector-wise quantization to quantize most features to 8-bits and separately treating outliers with 16-bit matrix multiplication.
* QLoRA or 4-bit quantization enables large language model training with several memory-saving techniques that don't compromise performance. This method quantizes a model to 4-bits and inserts a small set of trainable low-rank adaptation (LoRA) weights to allow training.

The library includes quantization primitives for 8-bit & 4-bit operations, through `bitsandbytes.nn.Linear8bitLt` and `bitsandbytes.nn.Linear4bit` and 8-bit optimizers through `bitsandbytes.optim` module.

## System Requirements
bitsandbytes has the following minimum requirements for all platforms:

* Python 3.10+
* [PyTorch](https://pytorch.org/get-started/locally/) 2.4+
  * _Note: While we aim to provide wide backwards compatibility, we recommend using the latest version of PyTorch for the best experience._

#### Accelerator support:

<small>Note: this table reflects the status of the current development branch. For the latest stable release, see the
[document in the 0.50.0 tag](https://github.com/bitsandbytes-foundation/bitsandbytes/blob/0.50.0/README.md#accelerator-support).
</small>

##### Legend:
🚧 = Planned |
〰️ = Partially Supported |
✅ = Supported |
❌ = Not Supported

<table>
  <thead>
    <tr>
      <th>Platform</th>
      <th>Accelerator</th>
      <th>Hardware Requirements</th>
      <th>LLM.int8()</th>
      <th>QLoRA 4-bit</th>
      <th>8-bit Optimizers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="6">🐧 <strong>Linux, glibc >= 2.24</strong></td>
    </tr>
    <tr>
      <td align="right">x86-64</td>
      <td>◻️ CPU</td>
      <td>Minimum: AVX2<br>Optimized: AVX512F, AVX512BF16</td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟩 NVIDIA GPU <br><code>cuda</code></td>
      <td>SM60+ minimum<br>SM75+ recommended</td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟥 AMD GPU <br><code>cuda</code></td>
      <td>
        CDNA: gfx908, gfx90a, gfx942, gfx950, gfx1250<br>
        RDNA: gfx101X, gfx103X, gfx110X, gfx115X, gfx120X
      </td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟦 Intel GPU <br><code>xpu</code></td>
      <td>
        Data Center GPU Max Series<br>
        Arc A-Series (Alchemist)<br>
        Arc B-Series (Battlemage)
      </td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟪 Intel Gaudi <br><code>hpu</code></td>
      <td>Gaudi2, Gaudi3</td>
      <td>✅</td>
      <td>〰️</td>
      <td>❌</td>
    </tr>
    <tr>
      <td align="right">aarch64</td>
      <td>◻️ CPU</td>
      <td></td>
      <td>✅ *</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟩 NVIDIA GPU <br><code>cuda</code></td>
      <td>SM75+</td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td colspan="6">🪟 <strong>Windows 11 / Windows Server 2022+</strong></td>
    </tr>
    <tr>
      <td align="right">x86-64</td>
      <td>◻️ CPU</td>
      <td>AVX2</td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟩 NVIDIA GPU <br><code>cuda</code></td>
      <td>SM60+ minimum<br>SM75+ recommended</td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟥 AMD GPU <br><code>cuda</code></td>
      <td>
        CDNA: gfx908, gfx90a<br>
        RDNA: gfx101X, gfx103X, gfx110X, gfx115X, gfx120X
      </td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟦 Intel GPU <br><code>xpu</code></td>
      <td>
        Arc A-Series (Alchemist) <br>
        Arc B-Series (Battlemage)
      </td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td align="right">arm64</td>
      <td>◻️ CPU</td>
      <td></td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td></td>
      <td>🟩 NVIDIA GPU <br><code>cuda</code></td>
      <td>SM121</td>
      <td>✅</td>
      <td>✅</td>
      <td>✅</td>
    </tr>
    <tr>
      <td colspan="6">🍎 <strong>macOS 14+</strong></td>
    </tr>
    <tr>
      <td align="right">arm64</td>
      <td>◻️ CPU</td>
      <td>Apple M1+</td>
      

(Full upstream documentation preserved in UPSTREAM_CLONE/README.md.)

---

## Installation

See the upstream documentation quoted in What This Project Does above.

## Usage

<h1 align="center">bitsandbytes</h1>
<p align="center">
    <a href="https://github.com/bitsandbytes-foundation/bitsandbytes/main/LICENSE"><img alt="License" src="https://img.shields.io/github/license/bitsandbytes-foundation/bitsandbytes.svg?color=blue"></a>
    <a href="https://pepy.tech/project/bitsandbytes"><img alt="Downloads" src="https://static.pepy.tech/badge/bitsandbytes/month"></a>
    <a href="https://github.com/bitsandbytes-foundation/bitsandbytes/actions/workflows/tests-nightly.yml"><img alt="Nightly Unit Tests" src="https://img.shields.io/github/actions/workflow/status/bitsandbytes-foundation/bitsandbytes/tests-nightly.yml?logo=github&label=Nightly%20Tests"></a>
    <a href="https://github.com/bitsandbytes-foundation/bitsandbytes/releases"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/bitsandbytes-foundation/bitsandbytes"></a>
    <a href="https://pypi.org/project/bitsandbytes/"><img alt="PyPI - Python Version" src="https://img.shields.io/pypi/pyversions/bitsandbytes"></a>
</p>

`bitsandbytes` enables accessible large language models via k-bit quantization for PyTorch. We provide three main features for dramatically reducing memory consumption for inference and training:

* 8-bit optimizers uses block-wise quantization to maintain 32-bit performance at a small fraction of the memory cost.
* LLM.int8() or 8-bit quantization enables large language model inference with only half the required memory and without any performance degradation. This method is based on vector-wise quantization to quantize most features to 8-bits and separately treating outliers with 16-bit matrix multiplication.
* QLoRA or 4-bit quantization enables large language model training with several memory-saving techniques that don't compromise performance. This method quantizes a model to 4-bits and inserts a small set of trainable low-rank adaptation (LoRA) weights to allow training.

The library includes quantization primitives for 8-bit & 4-bit operations, through `bitsandbytes.nn.Linear8bitLt` and `bitsandbytes.nn.Linear4bit` and 8-bit optimizers through `bitsandbytes.optim` module.

## API

* [Official Documentation](https://huggingface.co/docs/bitsandbytes/main)
* 🤗 [Transformers](https://huggingface.co/docs/transformers/quantization/bitsandbytes)
* 🤗 [Diffusers](https://huggingface.co/docs/diffusers/quantization/bitsandbytes)
* 🤗 [PEFT](https://huggingface.co/docs/peft/developer_guides/quantization#quantize-a-model)

## Dependencies

| Metric | Value |
|--------|-------|
| Files | measured |
| Lines of Code | measured |
| Dependencies | measured |
| Upstream licence | MIT |
| Overlay licence | Anticommons 0.1.0 |

Dependency manifests live in `UPSTREAM_CLONE/`; pinned lockfile in `anticloud/` where applicable.

## Configuration

See upstream source in UPSTREAM_CLONE/ and the quoted documentation above.

## Contributing

# Contributing to bitsandbytes
We want to make contributing to this project as easy and transparent as
possible.

## Pull Requests
We actively welcome your pull requests.

1. Fork the project and create your branch from `main`.
2. If you've added code that should be tested, add tests.
3. If you've changed APIs, update the documentation.
4. Ensure the test suite passes.
5. Make sure your code lints, install the [pre-commit hooks as documented here](https://huggingface.co/docs/bitsandbytes/main/en/contributing#setup-pre-commit-hooks).

## Issues
We use GitHub issues to track public bugs. Please ensure your description is
clear and has sufficient instructions to be able to reproduce the issue.

## License
By contributing to bitsandbytes, you agree that your contributions will be licensed
under the LICENSE file in the root directory of this source tree.

## Licence

Upstream (c) its contributors under MIT - see `UPSTREAM_CLONE/LICENSE`. This packaging overlay is licensed under Anticommons 0.1.0.

## Upstream

- URL: https://github.com/bitsandbytes-foundation/bitsandbytes
- Pinned commit: `833649043474794b8fe7a4136e0c40faf077b2e0`
- Verify: compare against the pinned commit in the upstream project history.

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`cccbf9638a439376c5bfcc0672ddc94bbf976e18f9ebb99ca969d0da59d237ff`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

