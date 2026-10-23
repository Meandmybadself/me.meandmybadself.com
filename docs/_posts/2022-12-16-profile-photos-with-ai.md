---
layout: post
title:  "Profile Photos with AI"
date:   2022-12-16 12:00:00 -0600
categories: stable-diffusion dreambooth ai
---



# Overview

This will help you create a [Stable Diffusion](https://en.wikipedia.org/wiki/Stable_Diffusion) [Dreambooth](https://github.com/XavierXiao/Dreambooth-Stable-Diffusion) model that will use textual inputs to create imagery of you / whoever you choose to model. The process is unbelievably fun & weird & narcissistic.

| <img src='/assets/stable-diffusion/grid-0003.jpg' width='600' alt='Grid of generated profile photos'/> |
|--|
| `jbdb!! portrait face album art of detailed storybook illustration, cyberpunk art, futuristic product design, neoplasticism, pop surrealism by petros afshar takashi murakami victor ngai behance contest winner featured on pixiv serial art symmetry` |

[Stable Diffusion](https://en.wikipedia.org/wiki/Stable_Diffusion) is a system allowing you to create detailed images based on text descriptions.

[Dreambooth](https://github.com/XavierXiao/Dreambooth-Stable-Diffusion) allows for text-to-image generation with only a few sample images.

# Prior Art
I went down this path using [Mathowie’s blog post](https://a.wholelottanothing.org/2022/11/02/stable-diffusion-and-ai-generated-art-is-absolutely-wild-in-every-way/) + [AItreprenuer’s video](https://www.youtube.com/watch?v=ravETUa84P8&feature=emb_title).

# Steps

  * [Get a free API key from Hugging Face](https://huggingface.co/docs/huggingface_hub/how-to-inference)
    * You’ll need to download the Dreambooth model.
  * [Pay for some Google Colab Compute Units](https://colab.research.google.com/signup)
    * Get $9.99 / pay-as-you-go
  * [Copy this Colab Python Notebook](https://colab.research.google.com/github/TheLastBen/fast-stable-diffusion/blob/main/fast-DreamBooth.ipynb)
  * Pick out 20-30 pictures of the subject. Make sure they’re the only one in the photo & that their face isn’t obstructed. They should also be relatively in-focus.
  * Using [birme.net](), 
    * Crop each photo to 512×512 pixels
    * Save your photos using a name that has never been used anywhere. This is how you’ll refer to yourself textually when describing your photos. I used jbdb_1.jpg, jbdb_2.jpg, etc.
    * Go through the notebook’s steps & train your model. This will take about 45 minutes & will save a ~2gig model into your Google Drive.
    * Once that’s done, you’ll be able to start up the notebook whenever you like & create images.

[I’ve kept a list of the textual prompts that have resulted in interesting outputs here](https://docs.google.com/spreadsheets/d/1JpOyfkGSfIAnFCvaAFARe89sjEipMH77pxsWeY3UEs4/edit#gid=0).

# Alternative
If you have a healthy GPU at home with 8gb or more of RAM, you can download the model you generated on Colab from Google Drive and generate images at home. The benefits to this are:

* You won’t incur startup wait times / bootstrapping when starting Stable Diffusion via Colab.
* You don’t need to keep a 2 gig model in Google Drive
* Stable Diffusion UI has a bunch of extra features you can play with.
* You can quickly swap between generated models.

# Tips

* When you don’t like how an image was rendered, determine what you don’t like about the image (eg “Too anime”), and then use “anime” in the negative prompt.
* GFPGAN is a feature in the desktop version of Stable Diffusion that “corrects faces”. While it does correct faces, it also feels like it takes something away from the* distinguishing features of a face.
* Generate a series of images to get the gist of types of imagery you’ll create.