# Hyperledger Fabric on Kubernetes of Qloud Container Service


[Hyperledger Fabric](https://hyperledger.org/projects/fabric) is one of the most popular blockchain infrastructures in the world, which is open sourced and hosted by Linux Foundation.

## Introduction
This chart implements a solution of automatic configuration and deployment for Hyperledger Fabric. 

A NAS (NFS protocol) shared file storage is needed for: 1. distribution of crypto and configurations; 2. data persistence for most services.

Currently v1.1.0 of Hyperledger Fabric is supported.

Blockchain Explorer is supported.


The following table lists the configurable parameters of this chart and their default values.

| Parameter                  | Description                        | Default                                                    |
| -----------------------    | ---------------------------------- | ---------------------------------------------------------- |
| `dockerImageRegistry` | Docker image registry. Refer to values.yaml inside this chart for qloudchain options.                | `registry.cn-hangzhou.aliyuncs.com/cos-solution`                                        |
| `externalAddress` | Public IP for application outside cluster to access blockchain network | `1.2.3.4` |
| `fabricNetwork` | Name of blockchain network | `network01` |
| `fabricChannel` | Name of initial channel in blockchain network | `bankchannel` |
| `ordererNum` | Number of orderers | `3` |
| `orgNum` | Number of peer organizations. There will be two peers created for each organization for HA. So the total number of peers will be (orgNum * 2) | `2` |
| `ordererDomain` | Domain of orderers | `qloudchain.com` |
| `peerDomain` | Domain of peers | `qloudchain.com` |
| `caExternalPortList` | NodePort list for CA services | `["31054", "31064"]` |
| `ordererExternalPortList` | NodePort list for orderer services | `["31050", "31060", "31070"]` |
| `peerExternalGrpcPortList` | NodePort list for peer services via gRPC | `["31051", "31061", "31071", "31081"]` |
| `peerExternalEventPortList` | NodePort list for peer services via eventing | `["31053", "31063", "31073", "31083"]` |
| `imagePullPolicy` | Image pull policy | `IfNotPresent` |
| `hyperledgerFabricVersion` | Version of Hyperledger Fabric. Currently support 1.1.0 | `1.1.0` |
| `thirdPartyImageVersion` | Version of third-party images of Hyperledger Fabric, like CouchDB, ZooKeeper, Kafka | `0.4.6` |
| `explorer.enabled` | Whether to enable built-in Blockchain Explorer or not, which will create a LoadBalancer and expose a Web UI for monitoring blockchain network | `true` |
