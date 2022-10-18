# Go Ethereum - GETH

**The most popular standalone ethereum client software to join or create ethereum blockchain.**

[Official Link for Installation](https://geth.ethereum.org/docs/install-and-build/installing-geth "Official Link for Installation")

**This section of the repository is dedicated to the installation of private ethereum network using geth client software on Kubernetes.**

- To make this simple, and ready to go we used on of the Public Cloud Kubernetes Solution of AWS known as EKS.
- We have used POA ( Proof Of Authority ) as an consensus mechanism to create ethereum private blockchain setup.

**How it differs from the other kubernetes solution** ?
Answer - Persistent Volume is being used with statefulset, the implementation may differ with respect to different providers of kubernetes.
Under the hood, the concept of Persistent volume remains same for all ( Storage Class, Persistent Volume, Persistent Volume Claim Template.)

**My Assumptions, One going through this must be aware about..
**
- Ethereum Blockchain, specifically Private Blockchain.
- Ethereum Private Blockchain setup on plain host machines or virtual machines.
- Consensus Mechanism ( POA, POW)
-  Working Kubernetes Cluster setup.

Let's Familiar with the Directory Structure and the Setup

1.  Bootnode
	Contains the k8s manifest files related to bootnode.
2. Init Node
	 It contains the initial predefined very first blockchain node spawned to initialize the private blockchain network.
	 
	 Why Init Node ?
	 - POA Blockchain setup initilization must contain atleast one signer within **genesis**  file
	 - Every Nodes joining the same private blockchain setup must initialize itself with the same **genesis** file
	 - Init Node or the Node with Signer Account is the only node responsible to create new blocks till the time blockhain network approves new signers to the **write/validate** new blocks.
	 - Init Node contains predefined signer account details composed in an individual container.
	 
3. Nodes 
	Contains the manifest files for the regular transaction nodes.
	 

------------

![Pods Deployment Strategy Design](img/pods-deployment-strategy.png"Pods Deployment Strategy Design")