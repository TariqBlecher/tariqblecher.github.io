
### The problem

The removal of noise from noisy speech is a fundamental challenge for Audio Deep Learning. For many applications, such as hearing aids, this algorithm should be able to operate in near real time, however, for this demo I will not focus on this constraint. 

This was my first time working with speech data, and I was curious about how much data I needed to train the model and also if the model would be able to generalise to speech which sounded a bit different (e.g.a  different language / accent - there are so many ways to vary speech.)

### The approach 

For my training data, I mixed clean speech data from the RAVDESS dataset with noise data from the UrbanSound8K dataset. The RAVDESS dataset basically consists of short clips of American-accented English with different emotions (happy, sad, angry, etc.) and the UrbanSound8K dataset was noise signals sampled from a city (e.g. car alarms, dogs barking, traffic, etc.) 

For my testing data, I chose the Speech Accent Archive which consists of 150+ different english accents and I mixed with this a Hospital Ambient Noise dataset which is made up of sound recordings in medical settings (e.g. someone wheeling in a trolley, baby crying).


### Reading in the data 

I had decided to use Tensorflow but Tensorflow was unable to read the raw wav files due to a formatting issue, so I rewrote the original datasets locally and uploaded them back onto Kaggle. I also downsampled the datasets back to 8K - this captures most of the Speech signal.

This is quite a limited dataset for speech enhancement. My goal for this project was primarily to check how well this algorithm generally to a completely different unseen dataset.

### Algorithm 

This algorithm takes a Short Time Fourier Transform (STFT) of the audio files to return the transformed signal as a 2D array of dimensions time and frequency. The transformed signal is complex, but the algorithm only operates on the amplitude. The amplitude is passed through a softmask + UNet algorithm. This is a re-worked version from https://github.com/karolzak/keras-unet where I added the softmask component.

### Loss Function

I started with an MAE loss between the clean speech Fourier amplitude and the reconstructed speech Fourier amplitude. However, this had the problem that it penalised retaining noise as much as losing speech. In terms of understanding speech, it is much more important to keep speech than to reduce noise, so I created a custom loss function which features both a MAE term and another term which focuses specifically on retaining speech. Essentially this new term can be seen as the same MAE with an additional masking of both quantities with the true speech amplitude. 

```
def signal_enhancement_loss(y_true, y_pred):
    mae = tf.abs(y_true - y_pred)
    speech_loss =  2 * tf.abs(y_true ** 2 - y_pred * y_true)
    return tf.reduce_mean(mae, axis=-1) + tf.reduce_mean(speech_loss, axis=-1)
```

### METRIC

The PESQ metric is used in the industry as an automatic way to measure speech quality. It is not without it's problems but it still works as a first pass. I would advise you to listen to the output files (clean, corrupted and corrected) to get a better sense of how the algorithm performs.


### Results

Unseen data test In the Notebook below I test the model on a completely different dataset featuring 150+ different english accents mixed with hospital noise. https://www.kaggle.com/tariqblecher/speech-enhancement-unseen-data-test

Results On the validation data, we saw an average increase of +0.44 in the PESQ score (from 2.08 to 2.52) In the unseen test data, we saw an average increase of +0.17 in the PESQ score (from 2.13 to 2.30)

### The Code

If you want to see the code, here's the [Github Link][github-link].



[github-link]: https://github.com/TariqBlecher/speech_enhancement
