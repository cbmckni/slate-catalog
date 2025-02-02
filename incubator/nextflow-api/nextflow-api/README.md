Deploy a Nextflow-API Server to Kubernetes Using SLATE

======

This guide assumes you have SLATE, access to a K8s cluster, and a valid PVC on that cluster.

#### 1. Configure Nextflow-API Server

The file `values.yaml` contains all of the configurable values across the chart. 

Edit the following values:

##### PVC
```
# PVC
LocalPVC:
  # If true, use existing PVC on local cluster.
  # (temp, future PVCs will be dynamically configurable)
  Enabled: true
  Name: deepgtex-prp
```

Change the "Name" to the PVC you have set up on your K8s cluster.

**TODO:** Remote cluster configuration(disregard and leave "False" for now)

##### Resources/Replicas

```
# Resource request per container
Resources:
  CPU: 250m
  Memory: 1Gi

# Number of containers
Replicas: 1
```

You may change the resource requests to your liking. Leave the number of replicas alone for now.


Now the server is configured and ready for deployment!

#### 2. Deploy Nextflow Server

##### Local SLATE Installation

Navigate to `slate-catalog/incubator/nextflow-api/`

Deploy using `slate app install --group my-group --cluster my-cluster --local nextflow-api`

#### 3. Use Nextflow Server

Get the instance ID with `slate instance list`

Get all info, including the externally accessible IP or URL with `slate instance info <instance ID>`

Navigate to the IP/URL with an internet browser. Then start using Nextflow! 

#### 4. Delete deployment

Get the instance ID with `slate instance list`

Then delete with `slate instance delete <instance_id>`

All done!


