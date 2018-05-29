---
layout: post
title:  "Anti AI AI"
date:   2017-5-19 8:34:25
categories: mediator feature
tags: featured
image: /assets/article_images/header_old.png
image2: /assets/article_images/header_old-mobile.jpg
---

# Anti Ai Ai — Wearable Artificial Intelligence

The [post-truth](https://en.wiktionary.org/wiki/post-truth#English) era is just getting started. Near the end of 2017 we’ll be consuming content synthesised to mimic real people. Leaving us in a sea of [disinformation](https://en.wikipedia.org/wiki/Disinformation) powered by AI and machine learning. The media, [giant tech corporations](https://www.ft.com/content/0feeafe6-2c01-11e7-9ec8-168383da43b7) and [citizens](https://www.wsj.com/articles/most-students-dont-know-when-news-is-fake-stanford-study-finds-1479752576) already struggle to discern fact from fiction. And as this technology is democratised it will be even more prevalent.

Preempting this we prototyped a device worn on the ear and connected to a neural net trained on real and synthetic voices called Anti AI AI. The device notifies the wearer when a synthetic voice is detected and cools the skin using a [thermoelectric plate](https://en.wikipedia.org/wiki/Thermoelectric_cooling) to alert the wearer the voice they are hearing was synthesised: by a cold, lifeless machine.

<!-- ![](/assets/article_images/overlaid.png)  -->

<figure class="medium">
<img src="/assets/article_images/overlaid.png" alt="">
</figure>

# A Powerful IoT Device

To make this work we developed a custom circuit board using the tiny [Simblee](https://www.simblee.com/) BLE Arduino chip, and custom iOS app that streams audio to a [Tensorflow](https://www.tensorflow.org/) application running a neural net trained on synthetic voices.

<!-- ![Our PCB is being manufactured https://circuits.io/circuits/4984689-wearable-synthetic-voice-sensor-with-thermal-feedback](/assets/article_images/boards.png)
 -->
<figure class="medium">
<img src="/assets/article_images/greenboard.png"/>
</figure>

<figure class="medium">
<img src="/assets/article_images/boards.png">
<figcaption>Our PCB being <a href="https://circuits.io/circuits/4984689-wearable-synthetic-voice-sensor-with-thermal-feedback">manufactured</a> </figcaption>
</figure>


# Thermal Feedback

We wanted the device to give the wearer a unique sensation that matched what they were experiencing when a synthetic voice is detected. Common feedback mechanisms use light, sound or vibration to alert users. By using a 4x4mm [thermoelectric Peltier plate](https://en.wikipedia.org/wiki/Thermoelectric_cooling) we were able to create a noticeable chill on the skin near the back of the neck without drawing too much current.

<!-- ![Anti AI AI cooling element – Peltier Module 3.96mm x 3.96mm x 2.40mm](/assets/article_images/peltier.jpeg "Anti AI AI cooling element – Peltier Module 3.96mm x 3.96mm x 2.40mm")
 -->

<figure class="medium">
<img src="/assets/article_images/peltier.jpeg"/>
<figcaption>Anti AI AI cooling element – Peltier Module 3.96mm x 3.96mm x 2.40mm</figcaption>
</figure>
<p/>
<figure class="medium">
<iframe src="https://player.vimeo.com/video/218113767?color=f58220&title=0&byline=0&portrait=0" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen alt="Anti AI AI &ndash; Wearable Artificial Intelligence"></iframe><figcaption>Anti AI AI &ndash; Wearable Artificial Intelligence</figcaption>
</figure>

# Architecture

To tie the hardware together we developed several independent components. Our neural network formed the backbone of the system, remotely classifying audio data being streamed in via a phone (more about the network below). All training was done in an offline step prior to running our classifier. One improvement would be to continually improve the network based on new input it receives ‘in the wild’, but that was a little beyond our five day timeframe. The iPhone app provided the glue between our IOT wearable and the neural network. This ended up being a rather simple app, doing as little processing as possible as ultimately we can see a future state of this project where the device stands alone. The architecture of the whole system is shown below.

<!-- ![](/assets/article_images/arch.png) -->

<figure class="full">
<img src="/assets/article_images/arch.png">
</figure>

<!-- <img src="/assets/article_images/arch.png" width="100%"> -->

# Keras and Tensorflow

Building neural networks has never been more accessible. Keras is a python library that sits on top of Tensorflow and allowed us to build a neural network at a very high level. Rather than just getting something working, we are able to design our network and bring it to life rapidly. Keras essentially does all the work of generating a Tensorflow network, that we can then use to train and subsequently evaluate data. When it comes to actually training the network, Tensorflow still requires decent dedicated hardware to train in any reasonable time frame, and despite having done it several times now, the setup process to get a network training on the GPU remains a challenge.

Cloud infrastructure platforms such as Cloud ML seem promising when it comes to deploying a pre-trained model, but during development having a dedicated machine with a powerful GPU is almost essential. In developing our approach we experimented with several network layouts, including a recurrent network which was in theory, similar to Deepmind’s Wavenet. The neural network we had most success with though was a fairly simple network comprised of multiple 1D convolutional layers. All the code can be found in our [github](https://github.com/dt-rnd) repository

# Next Steps

This project is a work in progress. In 5 days we created a functional prototype of our wearable AI. An end-to-end powerful Tensorflow neural net connected to a custom wearable BLE device. When the circuit boards arrive from the manufacturer we’ll bring it all together as a wearable device and continue to improve our neural net with more synthetic content as it is released.

# Project Context

As AI starts to robustly understand and synthesise all manner of things, from [human speech](https://deepmind.com/blog/wavenet-generative-model-raw-audio/) to the [creative style](http://genekogan.com/works/style-transfer/) of famous painters, we’re entering an era where anything that can be digitised can be mimicked by AI.

<!-- ![Experiments with style transfer — Gene Kogan](/assets/article_images/mona.jpeg) -->

<figure class="small">
<img src="/assets/article_images/mona.jpeg">
<figcaption>Experiments with style transfer — Gene Kogan</figcaption>
</figure>

We see the ability to mimic anyone’s voice to say anything as a closing of the loop — if it looks real and sounds real, maybe it is real.

<figure class="small">
<iframe width="100%" height="166" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/318658101&amp;color=ff5500&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false"></iframe>
</figure>   

<figure class="small">
<iframe width="1490" height="838" src="https://www.youtube.com/embed/ohmajJTcpNk?ecver=1" frameborder="0" allowfullscreen></iframe>
<figcaption>Face2Face in action</figcaption>
</figure>


# Why is this relevant?

The irony is, the more technology improves the more adversarial it seems to become. Asking us fundamentally difficult questions. A great example being how to design software that chooses the best person/people to kill in a self driving car accident.

<figure class="small">
<img src="/assets/article_images/moralmachine.png">
<figcaption><a href="http://moralmachine.mit.edu/">http://moralmachine.mit.edu/</a></figcaption>
</figure>

<!-- ![http://moralmachine.mit.edu/](/assets/article_images/moralmachine.png)  -->



> “The future holds countless more difficult questions posed by technological advances and we won’t be able to answer them all with more technology.”


