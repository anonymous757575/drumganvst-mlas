<div align="center">
  <center><h1>DrumGAN VST: A Plugin for Drum Sound Analysis/Synthesis with Autoencoding Generative Adversarial Networks</h1></center>
</div>

<br/>
<div align="center">
<b>Supplementary material</b>
</div>

This repository contains supplementary material with regard to our paper "[DrumGAN VST](paper.pdf)", submitted to the Machine Learning for Audio Synthesis (MLAS) workshop at ICML 2022.

## Overview
In this work, we present DrumGAN VST, a simple and intuitive plugin for drum sound synthesis employing Generative Adversarial Networks (GANs) and inspired by previous work [1]. DrumGAN VST can synthesize:
1) 44.1 kHz sample-rate audio operability
2) Continuous instrument control
3) Encoding-decoding of sounds to generate variations
4) Development of a VST prototype
5) Integration into commercial software plugin from a top audio-tech company.


<br>
This website contains supplementary material to the following sections

  * [Increasing the sampling rate to 44,1 kHz](#increasing-the-sampling-rate-to-441-khz)
  * [From perceptual features to soft class labels](#from-perceptual-features-to-soft-class-labels)
  * [Adding an encoder](#adding-an-encoder)


## Increasing the sampling rate to 44,1 kHz
Some blabla

## From perceptual features to soft class labels
Some more blabla

<div align="center" style="font-size:75%;">
<img src="images/DRUMGAN2.png" width=700px><br>
Diagram of DrumGAN training procedure. Rather than using the true label as conditioning information for the Generator, we use the vector of class probabilities output by a pretrained classifier. This allows continuous control on the generated class after training, which enables creating hybrid sounds.
</div>

<br><br><br><br><br>

<table>
<caption><b>Hybrid Generation </b></caption>
  <tr>
    <td></td>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 1 </b></td>
    <td style="text-align: center; vertical-align: middle;"><b>Snare = 1</b></td>
    <td style="text-align: center; vertical-align: middle;"><b>Cymbal =</b></td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 0.2 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 0.2 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://www.computerhope.com/jargon/m/example.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
  </tr>
  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 0.2 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
        <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
  </tr>
</table>


## Adding an encoder
Once the generator network is trained, it is fixed and we use it to generate a dataset$
<table>
<caption><b>Encoding results</b></caption>
  <tr>
    <td></td>
    <td style="text-align: center; vertical-align: middle;"><b>DrumGAN</b></td>
    <td style="text-align: center; vertical-align: middle;"><b>Style-DrumSynth</b></td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 0.2 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
  </tr>

  <tr>
    <td style="text-align: center; vertical-align: middle;"><b>Kick = 0.2 </b></td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
    <td style="text-align: center; vertical-align: middle;">
      <audio controls>
      <source src="https://github.com/anonymous757575/drumganvst-mlas/blob/gh-pages/audios/random_enc_dec.mp3">
      </audio>
    </td>
  </tr>

</table>


## References

[1] Nistal, J., Lattner, S., and Richard, G. DrumGAN: Synthesis of Drum Sounds With Timbral Feature Conditioning Using Generative Adversarial Networks. In Proc. of the 21st International Society for Music Information Retrieval, ISMIR, Montréal, Canada, 2020.
