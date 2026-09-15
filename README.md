# GR_Implementations_DAFX
This project revolves around implementation of different gain-reduction tools often used in audio applications such as engineering, mixing, mastering... which often introduce significant degradations. 

All gain reduction tools are inspired from their implementation in the DAFX textbook.

## Table of contents

A Step-by-step implementation of different tools
  1. Standard compressor implementation
  2. Limiter implementation
  3. Clipper implementation
  4. Multiband compressor implementation

B Combined implementation

C Comparison of outputs

D Suggestion of correction

E Pipeline all together (user implementation)

F References

## Introduction

"[Compression] allows the increase of the overall loudness of the track. Considering that the casual listener often gives preference to the louder of two musical works, a trend has developed towards always higher average levels. Moderation is, however, necessary because the “loudness war” can induce severe degradations of the audio and musical quality [Kat07, Lun07]." -- DAFX

Here, different GR tools are established and explained step by step, before combining them into a single implementation. Then, analysis of the outputs is carried out, to compare their spectrums against that of the original signal. A difference spectrogram is then generated between original and processed spectrum as well as a time-domain null test (output_signal - x), before using this information to correct the degraded outputs.


## A Step-by-step implementation of each different tool
**photo**

Here, there are 2 paths:

Top: the unaffected input signal goes through a delay line. The delay exists purely so that by the time this path's audio arrives at the multiply, output of the other path is there too.

Bottom: here, the input is used to result in a scalar by which to multiple and reduce the signal.
At the multiplier point, the delayed signal is multiplied with the gainr eduction perceptage found in the bottom path, before this sample value is added to the output array.
