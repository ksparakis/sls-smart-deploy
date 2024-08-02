# sls-smart-deploy
In your pipeline detect which handlers have had code changes that affect them, and deploy lambdas individually when possible, to speed up deployments.


# Introduction
One issue I have constantly ran into as a serverless engineer is that when deploying my serverless project it can take forever even for a small change.
So here I introduce sls-smart-deploy.

Buisness logic works as follows:

- Create a map of all functions. This will find the relationship between a handler and any down stream code changes.
- Using git figure out what files/functions have had changes, and calculate which handlers have been affected.
- Itterate and deploy those handlers individually (concurrently if possible)
- Do a full deploy if severless yaml, package.json or 
