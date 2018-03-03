# ProgGAN-PyTorch
**Disclaimer:** I give no promises that this implementation actually works the way it's supposed to. In particular I am not sure I correctly implemented weight initializations as done in the original paper, though I have tried my best.

This repo is an implementation of the paper [Progressive Growing of GANs for Improved Quality, Stability and Variation](https://arxiv.org/abs/1710.10196) in PyTorch. ProgGAN.py includes all the actual code of the model, while train.py handles initializing a model, loading training data, saving checkpoints etc. I attempted to stay as faithful to the paper as possible, the only exception being the learning rate. No matter what I tried, I was completely unable to get a model to learn anything with the high learning rate suggested in the paper. I would be very thankful for ideas why that might have been the case and what I could have done differently.

The most important thing I learned was just what huge amounts of compute this technique takes. I was unfortunately not able to train a model close to the resolutions shown in the paper. I also found very strange artifacts (the oddly geometric splotches of extreme color) being created in the images that I don't recall seeing in other kinds of GANs. The only explanation I can think of is that it has something to do with the linear outputs, or it could be a bug in my implementation I haven't been able to spot. Here is the training so far as I got it on celeba:

![celeba](https://github.com/ConnorJL/ProgGAN-PyTorch/blob/master/out2.gif?raw=true)

## How To Use

**Requirements:** PyTorch, Torchvision, Scipy, TensorboardX (for logging), Tensorflow (if you want to use tensorboard to view the logs)

You can either use the ProgGAN class in ProgGAN.py and create your own training script by passing data to the gan.train function, or use the included train.py. The configuration variables are at the top of the script. The script expects your dataset to be in the specified folder, with every size of image in their own subfolder (e.g. "celeba/4", "celeba/8" etc). You can use the create_dataset.py to reformat a folder full of images to the required form.