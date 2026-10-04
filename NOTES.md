# Patch Notes

## 1. Summary of changes

* Fixed task search SQL so archived tasks are excluded from both title and description matches.
* Removed the artificial query delay (`Thread.sleep`) from the task search endpoint.
* Added validation for invalid pagination values (`page < 1` or `pageSize < 1`), returning HTTP 400.
* Added validation for invalid task status values, returning HTTP 400 instead of HTTP 500.

## 2. What I chose not to change

I kept the patch focused on the highest-value confirmed issues. Existing pagination boundaries and status-filter reset behavior were tested and worked correctly. I did not add broader refactoring or changes to unrelated areas because they were outside the focused patch and timebox.

## 3. Biggest remaining risk

The API does not currently enforce an upper limit on `pageSize`. A very large value could increase memory usage and response time as the dataset grows.

## 4. Tools / AI used

I used AI assistance to inspect the code, identify bug causes, plan focused fixes, and guide reproduction/testing. I reviewed the suggested changes, implemented them in the repository, and manually verified the affected API behavior and application startup.
