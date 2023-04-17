---
title: Primitives of Decentralized Computing/P2P Computing
layout: post
description: Decentralized computing (!=Blockchain) consists of a set of tools to perform computing activities without a server. We look at what is the most basic set of primitives from which generic decentralized computing platforms can be constructed.
---
Decentralized computing/Peer-to-peer (P2P) computing relies on a set of primitives to enable the development and deployment of distributed applications. Some of the key primitives for P2P computing are:

### Peer-to-peer networks

Peer-to-peer (P2P) networks are a type of decentralized network architecture in which each node in the network can act as both a client and a server, sharing resources and data with other nodes on the network. In P2P networks, there is no centralized server that manages the network or controls the flow of data. Instead, each node in the network is responsible for maintaining and sharing a portion of the resources and data available on the network.

P2P networks can be classified into two main categories: structured and unstructured. Structured P2P networks use a distributed hash table (DHT) to organize and locate resources, while unstructured P2P networks rely on flooding or gossip protocols to share information and locate resources.


### Distributed hash tables (DHT)

A Distributed Hash Table (DHT) is a decentralized data structure used in peer-to-peer (P2P) networks. It is a way of storing and retrieving information without relying on a centralized server.

A DHT is a hash table that is distributed across many nodes in a P2P network. Each node in the network maintains a small part of the hash table and is responsible for storing and retrieving data associated with a particular set of keys. The keys are hashed to determine which node in the network is responsible for storing and retrieving the corresponding data.

DHTs provide a decentralized way of storing and retrieving data that is highly scalable and fault-tolerant. Because the hash table is distributed across many nodes, it can easily handle large amounts of data and traffic. Additionally, if a node fails or goes offline, the data can still be accessed from other nodes in the network.

DHTs are widely used in P2P networks for various applications, such as file sharing, content distribution, and messaging. Some popular examples of DHT-based networks include BitTorrent, the InterPlanetary File System (IPFS), and the Kademlia network used by the eDonkey and eMule file sharing clients.


### Routing protocols

Routing protocols enable nodes to discover and communicate with other nodes in the network, even when the network topology is constantly changing. Routing protocols are a set of rules or algorithms that enable nodes in a network to find the best path to reach a particular destination node. In other words, they are used to determine the optimal route for data to travel from one node to another in a network.

Routing protocols are essential for communication networks, including the internet, to work efficiently and effectively. There are several types of routing protocols used in different types of networks, such as:

Distance Vector Routing: In this type of routing, each node maintains a table that contains information about the distance and direction to each of its neighboring nodes.

Link-State Routing: In this type of routing, each node maintains a map of the entire network and calculates the shortest path to reach a particular destination using Dijkstra's algorithm.

Path Vector Routing: This type of routing is similar to distance vector routing, but it also takes into account other factors such as policy, network topology, and the path taken by the data.

Hybrid Routing: This is a combination of two or more routing protocols, where each protocol is used for a different part of the network.

Routing protocols enable efficient and reliable communication between nodes in a network, and they are essential for many types of applications and services, such as online gaming, video conferencing, and file sharing.

### Resource discovery

Resource discovery in peer-to-peer (P2P) networks refers to the process of finding and accessing resources, such as files, services, and applications, that are available on other nodes in the network.

In a P2P network, each node is responsible for maintaining and sharing a portion of the resources available on the network. Resource discovery enables nodes to discover and access these resources in a decentralized and efficient manner, without relying on a centralized server or directory.

There are several approaches to resource discovery in P2P networks, including:

Centralized approach: In this approach, a centralized directory or index is maintained that contains information about the location of resources in the network. Nodes can query the directory to find the resources they need.

Flooding: In this approach, a node sends out a broadcast message to all other nodes in the network requesting the desired resource. If a node has the requested resource, it sends a response back to the requesting node.

Distributed Hash Tables (DHT): In a DHT-based approach, the resources are stored on nodes in the network, and a DHT is used to store the location information of these resources. Nodes can query the DHT to find the resources they need.

Hybrid approaches: These approaches combine multiple methods, such as using a centralized directory and a DHT, to provide efficient and reliable resource discovery.

Resource discovery is a crucial aspect of P2P networks, as it enables nodes to access the resources they need and ensures that the network is utilized efficiently.

### Security protocols

Security protocols are an essential aspect of peer-to-peer (P2P) networks, as they help to ensure the confidentiality, integrity, and availability of data and resources shared on the network. Some of the common security protocols used in P2P networks include:

Authentication: This protocol is used to verify the identity of nodes in the network. Nodes may use digital certificates, usernames and passwords, or other forms of authentication to ensure that they are communicating with the intended node.

Encryption: This protocol is used to protect the confidentiality of data transmitted on the network. Data is encrypted using algorithms such as AES, RSA, or Blowfish, which make it unreadable to unauthorized parties.

Digital Signatures: This protocol is used to verify the authenticity and integrity of data. Digital signatures are created using cryptographic algorithms, which ensure that data has not been tampered with during transmission.

Firewall: This protocol is used to prevent unauthorized access to the network. Firewalls can be configured to block certain types of traffic, such as traffic from known malicious sources.

Intrusion Detection and Prevention: These protocols are used to detect and prevent unauthorized access to the network. They can detect and block known or suspected malicious traffic, as well as alert network administrators to potential security breaches.

Virtual Private Networks (VPNs): This protocol is used to create a secure connection between nodes on the network. VPNs encrypt data transmitted between nodes, ensuring that it cannot be intercepted or read by unauthorized parties.

Together, these primitives provide the building blocks for P2P computing, enabling the development of distributed applications that are scalable, fault-tolerant, and resilient.





