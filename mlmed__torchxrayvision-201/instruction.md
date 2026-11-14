# Issue

**Title:** Add VQGAN AE baseline model

## Description

A VQ-GAN (`Esser et al., 2021 <https://arxiv.org/abs/2012.09841>`_) that
    encodes a chest X-ray into a grid of discrete latent codes and decodes it
    back. It was built for generating counterfactual explanations with Latent
    Shift (`Cohen et al., 2021 <https://arxiv.org/abs/2102.09475>`_): the
    gradient of a classifier's output is followed in the latent space, and
    decoding gives an image the classifier scores as less positive. It was
    used for the 6th place MIDRC XAI Challenge winner.

The native resolution of the model is 768x768. Inputs are expected in the
    TorchXRayVision pixel range of [-1024, 1024] and are resized by bilinear
    interpolation automatically. The single channel is repeated to three for the
    VQ-GAN, and ``decode`` returns one channel clipped to [-1024, 1024] at
    768x768, regardless of the input size.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24cc049ed16e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.