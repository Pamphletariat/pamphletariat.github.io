## Maintainer Workflow (Normal, Do-This-Every-Time)

Pamphletariat is a publication. The maintainer workflow is intentionally simple:

> **Look at the PR locally → make any necessary fixes → commit directly to ********************`main`********************.**

No PR-branch editing. No pushing contributor branches. No special cases.

---

### The normal workflow (this is the default)

Use this whenever you want to **see the pamphlet locally** and **make changes yourself** before publication.

1. Make sure you are on `main` and up to date:

   git checkout main

   git pull

2. Apply the PR to your working tree (without creating a branch):

   gh pr checkout <PR_NUMBER> --patch

   This applies the PR’s changes directly onto your current `main` working tree.
   Nothing is committed yet.

3. Build and preview the site locally:

   ./watch.pl

4. Make any required changes:

   * formatting fixes
   * build compatibility fixes
   * mechanical normalization

5. Commit the final, published result:

   git add .

   git commit -m "Publish pamphlet (with build normalization)"

   git push

6. Close the PR:

   gh pr close <PR_NUMBER> --comment "Applied and published with editorial normalization."

That’s it. This is the entire process.

---

### Things you should *not* do

* Do **not** use `gh pr checkout` without `--patch`
* Do **not** commit on PR branches
* Do **not** push contributor branches
* Do **not** try to "fix the PR" instead of the publication
