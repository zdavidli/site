---
layout: post
title: Variational Autoencoders for Surgical Tool Detection
author: David
categories: research
tags: vae
---

# Introduction

In this series of posts, I'll be going over the motivations for my master's research work.
My research work is at the intersection of computer vision and surgical methods. In most medical applications,
there's a significant lack of labeled data, so we're trying to combat this by labeling endoscopic video frames
into two coarse labels -- those with surgical tool presence and those without.

The way we decided to do this was to use a variational autoencoder to learn a latent representation of
endoscopic video. You can find the video dataset [here](https://www.youtube.com/watch?v=6niL7Poc_qQ).

In the rest of this post, I'll introduce the concept of a variational autoencoder and the advantages of using
this model to learn a representation.

# What is a Variational Autoencoder?

There are many other blog posts that describe variational autoencoders in great detail and probably explain it better than I will:

* <https://jaan.io/what-is-variational-autoencoder-vae-tutorial/>
* <https://lilianweng.github.io/lil-log/2018/08/12/from-autoencoder-to-beta-vae.html>
* <https://wiseodd.github.io/techblog/2016/12/10/variational-autoencoder/>

The idea behind using a VAE is to learn latent variables that, when combined, can generate examples.
For instance, if we are learning representations for human faces, two latent variables might be
gender and glasses. For instance, the latent vector `[1,1]` might represent a female face with glasses.
Each component of this vector roughly corresponds to a slider, so if we adjust the first component toward -1,
we get a more male face, and adjusting the second component towards -1 gives us a face without glasses.

In our domain, we would like to model parts of tool motion by these latent variables.

# Why use one?



