<div align="center">
  <center><h1>DrumGAN VST: A Plugin for Drum Sound Analysis/Synthesis with Autoencoding GANs</h1></center>
</div>

<div align="center">
<b>Supplementary material</b>
</div>

<br/>
This repository contains supplementary material with regard to our paper "[DrumGAN VST](paper.pdf)", submitted to the Machine Learning for Audio Synthesis (MLAS) workshop at ICML 2022.

## Overview
DrumGAN VST is a simple and intuitive plugin for drum sound synthesis employing Generative Adversarial Networks (GANs) and inspired by previous work [1]. DrumGAN VST offers the following key features:
1. 44.1 kHz sample-rate audio operability
2. Continuous instrument control over kick, snare, and cymbals: choose the amount of "kickness", "snareness", and "cymbalness" you want to confere to the synthesized sound. This control can also be used to create hymbrid sounds that morph characteristics from each instrument class, or to explore weird sounds by setting these parameters to unrealistic combinations (e.g., all to zero).
3. Analysis/resynthesis AKA encoding/decoding: DrumGAN VST features an encoding neural network that can be used to analysize/encode some pre-existing sound and decode/resynthesize variations of it. 
4. DrumGAN VST will be shortly available as an integrated feature in a commercial VST plugin.

In what follows, we showcase the aforementioned capabilities of DrumGAN VST by providing some audio and musical examples. We also show a demo of the latest prototype (to preserve anonymity, a demo of the final commercial software will be published upon acceptance of the paper).

<div align="center" style="font-size:75%;">
<video width="320" height="240" controls>
  <source src="https://anonymous757575.github.io/drumganvst-mlas/videos/drumGAN.mp4" type="video/mp4">
</video>
</div>

<!-- <div align="center" style="font-size:75%;">
<img src="images/DRUMGAN2.png" width=700px><br>
Diagram of DrumGAN training procedure. Rather than using the true label as conditioning information for the Generator, we use the vector of class probabilities output by a pretrained classifier. This allows continuous control on the generated class after training, which enables creating hybrid sounds.
</div>
 -->
<br><br><br><br><br>


<!-- <br>
This website contains supplementary material to the following sections

  * [Increasing the sampling rate to 44,1 kHz](#increasing-the-sampling-rate-to-441-khz)
  * [From perceptual features to soft class labels](#from-perceptual-features-to-soft-class-labels)
  * [Adding an encoder](#adding-an-encoder)
 -->

## Baseline Comparisons
We compare DrumGAN VST generations with real samples and two other neural drum synthesizers as baselines: one is CRASH, based on diffusion models, and the other is Style-DrumSynth, based on StyleGAN. While the baselines are state-of-the-art, they have high bias and fail to capture the diversity and quality of timbres compared to real data, while DrumGAN produces high quality samples similar to the real data. Samples were randomly selected to fairly reflect the diversity and quality of samples from each model. Quantitative comparisons can be found in the paper.

<table style="width:50%">
<caption><b>random generations</b></caption>
  <tr>
    <td style="width: 16%; text-align: center; vertical-align: middle;"><b>Real Data</b></td>
    <td style="width: 16%; text-align: center; vertical-align: middle;"><b>DrumGAN</b></td>
    <td style="width: 16%; text-align: center; vertical-align: middle;"><b>CRASH</b></td>
    <td style="width: 16%; text-align: center; vertical-align: middle;"><b>Style-DrumSynth</b></td>
  </tr>

  <tr>
<!--     <td style="text-align: center; vertical-align: middle;"><b>Kicks </b></td> -->
    <td style="width: 16%; text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen true.wav">
      </audio>
    </td>
    <td style="width: 16%; text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen drumgan.wav">
      </audio>
    </td>
    <td style="width: 16%; text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen CRASH.wav">
      </audio>
    </td>
    <td style="width: 16%; text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen dsd.wav">
      </audio>
    </td>
  </tr>

<!--   <tr>
    <td style="text-align: center; vertical-align: middle;"><b> Cymbals </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_cymbal.wav">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b> Snares </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_snare.wav">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="">
      </audio>
    </td>
  </tr> -->
</table>




## Instrument Control & Interpolations
We show interpolations for DrumGAN VST. Inital and target timbres are chosen from generated samples. DrumGAN VST is explicitly conditioned on a global class probability latent vector, therefore, interpolations sound like reasonable instruments across all classes.

<table>
<caption><b>Class Interpolations</b></caption>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Cymbals to Kicks </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/int_01.wav">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b> Kicks to Snares </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/int_12.wav">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b> Cymbals to Snares </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/int_02.wav">
      </audio>
    </td>
  </tr>
</table>


<table>
<caption><b>Progressive mixing </b></caption>
  <tr>
    <td></td>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 1 </b></td>
    <td style="text-align: center; vertical-align: middle;"><b>Snare = 1</b></td>
    <td style="text-align: center; vertical-align: middle;"><b>Cymbal = 1</b></td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Kick from 0 to 0.5 </b></td>
    <td style="text-align: center; vertical-align: middle;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen dsd.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen crash.mp3.mp3">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Snare from 0 to 0.5 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen.mp3">
      </audio>
    </td>
  </tr>
  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Cymbal from 0 to 0.5 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/random_gen.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
    </td>
  </tr>
</table>


## Analysis/Synthesis of prexisting sounds
We compare encoded and reconstructed pairs of audio examples for DrumGAN VST and Style-DrumSynth, which also incorporates an encoder analogous to ours. Encoded sounds are chosen from both the models' pre-generated samples, as well as from different real drum datasets. We can hear that DrumGAN VST's synthesized examples are generally perceived closer in terms of timbre to the original encoded sample.

<table>
<caption><b>Encoding results</b></caption>
  <tr>
    <td></td>
    <td style="text-align: center; vertical-align: middle;"><b>DrumGAN</b></td>
    <td style="text-align: center; vertical-align: middle;"><b>Style-DrumSynth</b></td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Unseen Kicks </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/enc_dec_kicks.wav">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Unseen Cymbals </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/enc_dec_cymbals.wav">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Unseen Snares </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/enc_dec_snares.wav">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="">
      </audio>
    </td>
  </tr>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Unseen Other </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/enc_dec_other.wav">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="">
      </audio>
    </td>
  </tr>

</table>

## Other Examples
<table>
<caption><b>Converting Beat-box to Drums</b></caption>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Original</b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/beatboxGANitscalledmusicOrig.mp3">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Resynthesized</b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://anonymous757575.github.io/drumganvst-mlas/audios/beatboxGANitscalledmusic.mp3">
      </audio>
    </td>
  </tr>
</table>


## References

[1] Nistal, J., Lattner, S., and Richard, G. DrumGAN: Synthesis of Drum Sounds With Timbral Feature Conditioning Using Generative Adversarial Networks. In Proc. of the 21st International Society for Music Information Retrieval, ISMIR, Montréal, Canada, 2020.
