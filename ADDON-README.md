# Usage

## This is a security add-on for the `https://github.com/karl-denby/mongo-infra-minikube` repo by Karl Denby.
It is intended to be used ON TOP of this repo.

## Problem to solve:

Automatically Enables **TLS** and **Authorization** as well as deploys a managed user for **Authentication** on top of your existing Replica Set Sample.
### Usage:

#### Before using this repo.
1. Clone the mongo-infra-minikube repo, cd into the directory `mongo-infra-minikube/MEKO-opsmanager`.
2. Update the template files with MongoDB version 8.0.4-ent (defaults are 6.0.0-ent\5.0.0-ent) for both the AppDB & the MongoDB replica sample.
3. Run `bash quick-start.sh` to deploy OM + AppDB into the local minikube cluster (This process takes ~25 mins).
   * Select EKO version `1.30.0` & Ops Manager version `8.0.2`.

### MIGHT BE USELESS
# 4. Run `bash extras.sh` and choose the option `Deploy-Sample` (This process takes ~10 mins).
Also reuires to run
kubectl delete pod/my-replica-sample-0 before deployinth the sssl set

### After you have a running cluster with OM, AppDB & the sample replica set:
5. Clone **this** repo into the `mongo-infra-minikube/MEKO-opsmanager directory` using these commands:
```
git clone https://github.com/thedanmaor/mongo-infra-docker-security-addon.git 
mv mongo-infra-docker-security-addon/* .
rm -rf mongo-infra-docker-security-addon
```
9. Run `bash ssl-extras.sh`  and choose the option `Deploy-SSL-on-top-of-Sample` (This process takes ~10 mins).
10. Run `bash ssl-extras.sh`  and choose the option `Deploy-MDB-User`(This process takes ~1 mins).

### Cleanup
After you run `bash clean-up.sh` to remove the cluster, also run `bash cleanup-old-certs` to remove all old certificate files from the folder.

© Dan Maor (2025)
