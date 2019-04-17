---
layout: post
title: Using variations of VAEs
author: David
categories: research
tags: vae
---

# Drawbacks of traditional VAE
A couple weeks ago, I went to a [computer vision workshop](https://ccvl.jhu.edu/news/2019/jhu-computer-vision-workshop/) and discussed
my research with other students at JHU. There, I got the idea to try some other forms of VAEs to promote "disentangled representations."
On a high level, this means learning a latent space where each latent dimension controls some different aspect of the resulting image.

Furthermore, I learned that VAEs suffer from so-called "posterior collapse"[^1]. It seems that there's a lot written about this, but I completely missed it when I was starting this project off.
The idea behind this is that if the decoder is sufficiently powerful, then it doesn't matter what sort of latent representation we learn.
This is really bad for our application, since the whole point is to use the VAE to learn a useful, compressed representation.

After the conference, I had a couple new directions -- I put my latent space manipulation experiments on hold.
The first task was to make sure I wasn't suffering from posterior collapse, and the second task was to try variations of VAEs that
enforce disentangled representations.

# Posterior Collapse
TODO

# Variants of VAEs

## `$\beta$`-VAE
I first learned of `$\beta$`-VAE through [Lilian Weng's blog post.](https://lilianweng.github.io/lil-log/2018/08/12/from-autoencoder-to-beta-vae.html)
The paper can be found [here](https://openreview.net/pdf?id=Sy2fzU9gl)

## MMD-VAE
https://ermongroup.github.io/blog/a-tutorial-on-mmd-variational-autoencoders/


[^1]: Slide 5 of http://www.people.fas.harvard.edu/~yoonkim/data/sa-vae-slides.pdf
