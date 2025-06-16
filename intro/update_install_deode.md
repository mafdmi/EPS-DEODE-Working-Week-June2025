# Update and install Deode-Workflow
## If you have a local branch
1. `cd Deode-Workflow`
4. (if you don't have an "upstream" remote:) `git remote add upstream git@github.com:destination-earth-digital-twins/Deode-Workflow.git`
3. `git fetch upstream develop`
2. `git checkout <custom-branch-name>`
4. `git merge upstream/develop`
5. `poetry update`
6. `poetry install`

## If you don't have a local fork and branch
1. Make a fork if you haven't already
2. `git clone <fork-url>`
3. `cd Deode-Workflow`
4. `git remote add upstream git@github.com:destination-earth-digital-twins/Deode-Workflow.git`
5. `git fetch upstream`
6. `git checkout upstream/develop`
7. `git switch -c <custom-branch-name>`
9. `poetry install`