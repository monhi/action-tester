# Action Tester
This repository is cretaed to test the Github Action feature which helps developers to release their packages in GitHub automatically when they commit and push the changes to repos.

for more information please have a look at following link:

https://github.com/features/actions

As I would like to see how these feature works, I create this repo and test action feature step by step.

the `.github/workflow/deploy.yml` is the workflow file for this project.

Now only windows setup package is working but I also have a plan for MacOS and Linux operating systems.

To create a new setup package I follow this steps:
```
add some changes to the code.
git status # to see which files are changed.
git add .  # to add all changes 
git commit –m "new contents are added to the local repo"      # to commit changes and also find the sha of commit.
git push origin main # adding new contents to the remote repository in GitHub.
git log --oneline   # to find the commit_sha of the last commit.
git tag –a vx.y.z commit_sha –m "Message"  # here vx.y.z is the semantic version for newly commited contents (for example v1.0.0) and commit_sha is the sha of final commit.
git push origin --tags # here we commit to the tags and it triggers action file to run and produce new release 
```
I developed my workflow in a way that it runs when a new tag with semantic version number is created.
It is important that the semantic version number begins with 'v' character. for example v1.0.1 activates the workflow file.
```
on:
  push:
    tags:
      - 'v*'
```
To see the generated setup pacakges, please have a look at following link in this repo:

https://github.com/monhi/action-tester/releases/




