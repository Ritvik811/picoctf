# m00nwalk 

**Flag:** `flag`

- step 1
  After downloading the file I see that it is a ```.wav``` audio file. Based on the given 2 hints which were
  1. How did pictures from the moon landing get sent back to Earth?
  2. What is the CMU mascot?, that might help select a RX option
 
     The first hint asks us how did the pictures from the moon landing get sent to earth. A quick google search tells us to [SSTV](https://en.wikipedia.org/wiki/Slow-scan_television)

- step 2
So based on the info and help from a tutorial I learn about ```qsstv```. It's a software which converts audio files to images.
After installing qsstv and also pavucontrol. After installing we need to comfigure qsstv.I used the following commands for getting everything done.

``` apt-get install qsstv
pactl load-module module-null-sink sink_name=virtual-cable (configuring a null audio)
pavucontrol (A GUI will pop-up, went to the  "Output Devices" tab to verify that "Null Output gets detected)
qsstv (The program GUI will pop-up, go to "Options" -> "Configuration" -> "Sound" and select the "PulseAudio" Audio Interface) ```

After this we have to get back to the pavucontrol menu to initiate a recording of the audio as qsstv captures the audio from the null output



What you learned through solving this challenge:

1. first concept
2. second concept
3. etc.

Other incorrect methods you tried:

- a
- b
- c

References

- reference 1
- reference 2
- etc.
