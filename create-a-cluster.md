## Create a Kubernetes Cluster

1\. Go to <https://console.cloud.google.com/>.

2\. Select or create your *project*.

3\. Click on the *Activate Cloud Shell* button:

```
Welcome to Cloud Shell! Type "help" to get started.
Your Cloud Platform project in this session is set to your-google-project.
Use “gcloud config set project [PROJECT_ID]” to change to a different project.
user@cloudshell:~ (your-google-project)$
```

4\. Set the default zone to `europe-west1-c` (it's in Belgium!):

```
user@cloudshell:~ (your-google-project)$ gcloud config set compute/zone europe-west1-c
Updated property [compute/zone].
```

5\. Make sure that you have the Kubernetes Engine API enabled:

```
user@cloudshell:~ (your-google-project)$ gcloud services enable container.googleapis.com
Operation "operations/acf.de16a8e7-1b0d-484d-aa9b-a61283157476" finished successfully.
```

***Remark:*** This operation can take quite some time!

6\. Create a new Kubernetes cluster, called `cluster-01`, with 4 servers/nodes using the latest version of Kubernetes:

```
user@cloudshell:~ (your-google-project)$ gcloud container clusters create cluster-01 \
  --cluster-version=latest \
  --num-nodes 4
WARNING: Currently VPC-native is not the default mode during cluster creation. In the future, this will become the default mode and can be disabled using `--no-enable-ip-alias` flag. Use `--[no-]enable-ip-alias` flag to suppress this warning.
WARNING: Newly created clusters and node-pools will have node auto-upgrade enabled by default. This can be disabled using the `--no-enable-autoupgrade` flag.
WARNING: Starting with version 1.18, clusters will have shielded GKE nodes by default.
WARNING: Your Pod address range (`--cluster-ipv4-cidr`) can accommodate at most 1008 node(s).
This will enable the autorepair feature for nodes. Please see https://cloud.google.com/kubernetes-engine/docs/node-auto-repair for more information on node autorepairs.
Creating cluster cluster-01 in europe-west1-c... Cluster is being health-checked (master is healthy)...done.
Created [https://container.googleapis.com/v1/projects/play-with-consul-at-ing/zones/europe-west1-c/clusters/cluster-01].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/europe-west1-c/cluster-01?project=play-with-consul-at-ing
kubeconfig entry generated for cluster-01.
NAME        LOCATION        MASTER_VERSION  MASTER_IP      MACHINE_TYPE   NODE_VERSION   NUM_NODES  STATUS
cluster-01  europe-west1-c  1.15.11-gke.9   35.187.76.183  n1-standard-1  1.15.11-gke.9  4          RUNNING
```