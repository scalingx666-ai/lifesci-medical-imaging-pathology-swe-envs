# Issue

**Title:** chore(release): Release OHIF 3.13.14 - all security focused

## Description

<!-- Do Not Delete This! pr_template -->
<!-- Please read our Rules of Conduct: https://github.com/OHIF/Viewers/blob/master/CODE_OF_CONDUCT.md -->
<!-- 🕮 Read our guide about our Contributing Guide here https://docs.ohif.org/development/contributing -->
<!-- :hand: Thank you for starting this amazing contribution! -->

<!--
⚠️⚠️ Please make sure the checklist section below is complete before submitting your PR.
To complete the checklist, add an 'x' to each item: [] -> [x]
(PRs that do not have all the checkboxes marked will not be approved)
-->

### Context
The following from master get back ported for release:

1. #6403 
2. #6406
3. stop printing GITHUB_TOKEN in the preinstall script
   
    When GITHUB_TOKEN was set, preinstall.js printed a git config command containing the token, so it showed up in the CircleCI log. It also saved the token in the global git config on every install. Nothing uses SSH GitHub URLs any more, so the block is dead code. Remove it, as master did in a279347a0b.

    Also delete platform/app/preinstall.js. Nothing references it and it had the same token-printing code (removed on master in a7f649f6b9).
<!--
Provide a clear explanation of the reasoning behind this change, such as:
- A link to the issue being addressed, using the format "Fixes #ISSUE_NUMBER"
- An image showing the issue or problem being addressed (if not already in the issue)
- Error logs or callStacks to help with the understanding of the problem (if not already in the issue)
-->

### Changes & Results
Mostly the same edits made in master were done for the release/3.13 branch. Some items didn't apply (e.g. node for the various dependency audit checks that do not exist on the release/3.13 branch).

<!--
List all the changes that have been done, such as:
- Add new components
- Remove old components
- Update dependencies

What are the effects of this change?
- Before vs After
- Screenshots / GIFs / Videos
-->

### Testing
All CI checks and tests must pass.
Some testing was performed locally ( and #6403)

<!--
Describe how we can test your changes.
- open a URL
- visit a page
- click on a button
- etc.
-->

### Checklist

#### PR

<!--
https://semantic-release.gitbook.io/semantic-release/#how-does-it-work

Examples:
Please note the letter casing in the provided examples (upper or lower).

- feat(MeasurementService): add ...
- fix(Toolbar): fix ...
- docs(Readme): update ...
- style(Whitespace): fix ...
- refactor(ExtensionManager): ...
- test(HangingProtocol): Add test ...
- chore(git): update ...
- perf(VolumeLoader): ...

You don't need to have each commit within the Pull Request follow the rule,
but the PR title must comply with it, as it will be used as the commit message
after the commits are squashed.
-->

- [x] My Pull Request title is descriptive, accurate and follows the
  semantic-release format and guidelines.

#### Code

- [x] My code has been well-documented (function documentation, inline comments,
  etc.)

#### Public Documentation Updates

<!-- https://docs.ohif.org/ -->

- [x] The documentation page has been updated as necessary for any public API
  additions or removals.

#### Tested Environment

- [x] OS: Windows 11
- [x] Node version: 24.22.2
- [x] Browser: Chrome 156.0.8078.80
  <!--[e.g. Chrome 83.0.4103.116, Firefox 77.0.1, Safari 13.1.1]-->

<!-- prettier-ignore-start -->
[blog]: https://circleci.com/blog/triggering-trusted-ci-jobs-on-untrusted-forks/
[script]: https://github.com/jklukas/git-push-fork-to-upstream-branch
<!-- prettier-ignore-end -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fa151f51339`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.