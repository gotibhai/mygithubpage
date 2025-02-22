---
layout: post
title: Stutter.io, Playing with Audio Processing
date: 2017-11-18
permalink: "/blog/:title"
---

Adventures at Electric Hacks ( [Trent University](https://www.trentu.ca/) )

Hackathons are fun, weekend getaway's and I've recently been *sort of* addicted to them. The idea of going to a new place, meeting innovators and other hackers and the idea of actually hacking together a product/service in the spam of 36 hours is very exciting. 

Mostly all hackathons for me start with about 1-2 hours of brainstorming. This hackathon, my teammate came up with the idea of stutter.io!
He envisioned a service which would help people who stutter. The idea was to train them on a speech we gave them and then identify syllables and words they stutter on, these would be then stored against their profile. Now, they can input any speech they want themselves to train on and we would identify words and syllables where there is a high possibility of them stuttering. 

The first check would be to highlight these words for them. People usually stutter because their brain is trying to do two things at the same time, speak and think about what to speak next. Hence, highlighting the word makes their brain conscious that "Hey, you might stutter here, so lets just focus on speaking". We also hooked up a leap motion so that you could just sway your hand in any direction and we would replace that word with a synonym.

My task was to figure out where does a person stutter in a speech. Sounds simple, it's not trust me!

The first finding was the black box API's by [Google](https://cloud.google.com/speech/), [IBM](https://www.ibm.com/watson/services/speech-to-text/), [Twilio](https://www.twilio.com/speech-recognition) were far from accurate. So they were of no help. They were even unable to capture normal speech properly.

I then decided to visualize the audio to see if there was a visible difference where someone stutters. As you can see below in the waveform, the area she stutters has a high and almost similar amplitude and appears as a chunk. I figured if you could search an audio for chunks with these properties, you could find where they were stuttering, however after looking extensively and not finding relevant information, I decided to move on.

This was the audio file I was experimenting with.

{% include myaudio.html %}

![Waveform Depiction of the Audio]({{ "https://raw.githubusercontent.com/gotibhai/pushkinabbott/gh-pages/images/blogs/waveform.png"}})

![Power Spectogram of the Audio]({{ "https://raw.githubusercontent.com/gotibhai/pushkinabbott/gh-pages/images/blogs/power_spectogram.png" }})

![Amplitude of the Audio]({{ "https://raw.githubusercontent.com/gotibhai/pushkinabbott/gh-pages/images/blogs/amp.png" }})


* Talk about the diference between waveform and spectrogram *


Next, I stumbled upon something called time-stamped spech-to-text. The service I stumbled upon was called [Gentle](https://github.com/lowerquality/gentle). It's basically like an API which you call by passing an audio and it's transcript, you can even use the service right on their website.

It will try to align the audio and transcript and return a json with every word it found in the transcript and aligned in the audio with the start and end time. It'll also return the syllables it heard in that audio piece. In addition to all these successfull alignments, It also returns objects which it could not find in the transcript or it couldn't find in the transcript. 

To be continued ...
