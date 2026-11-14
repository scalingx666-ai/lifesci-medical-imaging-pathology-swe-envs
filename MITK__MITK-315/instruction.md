# Issue

**Title:** fix: crash on removing a DataNode from the DataManager due to missing…

## Description

fix: crash on removing a DataNode from the DataManager due to missing endRemoveRows in `QmitkDataStorageSimpleTreeModel::NodeRemoved` and `nullptr` in `QmitkDataStorageSimpleTreeModel::flags` causing the `mitk::NodePredicateAnd::CheckNode` to `throw std::invalid_argument("NodePredicateAnd: invalid node");`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `499a58d960b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.