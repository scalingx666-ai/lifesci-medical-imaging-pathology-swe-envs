# Issue

**Title:** Fix VMAT SCP MU scaling and clinical criteria logic

## Description

### Summary

This PR includes a small set of fixes:

1. Fix MU scaling in the VMAT SCP intermediate optimization to match Eclipse MU.
2. Fix the `clinical_criteria` logic when checking and modifying criteria.

---

### Changes

#### 1. VMAT SCP MU scaling fix

In `portpy/photon/vmat_scp/vmat_scp_optimization.py`:

Adjust the lower-bound constraint on the interior beamlet intensities from:

```python
constraints += [int_v >= self.vmat_params['mu_min']]
```

to 

```python
constraints += [int_v * 100 >= self.vmat_params['mu_min']]
```

This aligns MU handling within the SCP intermediate optimization with Eclipse’s MU scaling.

#### 2. Clinical criteria handling

Both `modify_criterion()` and `check_criterion_exists()` contained the same logical error:
they compared a constraint key (string) to the entire constraint dictionary, which always evaluated to false.

The updated logic now:
1. Properly matches criteria by type and parameters,
2. Iterates through the relevant constraint keys,
3. Updates only existing keys in the stored constraint dictionary,
4. Raises a clear warning if no matching criterion is found.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fef433df8a51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.