# My First Machine Learning Project 
As the title of this page might suggest, I spend the last semester learning about machine learning in an elective module called "Creating Rich User Experiences with Applied Machine Learning". Prior to this class, I haven’t done anything with ML other than watching a couple of videos on YouTube out of curiosity.

## What I Learned in Class
The class began with a small introduction to the history of deep learning. Shortly after, talked about the thought process one should have to frame the problem in a meaningful way. We demystified common ML terms and started working on a couple of examples to turn the theoretical knowledge into memorable and understandable exercises. We also covered overfitting, how to prevent it, and how to improve ML models in general.
The most important take away for me was a general understanding of what all the “knobs” do and how I can tweak a model to improve its results. I think it’s a solid basis, especially for someone totally new to the topic like myself, to continue working on other ML projects in the future.

## Machine Learning Steps

![Four ML Steps](https://notadvisable.github.io/audio_style_transfer/assets/img/fourStagesOfML.png)

### Framing the Problem
The problem I spend time on working was audio style transfer. Like normal image style transfer, audio style transfer takes two files, a content and a style, and tries to adjust the content file in a way that it fits the style.  
Style transfer is an optimisation problem. The model keeps track of content loss and style loss. It then strives to preserve as much of the content as possible while also trying to preserve as much of the style as possible.
My project was more of experimental nature, but I still wanted my ML model to be able to successfully transfer the style of one file to another in a way that both content and style are audibly present in the output file.

### Preparing the Data
Data preparation was quite easy. All I needed for my model were sets of two clips of audio. After some tests I decided to use short, 4 to 10-second-long wav files. Anything longer would’ve just dragged out the optimisation process and most likely clogged up the RAM even faster.

### Training the ML Model
The model I used was a shallow convolutional neural network, that independently computed features of both content and style. It then created a loss function and ran a ![BFGS](https://en.wikipedia.org/wiki/Broyden%E2%80%93Fletcher%E2%80%93Goldfarb%E2%80%93Shanno_algorithm) optimiser to reduce content and style loss.

### Predicting Using the ML Model
My model didn’t predict anything. Instead I’d replace this step with using the model to transfer style on a specific pair of files.

## What I Did
To gain a deeper understanding of the general concepts of style transfer, I also worked on image style transfer a bit. Here’s one of the images I created in the process.

![Lisbon's Starry Night - Image Style Transfer](https://notadvisable.github.io/audio_style_transfer/assets/img/imageStyleTransfer.png)
 
My project deals with translating this approach of style transfer from images to audio. However, since this was technically my first ML project, I used [this seedbank seed](https://research.google.com/seedbank/seed/audio_style_transfer) by Parag K. Mital as a basis. The author of the seed shows a novel approach that expands on [the work](https://dmitryulyanov.github.io/audio-texture-synthesis-and-style-transfer/) of Dmitry Ulyanov and Vadim Lebedev and is able to generate results that are a lot less noisy.

The source code of the seed project was mostly hosted on GitHub. So, I started on the audio transfer by doing what I always do when I don’t get hard-to-read code: refactoring! I threw out all the things I didn’t need, changed formatting and naming to make everything more readable, and, since the seedbank project was already over two years old when I started, replaced deprecated method calls.

I started my own colab notebook and GitHub repository and started setting up the project. I improved on the spectrogram visualisation by adding more functionalities like optional labels.
Next, I prepared some audio files for the transfer. I first tried doing style transfer on two pop songs. Eminem’s Rap God and Katy Perry’s Teenage Dream. I intentionally went for opposites to see how far I can push the model. As I expected however, these two songs didn’t mix well. There was just too much going on in both. Additionally, in this example, I used a high alpha value that adds additional weight to the content.
Here’s the result:
Content:
Style:
Result:

I realised that the style specifically needs to be of a simpler form to lead to clearer results. Instead of pop music, I opted for classic music for my prototype. I picked a Mozart song solely containing classical instruments. I used that sample as style, and a sample of a woman talking as the content. to prevent the content from poking through, I set the alpha to 0.001 and added another layer to the shallow neural network. I tried using another optimiser, but the Adam optimiser simply lead to a lot more noise and destroyed the structure of the clips, so I stuck with the BFGS optimiser instead.
Here’s the result of this trial:
Content: <audio controls>
  <source src="https://notadvisable.github.io/audio_style_transfer/assets/female_talking.wav" type="audio/wav">
</audio> 
Style: <audio controls>
  <source src="https://notadvisable.github.io/audio_style_transfer/assets/mozart.wav" type="audio/wav">
</audio> 
Result: <audio controls>
  <source src="https://notadvisable.github.io/audio_style_transfer/assets/talkingMozart2.mp3" type="audio/mp3">
</audio> 

As expected, this trial led to a much more promising result. You can hear the Mozart piece matching the speech pattern of the woman. 

### Closing Words
I tried around a lot with additional sets of content and style and tweaking everything until the result was making sense was quite the enjoyable experience. I occasionally ran into the problem of running out of RAM which forced me to restart the entire process, though.
[Pic of ram]
In any case, I can recommend playing around with the colab notebook in this repository yourself!





