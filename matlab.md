**Abstract**

 

This study is about the explanation of the working principles of shelving filter, IIR delay, flanger, and chorus, and the resulting effect they have on my music tracks. 

 

 

**Method and Results**

The track of percussions, bass, violin, and brass are applied with digital filters, which I build in Matlab. The idea is to use shelving filters to enhance the specific frequency range of different tracks, to make the timbre rich, such as increasing the frequency response of specific high frequencies to make the brass and violin brighter. And increasing low-frequency performance for the bass and kick.

 

The implementation of a shelving filter by Matlab is setting the center frequency of the filter and the gain of the amplitude. By using the mathematical method given by Valimaki and Reiss, a first-order shelving filter could be represented as the transfer function of the input signal and output signal.

 

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image002.gif)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image004.gif)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image006.gif)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image008.gif)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image010.gif)

Amplitude response of low shelving filter, take inverse of ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image012.gif) to make it a high shelving filter.

Where ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image014.gif) is the center angular frequency, and ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image012.gif) is the gain factor. ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image016.gif) are the coefficients of the shelving filters.

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image018.jpg)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image020.gif)

 

 

 

Since the timbre of a single instrument has more than one harmonic peak, multiple shelving filters should be applied to a single musical instrument. By adjusting the center frequencies of each peak and notch, and the gain factor for enhancing the amplitude, a simple equalizer is built by cascading those shelving filters together.

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image022.jpg)

An example of 2nd order shelving filter

 

Meanwhile, in order to enrich the timbre further, one extra resonator is implemented by building shelving filters. This is because human auditory has a different sensitivity to different frequencies. This means that the loudness of a sound with a specific sound pressure level differs on different frequencies. The most sensitive frequency of the human hearing system is around 3KHz. Therefore, I boosted 3KHz a little to make the instrument as beautiful as possible.

 

**IIR delay**

The digital delay could be implemented with IIR (infinite impulse response) filter by setting the feedback delay line with a gain that is less than 1. Meanwhile, setting the number of delay samples m to an adequate constant makes the virtual reflections audible.![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image024.jpg)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image026.gif)

The reverberation in the feedback system sounds better than the feedforward system, but it would be annoying if the M is not big enough because when the delay factor is small, the filter becomes a comb filter and boosts hugely in specific high frequencies. Also, when the gain factor G is closer to 1, the more echoic (the echo generates faster) it sounds, and vice versa. If the G is more than 1, the disaster will happen to human hearing, as it becomes an unstable IIR.![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image028.jpg)

 

**Flanger**

One of the easiest ways of building a digital flanger plugin is to use two forward delay paths. One of them is with a fixed delay length, and the other delay length is modulated with LFO (low-frequency oscillator). The LFO controls how wobbling the flanger effect is. This technique is also used for vocal vibrato modeling.

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image030.jpg)

To make the effect better, the delay length ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image032.gif) should better be half of the maximal value of the modulated delay length ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image034.gif).

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image036.gif)

As to the simple definition of the feedforward flanger's structure, manually implement LFO with a sinusoid, and also, the static path is added. It sounds nice, like the '60s The Doors and Jimi Hendrix's timbre, in which you can hear a slow pitch shifting.

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image038.jpg)

 

From the chart, we can see that when gain factor b0 of the modulation path reaches 1, the flanger effect would be the most obvious.

**Chorus**

The chorus plug-in basically refers to the same source with random start points and gain factors. These make the output sounds like an actual chorus but not simply multiplied like FIR or IIR delay.

 

The digital guitar chorus plug-in can be modeled as multiple feedforward paths with modulated delay lines. The modulation waveforms may be sinewaves or lowpass-filtered noise. ![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image040.jpg) 

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image042.gif)

![img](file:///C:/Users/HP/AppData/Local/Temp/msohtmlclip1/01/clip_image044.jpg)

**Conclusion**

Shelving filters can be used together as an Equalizer so that we can filter out the sounds we want. IIR delay can be used to achieve the effect of sound repeating while distancing, which I usually use it with vocals. Flanger and chorus can be used to achieve wider variation of dynamics.

 