---
title: "A Downscaled Faster-RCNN Framework for Signal Detection and Time-Frequency Localization in Wideband RF Systems"
collection: publications
status: published
permalink: /publication/frcnn
excerpt: 'We propose a wideband spectrum sensing technique to detect and localize wireless radio frequency (RF) signals of interest in time and frequency when uninteresting signals cause RF interference (RFI). Specifically, we adopt and downscale the existing Faster-RCNN (FRCNN) framework to achieve better signal detection and localization than the state-of-the-art. For experimental evaluation, we present a data generation framework for Wi-Fi as the signals of interest and the Bluetooth and microwave oven signals as the RFI. Experiments reveal that (i) the downscaled FRCNN model can achieve up to a mean average precision (mAP) of 0.8, significantly outperforming the state-of-the-art, (ii) feature extraction with the VGG-13 architecture gives the best mAP with pretrained weights and configured as trainable, (iii) for signal detection in real RF traces, when compared to training purely with synthetic RF data, a better mAP can be achieved by training with a mixture of synthetic and real RF traces or by fine tuning the synthetically-trained weights with an additional round of training on a small amount of real RF traces, and (iv) the mAP performance decreases as the signal to noise ratio (SNR) is lowered.'
date: 2020-04-21
venue: 'IEEE Transactions on Wireless Communications'
paperurl: 'https://ieeexplore.ieee.org/abstract/document/9075413'
citation: 'Prasad, K. S. V., D’souza, K. B., & Bhargava, V. K. (2020). A downscaled faster-RCNN framework for signal detection and time-frequency localization in wideband RF systems. IEEE Transactions on Wireless Communications, 19(7), 4847-4862.'
---


