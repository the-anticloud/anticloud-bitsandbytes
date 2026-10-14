# How to Update — BITSANDBYTES

**Project:** `BITSANDBYTES`
**Category:** CHIP_QUANTIZATION
**Domain:** chip quantization and model compression
**Date:** 2026-10-07

---

## Update Procedure

### Checking for Updates
```bash
BITSANDBYTES --version
BITSANDBYTES check-update
```

### Applying Updates
```bash
pip install --upgrade BITSANDBYTES
```

### Rolling Back
```bash
pip install BITSANDBYTES==<previous-version>
```

### Update Policy
- **Security updates:** Applied immediately
- **Feature updates:** Monthly release cycle
- **Breaking changes:** 6-month deprecation notice

## Verification

All 16 checks PASS. Evidence: `ISOLATED_LAB_RESULTS/03_Result_Register.md`.
