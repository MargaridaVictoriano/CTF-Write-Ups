**Plaid CTF 2019**

https://ctftime.org/event/743

**Space Saver (*misc 100p*) **

We were given a .dd file so the first thing I tried to do was to mount the disk image using the following command :

> sudo mount -o loop space_saver-90a5a93dfdda2d0333f573eb3fac9789.dd /mnt/tmp

After mounting the disk image, the only thing that I could found the following image:

 ![alt tag](https://github.com/MargaridaVictoriano/CTF-Write-Ups/blob/master/flag.png)

In spite of being called flag.png, it did not contain the flag so I had to keep looking.
I decided to use binwalk to extract all components of the file.

> binwalk --dd='.*' flag.png

I did not found anything particularly useful so I tried taking another look at the .dd file.
I used testdisk and I found 
