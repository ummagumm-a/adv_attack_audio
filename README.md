# Overview
This project implements two types of attacks to fool an audio classification model.

The architecture of the model is: input audio signal is passed through STFT function and is saved to disk as an image. 
Then, this image is taken by the model to assign it one of 8 classes.

* `get_adv_with_diff_stft.ipynb` - uses adversarial attack. 
Since there is a non-differentiable module inside the network, there is no straightforward way to apply, for example, FGSM attack. 
[1] suggests to substitute the non-differentiable module with a differentiable approximation. I implemented this strategy and my
observations confirm the validity of this method. This method drops model accuracy by 48%.
* `manual_attack.ipynb` - I choose a slice of audio and add random noise and distortion. This method drops model accuracy by 10%.

# References 
1. Athalye, A., Carlini, N. and Wagner, D., 2018, July. Obfuscated gradients give a false sense of security: Circumventing defenses to adversarial examples. In International conference on machine learning (pp. 274-283). PMLR.
