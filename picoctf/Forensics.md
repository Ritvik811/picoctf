# Trivial Flag transfer Protocol

**Flag:** ``

- step 1
  When installing the file I noticed the file size is actually large implying it contained a lot of data. Our first clue comes in the file name being tftp(trivial file transfer protocol), so I use Wireshark and open the file and export it to a tftp file. Here we noitce there are multiple files ```instructions.txt, plan, program.deb, picture1.bmp, picture2.bmp, and picture3.bmp```.
  
  ![Screenshot 2024-11-09 000434](https://github.com/user-attachments/assets/cee8881d-f4a0-40ed-b6f6-1edca4d43ba7)

- step 2
Here I first access the instructions.txt file. The file contained ```GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA```. This looks like some kind of cypher has been used so in order to figure that out I looked up a cypher identifier online.

![image](https://github.com/user-attachments/assets/01993eeb-6966-49a5-8f46-bf2fa75ac584)

-step 3
Here we find that the cypher used is a ceaser cypher. Heading over to ```dcode.fr``` we get the following output. ```TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN```.
Making it more legible I find out it says ***TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN*** Based on the hint here I opened the file plan Which was also encoded. ```VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF``` Analysing the text once again I learn that it is a ceaser cypher. After decoding the message was ```I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE. CHECK OUT THE PHOTOS```.

-step 4
There are 3 pictures and there should be hidden data among them.Since They mentioned the use of the program file I looked at the file and the file is a debian package or a ```.deb``` file. I used ```sudo dpkg -i programs.deb``` to unpack the file but it popped up with an error. Looks like the program was trying to install steghide. steghide is a stenagrophy tool used to hide data. I think this implies that the pictures have hidden data which I can retrive using steghide. I quickly looked up how to install steghide and installed all the necessary dependencies required. To know more on how to use the tool I used ```steghide --help``` to get more information on how I can use the command.

![image](https://github.com/user-attachments/assets/a22b7777-dfa7-4f28-86b5-1df9614e7c89)

-step 5
I used ```steghide extract -sf picture3.bmp -p DUEDILIGENCE``` The word DUEDILIGENCE the is the passpharse used to encrpt the file. The word seemed out of place in the hint so it was easy to figure out that it was the passphrase. after tryint the command with pictures2.bmp and pictures1.bmp I didn't get the flag but got it in pictures3.bmp. Then I catted out the flag and the challenege was done.

![image](https://github.com/user-attachments/assets/fa4a0f80-06c1-422f-b013-df1f02d670c6)


What I learned through solving this challenge:
1.Learnt what stenography is and how to use stehide 
2. Found out about tftp and how to intercept them. Learnt how to install and use wireshark.
3. leant how to fix broken packages


Other incorrect methods I tried:

- a Difficulty in figuring out the cypher
- b Didn't know how to approach the given file initially because i've never came across a .pcapng file 

References

- https://www.geeksforgeeks.org/how-to-install-steghide-tool-in-linux/
- https://wiki.wireshark.org/TFTP#:~:text=Trivial%20File%20Transfer%20Protocol%20(TFTP,and%20therefore%20easier%20to%20implement.
- https://www.comptia.org/content/articles/what-is-wireshark-and-how-to-use-it
