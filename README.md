# SpecGan
Spectrogram generator using GANs


I started this project as part of my Bachelor Thesis:
"Generator of graphic representations of phonic signals using GAN neural networks"
and develop it for learning purpose. 

## Model
Model is based on https://www.tensorflow.org/tutorials/generative/dcgan. 
List of major changes made after experiments to improve results:

-add noise to discriminator

-normalize input to value from 0 to 1

-changed activation function from tanh to sigmoid

## Datasets 

Mozilla commonvoice - huamn speech with noise: https://commonvoice.mozilla.org/en

Recording of drums: https://www.hexawe.net/mess/200.Drum.Machines/

Speak Like a Dog dataset: https://drive.google.com/drive/folders/1TmG1yjc0_RLUX7U0ZJGLPVWkAwiSkSWY

(WIP) Part of female recording from vctk corpus: https://datashare.ed.ac.uk/handle/10283/3443

## Data preprocessing

Steps taken to prepare tensor containing spectrograms from audio clips: 

1. Trim silnce with threshold equal to 15dB
2. Split audio clips into 2s chunks
3. Create spectrogram/mel-spectrogram using python.librosa (set parameters to get desired size of spectrogram)
4. Save all spectrograms to tf.tensor
5. Normalize values to 0-1 (done in model code)

## Results analysis 

To track loss function tensorboard was added. Althought loss fucntion is less useful in GANs than in other architectures, it helps to identify convergence failure(not finding an equilibrium between the discriminator and the generator - one of them dominates the other)

To analyze quality of generated audio, function converting mel/spectrograms to audio was implemented using librosa. 

## To do 
- Code cleaning/refactor
- Finish training on vctk female dataset




