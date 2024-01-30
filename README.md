# Overview

This repository contains snippets of my work on [Google's Summer 2023 Kaggle Contest on ASL Fingerspelling](https://www.kaggle.com/competitions/asl-fingerspelling). While my best score ultimately
placed me towards the lower end of the pack (827 out of 1315 entrants), I'm nonetheless proud of it because of the unconventional approach I chose to take. While the provided sample code (and most of the 
other submissions that I've seen) have focused on transformer-based models, I chose to take a different approach and use a stack of old-fashioned RNNs, with a CTC loss function.

Unfortunately, it seems that it was the choice of loss function that ultimately held the model back, as the contest was scored using Levenshtein distance, and as I discovered too-late into the 
competition, optimizing CTC loss will only improve Levenshtein distance up to a point, and then hit a wall. Following this discovery, I tried out a few different approaches to computing a new loss
for the training loop, including MWER (minimum word error loss). I think these approaches might have borne fruit if we'd had more time for exploration before drawing out our plans.

I still believe that an RNN-based approach is the right path to take here. I've been following in earnest the (RWKV [("rawkuv")](https://rwkv.org):w project. It promises to deliver transformer-like 
scalability coupled with RNN-like streaming inference. I honestly just don't like the idea of doing text-based inference in chunks. It feels so inelegant.

