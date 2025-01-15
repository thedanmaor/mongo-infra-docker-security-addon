# Usage

## This is an Add-on to the https://github.com/karl-denby/mongo-infra-minikube/ repo by Karl Denby
It is intended to be used ON TOP of this repo.

### Usage:
1. Clone the mongo-infra-minikube (MOM) repo, cd into the directory `mongo-infra-minikube/MEKO-opsmanager `
2. Update the template files with MongoDB version 8.0.4-ent (defaults are 6.0.0-ent\5.0.0-ent) for both the AppDB & the MongoDB replica sample
3. Run `quick-start.sh` to deploy OM + AppDB into the local minikube cluster (This process takes ~25 mins)
4. Deploy the "my-replica-sample" replica set into the minikube cluster via the `extras.sh` (This process takes ~10 mins)
5. Clone **this** repo into the mongo-infra-minikube/MEKO-opsmanager directory
6. Run `bash ssl-extras.sh`  and chose the option `Deploy-SSL-on-top-of-Sample` (This process takes ~10 mins)
7. Run `bash ssl-extras.sh`  and chose the option `Deploy-MDB-User`(This process takes ~1 mins)

### Cleanup
After you run `bash clean-up.sh` to remove the cluster, also run `bash cleanup-old-certs` to remove all old certificate files from the folder.

© Dan Maor (2025)
