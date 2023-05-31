---
title: Libp2p for Decentralized Applications
layout: post
tags: p2p, decentralization, javascript
description: Libp2p is a set of libraries useful for p2p computing. Libp2p provides the plumbing for building decentralized applications (DApps) and P2P platforms.
---

### What is libp2p?
Libp2p is a modular networking stack and protocol suite developed by [Protocol Labs](https://protocol.ai/). Libp2p forms one of the building webs of decentralized computational architecture along with [IPFS](/2023/05/31/IPFS-Decentralized-File-Storage.html) and [Smart Contracts](/2023/05/29/Interacting-with-Smart-Contracts-Ethereum-in-JavaScript.html). It is designed to provide a set of network protocols and components that can be used to build decentralized applications and peer-to-peer (P2P) systems.

Here are some key aspects and features of Libp2p:

1. Modular Architecture: Libp2p is designed with a modular architecture, which allows developers to choose and combine specific components based on their requirements. This modularity enables flexibility and interoperability in building P2P systems.

2. Network Agnostic: Libp2p is network agnostic, meaning it can work on various network protocols and transport mechanisms. It supports multiple protocols for communication, including TCP/IP, UDP, WebSockets, Bluetooth, and more.

3. Peer Discovery and Routing: Libp2p provides mechanisms for peer discovery and routing. It includes protocols such as Distributed Hash Tables (DHTs), Peer Routing, and Name Systems, which enable peers to find and connect with each other in a decentralized manner.

4. Secure Communication: Libp2p incorporates cryptographic protocols and secure transport mechanisms to ensure secure and authenticated communication between peers. It supports protocols like Transport Layer Security (TLS) and Secure Shell (SSH) for encryption and authentication.

5. Multi-Protocol Support: Libp2p supports multiple protocols for different functionalities, such as content-addressable storage (IPFS), pub-sub messaging (Gossipsub), decentralized naming systems (IPNS), and more. It allows developers to leverage these protocols while building P2P applications.

6. NAT Traversal: Libp2p provides techniques for traversing Network Address Translation (NAT) devices, which are commonly found in home and enterprise networks. These techniques allow peers behind NATs to establish direct connections with each other.

7. Peer Identity and Authentication: Libp2p incorporates peer identity management and authentication mechanisms. It uses cryptographic key pairs and digital signatures to establish trust between peers and ensure that messages are securely exchanged.

8. Extensibility: Libp2p is designed to be extensible, allowing developers to add and implement new protocols and components as needed. This enables the integration of custom functionalities and protocols into Libp2p-based applications.

9. Community and Ecosystem: Libp2p has a vibrant and active community of developers working on various projects and applications. It benefits from the broader ecosystem of Protocol Labs, which includes projects like IPFS (InterPlanetary File System) and Filecoin.

Libp2p serves as a foundational layer for building decentralized applications, distributed systems, and P2P networks. Its modular design, protocol flexibility, and secure communication capabilities make it a valuable tool for creating resilient, scalable, and decentralized systems.


### JavaScript Examples
To demonstrate some basic usage of Libp2p in JavaScript, here are two examples:

Example 1: Creating a Basic Libp2p Node and Handling Peer Discovery

	const Libp2p = require('libp2p');
	const TCP = require('libp2p-tcp');
	const PeerId = require('peer-id');
	
	async function createNode() {
	  const peerId = await PeerId.create();
	  const node = await Libp2p.create({
	    addresses: {
	      listen: ['/ip4/0.0.0.0/tcp/0']
	    },
	    modules: {
	      transport: [TCP],
	    },
	    peerId: peerId,
	  });
	
	  node.on('peer:discovery', (peerId) => {
	    console.log('Discovered peer:', peerId.toB58String());
	  });
	
	  await node.start();
	  console.log('Libp2p node started');
	}
	
	createNode();

Example 2: Establishing a Connection and Sending Messages

	const Libp2p = require('libp2p');
	const TCP = require('libp2p-tcp');
	const MPLEX = require('libp2p-mplex');
	const { NOISE } = require('libp2p-noise');
	const PeerId = require('peer-id');
	
	async function createNode() {
	  const peerId = await PeerId.create();
	  const node = await Libp2p.create({
	    addresses: {
	      listen: ['/ip4/0.0.0.0/tcp/0']
	    },
	    modules: {
	      transport: [TCP],
	      streamMuxer: [MPLEX],
	      connEncryption: [NOISE]
	    },
	    peerId: peerId,
	  });
	
	  node.on('peer:connect', (peerId) => {
	    console.log('Connected to peer:', peerId.toB58String());
	  });
	
	  await node.start();
	  console.log('Libp2p node started');
	
	  const targetPeerIdString = '<TARGET_PEER_ID>';
	
	  // Connect to a target peer
	  try {
	    const targetPeerId = PeerId.createFromB58String(targetPeerIdString);
	    await node.dial(targetPeerId);
	    console.log('Connected to target peer:', targetPeerIdString);
	
	    // Send a message to the target peer
	    const message = 'Hello from Libp2p!';
	    const { stream } = await node.dialProtocol(targetPeerId, '/libp2p/example/1.0.0');
	    await new Promise((resolve) => {
	      stream.write(message);
	      stream.end(resolve);
	    });
	    console.log('Message sent to target peer:', message);
	  } catch (error) {
	    console.error('Failed to connect to target peer:', error);
	  }
	}
	
	createNode();

### Examples of libp2p in Python

Example 1: Creating a Basic Libp2p Node and Handling Peer Discovery

	from libp2p import new_node
	from libp2p.crypto.keys import create_new_key_pair
	
	async def create_node():
	    private_key, _ = await create_new_key_pair()
	    node = await new_node(priv_key=private_key)
	
	    async def on_peer_discovery(peer_id):
	        print(f"Discovered peer: {peer_id}")
	
	    node.peerstore.host.add_peer_discovered_handler(on_peer_discovery)
	    await node.start()
	
	    print("Libp2p node started")
	
	await create_node()
	
Example 2: Establishing a Connection and Sending Messages

	from libp2p import new_node
	from libp2p.crypto.keys import create_new_key_pair
	from libp2p.peer.id import ID
	from libp2p.stream_muxer.mplex import MPLEX
	from libp2p.transport.tcp.tcp import TCP
	
	async def create_node():
	    private_key, _ = await create_new_key_pair()
	    node = await new_node(
	        priv_key=private_key,
	        listen_addrs=[("/ip4/0.0.0.0/tcp/0", TCP)],
	        muxer=MPLEX
	    )
	
	    async def on_peer_connect(peer_id):
	        print(f"Connected to peer: {peer_id}")
	
	    node.host.set_stream_handler("/libp2p/example/1.0.0", lambda stream: print(stream.read()))
	
	    node.peerstore.host.add_peer_connected_listener(on_peer_connect)
	    await node.start()
	
	    print("Libp2p node started")
	
	    target_peer_id_string = "<TARGET_PEER_ID>"
	
	    try:
	        target_peer_id = ID.from_base58(target_peer_id_string)
	        await node.connect(target_peer_id)
	        print(f"Connected to target peer: {target_peer_id_string}")
	
	        stream = await node.new_stream(target_peer_id, ["/libp2p/example/1.0.0"])
	        message = "Hello from Libp2p!"
	        await stream.write(message.encode())
	        print(f"Message sent to target peer: {message}")
	    except Exception as e:
	        print(f"Failed to connect to target peer: {e}")
	
	await create_node()




