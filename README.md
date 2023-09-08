# Esign/.github

## Workflows
### Deployment
#### v1
This first version of the deployment workflow clones your repository to the runner, then rsyncs the entire contents,
except for a list of exclude paths, to the remote.

Caveats:
* Every path that exists on the remote, but also exists in the repository will always be overridden when the workflow
runs
* For non-empty folders on the remote that also exist in the repo, their contents will be cleared when the workflow
runs

#### v2
The second version of the deployment workflow addresses the v1 issues. This workflow no longer syncs the entire
contents, but only paths that have change between revisions. At the end of every workflow run, the currently deployed
revision SHA is written to the remote at .githubactionsrevision.
To accommodate full redeploys, a "Deploy from scratch" toggle was added. This mimics v1 behaviour.
