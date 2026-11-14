# Issue

**Title:** Update color.py

## Description

### Description
<!--- Describe your changes in detail -->
This is just a conversion from lower case "hsv" to upper case "HSV" inside the "adjust_hue" function of the `caer/transforms/color.py`, which appears to be important to the PIL Image class. I did notice that it was somehow automatically corrected but not sure whether it was the python itself or VS Code that did it. 

### Types of changes
<!--- Put an `x` in all the boxes that apply, and remove the non-applicable items -->
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] Breaking change (fix or new feature that would cause existing functionality to change)
- [ ] Docstrings/Documentation updated
- [ ] New Feature to Caer
- [ ] New Examples to [`examples`](https://github.com/jasmcaus/caer/tree/master/examples)
- [ ] New tests added to cover the changes


### Related Issues
<!--- If it fixes an open issue, please link to the issue here. -->


### Checklist:
<!--- Go over all the following points, and put an `x` in all the boxes that apply. -->
<!--- If you're unsure about any of these, don't hesitate to ask. We're here to help! -->
- [x] I have followed the [contribution guidelines](CONTRIBUTING.md) and code style for this project.
- [ ] I have added tests covering my contributions (**important**).
- [ ] I have updated the documentation accordingly.
- [x] This PR is being made to `dev` and not `master` (**important**).
- [ ] I will squash merge this PR into `dev` (optional)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11ff37867c2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.