---
layout: post
title: CityVibes, Solution for Smart Cities
date: 2017-11-18
permalink: "/blog/:title"
---

## [Hack Western](http://www.uwo.ca/)


4:10 on Friday, I get an email saying there are extra spots on the bus for Hack Western which leaves at 4:30. 
Yup, talk about planning. Nonetheless, As I was riding high on my win from Electric hacks, I was all ready to adventure to Western
without any preparation, extra pair of clothes (Not the best idea in retrospect ...)

Going without a team, I met with a friend on the bus and we got chatting and I finally decided to work with them!

We tried to solve the problem of **Noise Pollution** in urban cities. 

Our idea was to develop a smart device of sorts with a ([GPS Module](https://en.wikipedia.org/wiki/Global_Positioning_System)) and a microphone. This device would eventually 
be hooked on to bikes which go around the city and can capture the noise from around the area and we can then plot this information as a heat map on a web app. In addition to the heat map, we can also classify the sounds using Audio Classification and figure out what's the source of that noise. 

Once again, I was responsible for **dealing with the Audio** 

I wanted to experiment and I decided that I'll train a neural network from scratch. 
The goal was to classify audio on the basis of the ([Urban Sound Dataset](https://serv.cusp.nyu.edu/projects/urbansounddataset/))
I started with the tutorial below. Great Explanation by the way..

([Urban Sound Classification](https://aqibsaeed.github.io/2016-09-03-urban-sound-classification-part-1/))

I was going slow and steady, trying to understand the feature extraction phase. 
The four main features of audio classification used were :
1) ([melspectrogram](https://librosa.github.io/librosa/generated/librosa.feature.melspectrogram.html)): Compute a Mel-scaled power spectrogram
2) ([Mel-frequency-cepstrum(mfcc)](https://en.wikipedia.org/wiki/Mel-frequency_cepstrum)): Mel-frequency cepstral coefficients
3) ([Chroma-feature](https://en.wikipedia.org/wiki/Chroma_feature))/([Chroma-stft](https://librosa.github.io/librosa/generated/librosa.feature.chroma_stft.html)): Compute a chromagram from a waveform or power spectrogram
4) [Special-Contrast](https://librosa.github.io/librosa/generated/librosa.feature.spectral_contrast.html)): Compute spectral contrast, using method defined in ([this paper](http://ieeexplore.ieee.org/document/1035731/))
5) ([Tonnetz](https://librosa.github.io/librosa/generated/librosa.feature.tonnetz.html)): Computes the tonal centroid features (tonnetz), following the method described in ([this paper](https://dl.acm.org/citation.cfm?id=1178727))

I had a lot of errors with the first approach of using a simple neural network. Mainly tensorflow complications. 
So i decided to try the second approach of applying a ([Convolution Neural Network](https://adeshpande3.github.io/adeshpande3.github.io/A-Beginner's-Guide-To-Understanding-Convolutional-Neural-Networks/))

The part 2 of the tutorial is linked ([here](https://aqibsaeed.github.io/2016-09-24-urban-sound-classification-part-2/))

There were some errors regarding modelling of the data and labelling which I solved. All this while I was training the neural network on my personal GPU on the cloud, hosted by ([Paperspace](https://www.paperspace.com/))

The code is up on github ([here](https://github.com/gotibhai/NoisePollutionDetection/tree/backend))

Finally, I trained the network with a 72% accuracy, which was considered pretty accurate in this usecase!

Notes: 
One of the main lessons I learnt was **ALWAYS USE JUPYTER NOTEBOOKS** 
I stupidly wrote scripts and had to run them from scratch again and again in the terminal. 




