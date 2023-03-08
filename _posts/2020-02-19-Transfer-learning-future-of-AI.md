---
layout: post
title: Transfer Learning - The Future of AI
description: Transfer learning is a technique of machine learning where models learnt from one data set are applied to another problem.
---

Transfer learning is a paradigm of machine learning often looked at in conjunction with End to End learning. End to end learning is paradigm in machine learning where an algorithm takes inputs and desired actions, to learn a function that maps input to output. An example is an end to end autonomous driving system which takes millions of hours of car videos to learn driving. AI practitioners prefer this paradigm of machine learning because they do not have to get external expertise. Also as everything is learnt from data, there will be very little “hard coding”. There are several problems with this logic:

1. It requires way too much of data
2. As everything will become a black box there is no way to debug certain behavior
3. Each application will have to start from scratch and cannot leverage upon learning in other applications
4. Using this approach, the algorithm will only learn to respond to events that are similar to events in the training data set, it may not extrapolate well to unseen circumstances
5. It requires large amount off computational power

A much better alternative paradigm is “Transfer Learning”. We humans do transfer learning all the time. For example we learn about objects and shapes since childhood. We learn about directions and road signs later in life. We learn motor skills again through our childhood. When we have to learn how to drive a car, we do not start from scratch. We use all the learning we have gained using various other activities to learn a car quickly. Because of this type of learning we don’t have to go through several thousands of hours of training. We will also be easily able to extrapolate our learning to different types of cars, different roads, different scenarios we might encounter while driving. We colloquially call this “common sense”. Transfer learning is a critical piece both for [Small Data AI](/2021/05/26/Small-Data-AI.html) and [Decentralized AI](/2023/02/25/Decentralized-Artificial-Intelligence.html). 

Transfer learning is already being put to use in several areas of AI. A good example of transfer learning is in text analytics using vector representations of words. Machines are better at understanding numbers than symbols. So most of natural language processing tools in AI convert text into numbers and use the numbers to derive information. If someone wants to get sentiment of a tweet they can take the numeric representation of the tweet and learn by tagging several tweets as positive or negative. So where does transfer learning come into play? For a single entity to tag millions of tweets as positive or negative and learn from that will be near to impossible. A better approach will be for one entity to build a tool to convert tweets into numbers (thus reducing the conditionality of the tweet) and another entity to use those numbers to build a sentiment model for a limited set of tweets. First entity is transferring the learning to the second entity, hence the paradigm is called transfer learning. This entity can further transfer it machine learnt model of sentiment to another entity who can use it for building marketing campaign models, so on and so forth.

This modularization of learning suddenly helps in scaling AI to massive levels. entities like Google, who scrape content across the internet can build the low level models of processing raw data. Specialized entities can build the next layer. For example layers to detect/recognize faces, get sentiment and intent from text etc. there could be higher layers who can build models for applications. These include stock market trading, fraud detection and autonomous driving.
![Transfer Learning Architecture](/assets/images/post_images/transfer-learning.png)

### Code Examples of Transfer Learning
Transfer learning can be implemented using various machine learning frameworks in both JavaScript and Python. Here are some examples:
#### Tensorflow.js
Transfer learning can be implemented in JavaScript using the TensorFlow.js library. Here's an example:
    // Load the MobileNet model
    const mobileNet = await tf.loadLayersModel('https://storage.googleapis.com/tfjs-models/tfjs/mobilenet_v1_0.25_224/model.json');

    // Freeze all the layers except the last one
    for (let i = 0; i < mobileNet.layers.length - 1; i++) {
      mobileNet.layers[i].trainable = false;
    }

    // Create a new model that takes the MobileNet as input
    const model = tf.sequential();
    model.add(mobileNet);
    model.add(tf.layers.flatten());
    model.add(tf.layers.dense({ units: 256, activation: 'relu' }));
    model.add(tf.layers.dropout({ rate: 0.5 }));
    model.add(tf.layers.dense({ units: 1, activation: 'sigmoid' }));

    // Compile the model
    model.compile({
      optimizer: tf.train.adam(),
      loss: 'binaryCrossentropy',
      metrics: ['accuracy'],
    });

    // Train the model using transfer learning
    model.fit(dataset, {
      epochs: 10,
      stepsPerEpoch: Math.ceil(numExamples / batchSize),
      callbacks: {
        onEpochEnd: async (epoch, logs) => {
          console.log(`Epoch ${epoch + 1}: loss = ${logs.loss.toFixed(4)}, accuracy = ${logs.acc.toFixed(4)}`);
        },
      },
    });
    
#### Tensorflow in Python
    # Load the MobileNet model
    base_model = tf.keras.applications.MobileNetV2(input_shape=(224, 224, 3), include_top=False, weights='imagenet')

    # Freeze all the layers except the last one
    for layer in base_model.layers[:-1]:
        layer.trainable = False

    # Add a new classifier on top
    x = base_model.output
    x = tf.keras.layers.GlobalAveragePooling2D()(x)
    x = tf.keras.layers.Dense(256, activation='relu')(x)
    x = tf.keras.layers.Dropout(0.5)(x)
    predictions = tf.keras.layers.Dense(1, activation='sigmoid')(x)

    # Create the new model
    model = tf.keras.models.Model(inputs=base_model.input, outputs=predictions)

    # Compile the model
    model.compile(optimizer=tf.keras.optimizers.Adam(lr=0.001), loss='binary_crossentropy', metrics=['accuracy'])

    # Train the model using transfer learning
    history = model.fit(train_dataset, epochs=10, steps_per_epoch=train_steps_per_epoch, validation_data=val_dataset, validation_steps=val_steps_per_epoch)

Note: These are just examples and may need to be modified based on the specific use case and dataset being used.







