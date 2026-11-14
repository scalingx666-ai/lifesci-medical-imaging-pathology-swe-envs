# Issue

**Title:** Parse undefined length OB/OW elements

## Description

This addresses #349.

OB and OW fields with undefined length now parse their contents as a sequence, concatenating all the bytes in the items within.

`readBytes` and `readString` return an error if the VL is `tag.VLUndefinedLength`, as parsing these tags shouldn't fall to these, and we avoid future accidental 4GB allocations.

Trying to parse the (contrived) file from the issue now returns:
```
readElement: error when reading value for element (0049,1001): unable to read field of undefined length
```

Parsing a real DICOM file with an OB field of undefined length parses without error.

I made this a constant (`ErrorExpectedDefinedLength`) so it could be used in a test, but I think it may be worth returning a custom error so we include the VR as well, e.g. 

```
readElement: error when reading value for element (0049,1001): undefined length element of type OB cannot be read
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c45b44e60ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.