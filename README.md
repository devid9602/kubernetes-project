# Kubernetes Learning Labs

A collection of Kubernetes notes and manifests for practicing core workload resources and persistent storage. Topics include Pods, ReplicaSets, Deployments, labels and selectors, and examples using PersistentVolumes, PersistentVolumeClaims, StorageClasses, and NFS.

## Repository layout

- `Kubernetes-Basic-Advance-Labs/Pod-ReplicaSet-examples/`: notes and examples covering Pods, namespaces, ReplicaSets, Deployments, labels, and selectors.
- `nfs-storage-class/`: NFS-oriented storage examples and a reference for statically provisioned storage.
- Other YAML and text files provide additional examples and command notes; inspect each manifest before applying it.

## Requirements

- A Kubernetes cluster and a correctly configured `kubectl` context.
- For the NFS examples, an NFS server/export reachable from cluster nodes and storage settings that match your environment.
- Some examples reference external container images. Confirm the image and its requirements before using it.

## Working with the examples

Read the matching notes and inspect the YAML first. Adapt namespaces, image names, NFS server/export paths, and storage sizes to your cluster. Apply related resources in dependency order—for example, a StorageClass or PersistentVolume before its claim and workload—and verify the result with:

```sh
kubectl get pods,deployments,services,pv,pvc,storageclass --all-namespaces
```

The static-storage reference uses `hostPath`, which is suitable only for single-node testing and is not shared or durable storage for a multi-node production cluster. NFS manifests also need a real, reachable export configured for your environment.

Some notes include a MySQL container example. It expects passwords to be provided through local environment variables; do not commit actual credentials or use sample database settings for production. These materials are learning examples, not a supported production platform.
