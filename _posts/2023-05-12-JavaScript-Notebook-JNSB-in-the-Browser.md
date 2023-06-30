---
title: Scribbler: JavaScript Notebook in the Browser
layout: post
description: Scribbler a JavaScript Notebook provides an easy way to build and experiment in JavaScript using only browser based computation, without the need to install any packages or tools on the PC/server. Several interesting use-cases panning across scientific computation, finance and machine learning can be built on top of Scribbler.
---

[JavaScript is a versatile programming language](/2023/02/22/Why-JavaScript-is-Great.html) and a [Jupyter like Notebook](/2023/01/01/Jupyter-like-JavaSript-Notebook.html) can further help in building solutions using JavaScript. [Scribbler](/jsnb/#./examples/Hello-world.jsnb) is one such tool to do experimentation in JavaScript like Jupyter for Python. JavaScript Notebooks built on Scribbler can be used to test code snippets and also for experimentation. 
Key features include:
- Easy to use javascript experimentation tool.
- Runs without backend (node.js/npm/pip install/ngnix etc etc). I call this a "nodeless" app for two reasons - 1. it does not require node and npm to use.. 2. it does not require a server (I didnt want to use the word "serverless" as that word has been polluted by Amazon).
- Can be loaded from the web (i.e. behind a webserver) or from the file system (certain features like WebRTC might require a server)
- UI is similar/close to Jupyter Notebook (for the sake familiarity for python developers). Has a minimalistic UI to put focus on user generated code/content.
- Light weight - uses Codemirror for formatting the code area and Pico CSS for styling.
- Comes pre-loaded with D3, Plotly and DI-Libs for power expereince. Other libraries can be loaded using the functions load_script and import_module.

**Scribbler Screenshot**
![Scribbler Screenshot](/assets/images/post_images/JSNB%20Screenshot.png)


JavaScript can be used for [financial calculations](/2023/04/06/Option-Pricing-using-Black-Scholes-in-JavaScript.html), [simulations/scientific calculations](/2023/04/25/Scientific-Simulation-in-JavaScript.html), [augmented reality (AR)](/2023/04/10/AR-in-JavaScript-using-React.html), [robotics](/2023/05/03/JavaScript-forRobotics.html), [machine learning](/2023/03/08/Machine-Learning-in-JavaScript.html), and [blockchain development](/2023/05/10/Integrating-Blockchain-in-Web-Application-MetaMask.html), to name a few use-cases. The below notebooks are samples/boilerplates to start experimenting/building some of these use-cases. Click on each link to play around with the code.

<iframe src="https://decentralized-intelligence.com/jsnb/examples/README" class="is-fullwidth" onload="this.style.height=(this.contentWindow.document.body.scrollHeight+20)+'px';"></iframe>

For updates on the tool checkout the github repo: [https://github.com/gopi-suvanam/jsnb](https://github.com/gopi-suvanam/jsnb)
Happy experimenting!!! 
