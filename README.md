### Introduction

This repository is an offshoot of https://github.com/gnunn-gitops/acm-hub-bootstrap

### Bootstrap Process

The bootstrap process, encapsulated in the `bootstrap.sh` script, is as follows:

1. Deploy all of the RHACM policies including the policy that deploys the OpenShift
GitOps operator with the bootstrap application
2. Label the Hub cluster, `local-cluster`, with the label `gitops=local.hub`. This trigger the
GitOps policy we deployed in step #3 to install OpenShift GitOps on the Hub cluster and
deploy the bootstrap application pointing to the repo and path needed for this cluster, i.e.
`local.home`

At this point the GitOps operator deploys everything the Hub cluster requires including storage, operators, etc
as well as other ACM components. In particular, the components that the script deployed (Hub + Policies) have
Argo applications that will take over managing these.