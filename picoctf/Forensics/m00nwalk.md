# m00nwalk 

**Flag:** `picoctf{beep_boop_im_in_space}`

- step 1
  After downloading the file I see that it is a ```.wav``` audio file. Based on the given 2 hints which were
  1. How did pictures from the moon landing get sent back to Earth?
  2. What is the CMU mascot?, that might help select a RX option
 
     The first hint asks us how did the pictures from the moon landing get sent to earth. A quick google search tells us to [SSTV](https://en.wikipedia.org/wiki/Slow-scan_television)

- step 2
So based on the info and help from a tutorial I learn about ```qsstv```. It's a software which converts audio files to images.
After installing qsstv and also pavucontrol. After installing we need to comfigure qsstv.I used the following commands for getting everything done.

 apt-get install qsstv
pactl load-module module-null-sink sink_name=virtual-cable (configuring a null audio)
pavucontrol (A GUI will pop-up, went to the  "Output Devices" tab to verify that "Null Output gets detected)
qsstv (The program GUI will pop-up, go to "Options" -> "Configuration" -> "Sound" and select the "PulseAudio" Audio Interface)

![image](https://github.com/user-attachments/assets/af6900ac-b7f8-4ebe-aaa6-ba6502f981b4)

![image](https://github.com/user-attachments/assets/1b4b99ba-402f-4a99-8981-c8aaa2c9062f)

After this we have to get back to the pavucontrol menu to initiate a recording of the audio as qsstv captures the audio from the null output.
Based on the second hint "What is the CMU mascot?" - the answer is "Scotty the Scottie Dog". This hinted that we should select "Scottie 1" as QSSTV's "Mode".

 - step 5
   Now we have to play the audio. Using ```paplay -d virtual-cable message.wav```. The image starts generating and we get the flag

   ![Image](https://github.com/user-attachments/assets/2d9d05ac-7528-43ed-a1b4-bc5e0dc8649f)



What I learned through solving this challenge:

1. What and how to use SSTV
2. Fixing broken packages

Other incorrect methods you tried:

- Tried seeing the audio graph of the file initially which was of no use

References

- [reference 1}(https://en.wikipedia.org/wiki/Slow-scan_television)
- [reference 2](https://ourcodeworld.com/articles/read/956/how-to-convert-decode-a-slow-scan-television-transmissions-sstv-audio-file-to-images-using-qsstv-in-ubuntu-18-04)
