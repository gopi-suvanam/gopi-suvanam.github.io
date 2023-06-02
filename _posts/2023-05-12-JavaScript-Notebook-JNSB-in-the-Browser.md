---
title: JavaScript Notebook (JSNB) in the Browser
layout: post
description: JSNB a JavaScript Notebook provides an easy way to build and experiment in JavaScript using only browser based computation, without the need to install any packages or tools on the PC/server. Several interesting use-cases panning across scientific computation, finance and machine learning can be built on top of JSNB.
---

[JavaScript is a versatile programming language](/2023/02/22/Why-JavaScript-is-Great.html) and a [Jupyter like Notebook](/2023/01/01/Jupyter-like-JavaSript-Notebook.html) can further help in building solutions using JavaScript. [JSNB](/jsnb/#./examples/Hello-world.jsnb) is one such tool to do experimentation in JavaScript like Jupyter for Python. JavaScript Notebooks built on JSNB can be used to test code snippets and also for experimentation. 
Key features include:
- Easy to use javascript experimentation tool.
- Runs without backend (node.js/npm/pip install/ngnix etc etc). I call this a "nodeless" app for two reasons - 1. it does not require node and npm to use.. 2. it does not require a server (I didnt want to use the word "serverless" as that word has been polluted by Amazon).
- Can be loaded from the web (i.e. behind a webserver) or from the file system (certain features like WebRTC might require a server)
- UI is similar/close to Jupyter Notebook (for the sake familiarity for python developers). Has a minimalistic UI to put focus on user generated code/content.
- Light weight - uses Codemirror for formatting the code area and Pico CSS for styling.
- Comes pre-loaded with D3, Plotly and DI-Libs for power expereince. Other libraries can be loaded using the functions load_script and import_module.

**JSNB Screenshot**
![JSNB Screenshot](/assets/images/post_images/JSNB%20Screenshot.png)


JavaScript can be used for [financial calculations](/2023/04/06/Option-Pricing-using-Black-Scholes-in-JavaScript.html), [simulations/scientific calculations](/2023/04/25/Scientific-Simulation-in-JavaScript.html), [augmented reality (AR)](/2023/04/10/AR-in-JavaScript-using-React.html), [robotics](/2023/05/03/JavaScript-forRobotics.html), [machine learning](/2023/03/08/Machine-Learning-in-JavaScript.html), and [blockchain development](/2023/05/10/Integrating-Blockchain-in-Web-Application-MetaMask.html), to name a few use-cases. The below notebooks are samples/boilerplates to start experimenting/building some of these use-cases. Click on each link to play around with the code.

### Introductory Notebooks
- [Hello-world](/jsnb/#./examples/Hello-world.jsnb). An introductory notebook with a hello-world example.
- [For-loop vs Reduce](/jsnb/#./examples/Timing-experiment.jsnb). Compares performance of for-loop in javascript with that of the native function reduce.

### Graphs/Plotting
- [Plotly graphs](/jsnb/#./examples/Plotly-Example.jsnb). Shows usage of Plotly library for plotting graphs in the browser.
- [Using DI-Libs for Plots](/jsnb/#./examples/DI-Lib-Plots.jsnb). Plotting graphs suing the library - di-libs.js

### P2P and Decentralization
- [WebTorrent library](/jsnb/#./examples/WebTorrent-Example.jsnb). Using webtorrent for writing and reading files to torrents network in the browser.
- [Blockchain using Metamask](/jsnb/#./examples/Ethereum-Metamask.jsnb). Integrating web-applications with Blockchain via Metamask.
- [IPFS in the Browser using js-ipfs](/jsnb/#./examples/IPFS-in-Browser.jsnb). Accessing decentralized file system ipsf from the browser.

### Financial Computation
- [Option Pricing using Black-Scholes](/jsnb/#./examples/Black-Scholes.jsnb). Pricing options using the famous Black-Scholes formula.
- [Option Pricing using Monte-Carlo Simulation](/jsnb/#./examples/Option-Pricing-MC.jsnb). Pricing options using Monte-Carlo simulation rather than a closed form formula.

### Simulation
- [Monte-Carlo Simulation of AMM](/jsnb/#./examples/AMM-Simulation.jsnb). Simulating Automate-Market-Making for assets in a decentralized exchange.
- [Simple Simulation Example](/jsnb/#./examples/Simple-Simulation.jsnb). Simulation of a physical system - a ball bouncing off four walls.
- [Bouncing Ball on Moving Boundary](/jsnb/#./examples/Dynamic-Simulation.jsnb). Simulation of a physical system - a ball bouncing off four walls but with one of the walls oscillating.
- [Monte-Carlo Simulation of Football Odds](/jsnb/#./examples/Monte-Carlo-Simulation-of-Goals.jsnb). Simulation of football goals and probability of winning.

### Scientific Computation
- [Runge-Kutta Method for Solving Differential Equation](/jsnb/#./examples/Runge-Kutta-for-Differential-Equations.jsnb)

For updates on the tool checkout the github repo: [https://github.com/gopi-suvanam/jsnb](https://github.com/gopi-suvanam/jsnb)
Happy experimenting!!! 
