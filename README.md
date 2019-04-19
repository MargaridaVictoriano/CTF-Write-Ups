**Plaid CTF 2019**

https://ctftime.org/event/743

** Space Saver (*misc 100p*) **

We were given a .dd file so the first thing I tried to do was to mount the disk image using the following command :

> sudo mount -o loop space_saver-90a5a93dfdda2d0333f573eb3fac9789.dd /mnt/tmp

After mounting the disk image, the only thing that I could found the following image:

 ![alt tag](https://github.com/MargaridaVictoriano/CTF-Write-Ups/blob/master/flag.png)

In spite of being called flag.png, it did not contain the flag so I had to keep looking.
I decided to use binwalk to extract all components of the file.

> binwalk --dd='.*' flag.png

I did not found anything particularly useful so I tried taking another look at the .dd file.
I used testdisk and I found this :

![alt tag](https://github.com/MargaridaVictoriano/CTF-Write-Ups/blob/master/testdisk.png)

The three .png files were equal and they all represented the organizer team logo (http://pwning.net/).
I used some steganography tools but I did not discover anything.
There was a space.rar file but it was encoded with a password.
I decided to try to crack the password using *John the Ripper*. While it was running, I decided to take a look at the raw hex of the P/PP/PPP.png file data. On each PNG I found this:

> 00040260: 0000 4945 4e44 ae42 6082 0053 7061 6300  ..IEND.B`..Spac.

> 00044260: 0000 4945 4e44 ae42 6082 0033 6569 3200  ..IEND.B`..3ei2.

> 00048260: 0000 4945 4e44 ae42 6082 0068 6572 4500  ..IEND.B`..herE.

I found curious that there was a string containing *Spac* because it resembles to the name of the challenge. I found the string near the >IEND footer of the PNG so I checked the other PNG's as well.
I merged the strings and I got this *Spac3ei2herE*. I inserted this on the encoded .RAR file and it was the correct password and I got the following image:

Spac3ei2herE
