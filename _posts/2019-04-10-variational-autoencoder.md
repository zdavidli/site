---
layout: post
title: Variational Autoencoders for Surgical Tool Detection
author: David
categories: research
tags: vae
---

# Introduction

In this series of posts, I'll be going over the motivations and methods for my master's research work[^1].
My research work is at the intersection of computer vision and surgical methods. In most medical applications,
there's a significant lack of labeled data, and we're trying to combat this by labeling endoscopic video frames
into two coarse labels -- those with surgical tool presence and those without. Incidentally we're also trying
to learn representations for tool motion.

# Motivation

I'm a part of the [Computational Interaction and Robotics Laboratory](https://cirl.lcsr.jhu.edu/), directed by Greg Hager.
One of the research directions of CIRL is the so-called "Language of Surgery." 

> The Language of Surgery project is based on the premise that surgical activity, like most human activity, is structured. Data from the surgical field captures this structure. Research in the Language of Surgery project aims to discover structure in surgical activity and develop applications that rely upon this structure. Since 2006, the Language of Surgery project has focused upon methods to develop representations to describe surgical instrument motion and video image data that not only generalize across activities but also are invariant to factors such as surgeons’ skill or style, objective assessment of technical skill, and providing data-driven targeted feedback to support acquisition of technical skill. The Language of Surgery project includes multiple studies with different types of data, which provide a unique opportunity to apply state of the art machine learning techniques to tackle important clinical challenges.

In surgical applications, data is mostly unlabeled since labels are tedious to generate and require the time of highly trained surgeons.
This means that, unless we're working with simulations, we have to do some unsupervised learning to make sense of surgical video.
In my project, I'm trying to focus just on the motion of surgical tools. 


# How are you trying to do this?

The way we decided to do this was to use a **variational autoencoder (VAE)** to learn latent factors of tool motion in
endoscopic video. You can find the video that I'm using as the dataset [here](https://www.youtube.com/watch?v=6niL7Poc_qQ).

## What is a Variational Autoencoder?

There are many other blog posts that describe variational autoencoders in great detail and probably explain it better than I will:

* <https://jaan.io/what-is-variational-autoencoder-vae-tutorial/>
* <https://lilianweng.github.io/lil-log/2018/08/12/from-autoencoder-to-beta-vae.html>
* <https://wiseodd.github.io/techblog/2016/12/10/variational-autoencoder/>

The idea behind using a VAE is to learn latent variables that, when combined, can generate examples.
For instance, if we are learning representations for human faces, two latent variables might be
gender and glasses. For instance, the latent vector `$[1,1]$` might represent a female face with glasses.
Each component of this vector roughly corresponds to a slider, so if we adjust the first component toward `$-1$`,
we get a more male face, and adjusting the second component towards `$-1$` gives us a face without glasses.

In our domain, we would like to model parts of tool motion by these latent variables.

## Why VAEs?

In unsupervised learning, a common strategy is to use a **generative model**, where the model is tasked with generating samples
from a learned probability distribution. This makes intuitive sense; generating good examples from a distribution probably means
you learned the distribution well.

Right now, the two most common generative models are generative adversarial models (GANs) and VAEs. GANs work by taking in noise
and using a generator neural network to make an adversarial example of the data. Then, the adversarial example is compared with a real
example by a discriminator, which tries to tell the fake apart from the real example. 
The result of this is that the generator learns to make examples that the discriminator will classify as real. In GANs,
the distribution of latent samples `$z$` is a "useful" source of randomness from which the generator can sample and turn into
good fakes.

On the other hand, in a VAE, the focus isn't producing something that looks like it came from the data distribution. Instead,
we want to reconstruct the example image we were given as input. Since the latent sample `$z$` in the encoder-decoder model
is a low-dimensional vector, the VAE learns a meaningful compressed representation of the input.

This is exactly what we want to do -- we want to learn a representation for tool motion or tool presence. Optimally we would like
a small number of components of the latent space to encode this, i.e. we want to learn a **disentangled representation**.


[^1] My master's research source code can be found at: <github.com/zdavidli/tool-presence>. In the future, I plan make a post with a summary of my results.
