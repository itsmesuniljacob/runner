# GitHub Actions Runner

[![Runner - Build and Deploy](https://github.com/ebomart/github-k8s-runner/actions/workflows/deploy-k8s-runner.yml/badge.svg)](https://github.com/ebomart/github-k8s-runner/actions/workflows/deploy-k8s-runner.yml)

<p align="center">
  <img src="https://github.com/actions/runner/blob/main/docs/res/github-graph.png">
</p>


The runner is the application that runs a job from a GitHub Actions workflow.


## References

This work is largely based on the work done by [Sander Knape](https://sanderknape.com/2020/03/self-hosted-github-actions-runner-kubernetes/) and [David Karlsen](https://github.com/evryfs/github-actions-runner-operator/):

**Modifications:**
- Added a sidecar docker-dind with TLS TCP communication between the client and the daemon containers
- Made it dedicated to establish a pool of runners associated to a GitHub organization, not to a particular repository
- Added a way to prefix the runners names (with RUNNER_NAME_PREFIX env variable)
- Removed the sudo package, sudo group and passwordless sudoers from the container user
- Added a way to use self signed certificates for a local registry as a config map
