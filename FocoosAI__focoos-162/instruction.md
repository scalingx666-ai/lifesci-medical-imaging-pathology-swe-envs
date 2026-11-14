# Issue

**Title:** Add mosaic and copy-paste augmentations

## Description

- Introduced MosaicAugmentation class to combine images in a grid layout.
- Added CopyPasteAugmentation class to enhance images by pasting objects from other images.
- Updated DictDataset methods to support new augmentation functionalities.
- Refactored existing methods for clarity and consistency, including deprecating the store_coco_roboflow_format method in favor of save.
- Improved annotation handling and bounding box adjustments in the dataset processing.

<!-- CURSOR_SUMMARY -->
---

> [!NOTE]
> Introduce mosaic and copy-paste augmentations with a CLI to generate/save augmented datasets, and update DictDataset to use a new save method with COCO export fixes.
>
> - **Augmentations (scripts/dataset_augmentations.py)**:
>   - Add `MosaicAugmentation` and `CopyPasteAugmentation` with bbox remapping and optional blending.
>   - Provide CLI to generate augmented images (weights, sizes, counts), write images to disk, build a new dataset, and save in Roboflow COCO format; optional val copy.
> - **Dataset (`focoos/data/datasets/dict_dataset.py`)**:
>   - Add `save(output_dir)` for Roboflow COCO export; deprecate `store_coco_roboflow_format` in favor of `save`.
>   - COCO export tweaks: `category_id` offset by +1; default `iscrowd` to 0.
>   - Minor refactor: typing import and small formatting in `from_segmentation`.
>
> <sup>Written by [Cursor Bugbot](https://cursor.com/dashboard?tab=bugbot) for commit d85453a0e9a1aa07491e66beeb12f12e24617fa5. This will update automatically on new commits. Configure [here](https://cursor.com/dashboard?tab=bugbot).</sup>
<!-- /CURSOR_SUMMARY -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec63256e269a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.