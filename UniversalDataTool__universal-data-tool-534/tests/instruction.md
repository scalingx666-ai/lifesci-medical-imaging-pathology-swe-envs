# Issue

**Title:** Fix the problem images disappear with a large number of labels in Image Classification, together with small UI improvements.

## Description

Related with #533 

Fix the problem images disappear with a large number of labels
- By adding min-height to the `ImageContainer`

![chrome_OUnsocKWma](https://user-images.githubusercontent.com/25426917/153711987-53d28dbd-2713-4680-a17b-cab28f60aa19.png)

---

And also with Small UI improvements:
- Fix "strange" bottom scroll bar
- Make JSON Editor full of the window's height instead of default's 500px

When Image Classification, there is a bottom scroll bar which seems strange and unnecessary:

![firefox_ox34mfNpSO](https://user-images.githubusercontent.com/25426917/153711795-98607b8f-2557-4a47-8438-0144d9a7c056.png)

And also make the JSON Editor full of the window's height for more visibility:
 
![chrome_9hKOE9GAsh](https://user-images.githubusercontent.com/25426917/153711899-7c16fd0f-568c-4915-9ebb-685685069d8c.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf44212a654a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.