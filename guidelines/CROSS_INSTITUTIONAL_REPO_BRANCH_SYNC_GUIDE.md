# Cross-Institutional Repository Branch Syncing Guide


This guideline explains how to sync a certain branch of a private repo within your organization, with a branch from the corresponding repo of the lambda GitHub organization. This is useful in certain situations such as: only a part of your private repo is relevant for lambda and you want to only sync that part with the lambda work.


For example, lets say we have a private repo for computer vision within sbtc organisation: `sbtc-cv`, only open to sbtc members; and there is a corresponding repo within lambda organisation: `lambda-cv`, that is open to all lambda members. Only some parts of the `sbtc-cv` repo are relevant to lambda and I want to share only those parts with the `lambda-cv`. 

1) Go to `sbtc-cv` repo, create a branch -e.g., `lambda-sbtc`-, and add the lambda-relevant scripts to this branch. Commit & Push to its own remote on GitHub.
2) Go to `lambda-cv` repo and create a branch that will be synced to the `lambda-sbtc` branch of `sbtc-cv` repo, e.g., use the same branch name: `lambda-sbtc`. Push to its own remote on GitHub.
3) Inside `lambda-cv` repo, add `sbtc-cv` as a remote: ```git remote add [remote name: e.g., sbtc] [sbtc-cv repo URL]```.
4) Checkout to `lambda-sbtc` of `lambda-cv`.
5) Fetch `lambda-sbtc` of `sbtc-cv`: ```git fetch sbtc lambda-sbtc```.
6) Pull the changes of `lambda-sbtc` of `sbtc-cv` to your current branch/repo (i.e., `lambda-sbtc` of `lambda-cv`) by: ```git merge sbtc/lambda-sbtc```. Solve the conflicts, commit, and push.
7) Merge `lambda-sbtc` of `lambda-cv` to the `main` of `lambda-cv` when needed.
8) If you want two-way sync, go to `sbtc-cv` repo, add `lambda-cv` as a remote: ```git remote add [remote name: e.g., lambda] [lambda-cv repo URL]```, and do the symetric approach of 4) to 7).