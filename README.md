# Usage

## This is a security add-on for the [mongo-infra-minikube](https://github.com/karl-denby/mongo-infra-minikube) repo by Karl Denby.
It is intended to be used ON TOP of this repo.

## Problem this repo solves:
Allows you to deploy a sample replica set which has **TLS** and **Authorization** enabled as well as deploys a managed user for **Authentication** on top of your existing Replica Set Sample. This can be used to Repro secure deployment issues on K8s.

### Usage:
## Before using this repo:
1. Clone the [mongo-infra-minikube](https://github.com/karl-denby/mongo-infra-minikube) repo, cd into the directory `mongo-infra-minikube/MEKO-opsmanager`.
2. Update the template files with MongoDB version 8.0.4-ent (defaults are 6.0.0-ent\5.0.0-ent) for both the AppDB & the MongoDB replica sample.
3. Run `bash quick-start.sh` to deploy OM + AppDB into the local minikube cluster (This process can take ~25 - ~35 mins).
   * Select EKO version `1.30.0` & Ops Manager version `8.0.2`.
4. Portforward local traffic into the cluster with `kubectl port-forward pod/mongo-infra-minikube-0 8080:8080 2>&1 > /dev/null &` 
5. Run `bash extras.sh` and choose the option `Deploy-Sample` (This process takes ~10 mins).
   This will setup the organization and deploy a non-secure Sample.

// kubectl delete pod/my-replica-sample-0 before deployinth the ssl set

### After you have a running cluster with OM, AppDB & port forwarding open:
1. Clone **this** repo into the `mongo-infra-minikube/MEKO-opsmanager directory` using these commands:
```
git clone https://github.com/thedanmaor/mongo-infra-docker-security-addon.git 
mv mongo-infra-docker-security-addon/* .
rm -rf mongo-infra-docker-security-addon
```
2. Run `bash security-extras.sh`  and choose the option `Deploy-Secure-Sample` (This process takes ~10 mins).
3. Run `bash security-extras.sh`  and choose the option `Deploy-MDB-User`(This process takes ~1 mins).

### Cleanup
After you run `bash clean-up.sh` to remove the cluster, also run `bash cleanup-old-certs.sh` to remove all old certificate files from the folder.

© Dan Maor (2025)
