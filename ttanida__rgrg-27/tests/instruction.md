# Issue

**Title:** Fix test set evaluation GPU memory leak

## Description

Hi,

As I have been reproducing your results based on your codebase, I have noticed that the test-set evaluation script (`src/full_model/test_set_evaluation.py`) has a GPU memory leak. As it iterates through batches for the language model evaluation, GPU memory use keeps climbing from batch to batch. On my hardware, that led to out-of-memory errors at some later point in evaluation, even with a batch size of 1 whereas that was no problem at training.

I've tracked the source of the leak down, and it seems that re-initiating the `bertscore` evaluation module for each batch (as `get_generated_reports` is called inside the dataset iterator loop, and `evaluate.load("bertscore")` is called in the function) was what caused this behavior. 

By initiating the evaluation module once before the loop, and keeping it on GPU throughout the dataset iteration as done in my suggested modifications, the memory leak was resolved and larger batches could be used with stable GPU memory usage. 

Thank you for the excellent and very well documented work!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb64933e222e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.