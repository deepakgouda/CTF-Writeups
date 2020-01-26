## Crypto: 
1. HOME RUN </br>
#### Problem description : </br>
Ecbf1HZ_kd8jR5K?[";(7;aJp?[4>J?Slk3<+n'pF]W^,F>._lB/=r
#### Solution : </br>
I observed special characters in the string, so I tried Base85 decode.

Flag : rtcp{uH_JAk3_w3REn't_y0u_4t_Th3_uWust0r4g3}

## Forensics:
1. BTS-Crazed
#### Problem description : </br>
An audio [file](files/Save\ Me.mp3) was provided.
#### Solution : </br>
Used strings to obtain the flag.
Flag : rtcp{j^cks0n_3ats_r1c3}

2. cat-chat
#### Problem description : </br>
```
nyameowmeow nyameow nyanya meow purr nyameowmeow nyameow nyanya meow purr nyameowmeow nyanyanyanya nyameow meow purr meow nyanyanyanya nya purr nyanyanyanya nya meownyameownya meownyameow purr nyanya nyanyanya purr meowmeownya meowmeowmeow nyanya meownya meowmeownya purr meowmeowmeow meownya purr nyanyanyanya nya nyameownya nya !!!!
```
once you've figured this out, head to discord's #catchat channel.

#### Solution : </br>
The text consisted of three repeating words `nya`, `meow` and `purr`. It hints of morse code, so I converted `nya` to '.', `meow` to '-' and `purr` to '/'. Used an online morse code decoder to obtain the text.

The discord channel, was filled with encoded chats by two bots. So, I converted 'rtcp' to morse code, encoded them and searched for the text in discord to get flag.

Flag : rtcp{th15_1z_a_c4t_ch4t_n0t_a_m3m3_ch4t}

3. BASmati ricE 64
#### Problem description : </br>
There's a flag in that bowl somewhere...
![image](files/rice-bowl.jpg)
Replace all zs with _ in your flag and wrap in rtcp{...}.
#### Solution : </br>
Using steghide, we get a txt file.
```
steghide --extract -sf rice-bowl.jpg
```
consisting of the text
```
³I··Y·ç;aÖx9Ì
÷ÏyÜÐ=Ý
```
The title hints at base64, so we encode the text to base 64 to get the flag.
```
~/RiceTeaCatPanda ● base64 steganopayload167748.txt 
s0m3t1m35zth1ng5zAr3z3nc0D3d
```
Don't forget to replace the z's with _'s

Flag : rtcp{s0m3t1m35_th1ng5_Ar3_3nc0D3d}

## Misc:
1. Strong Password
#### Problem description : </br>
Eat, Drink, Pet, Hug, Repeat!
#### Solution : </br>
All four words hint to the event title RiceTeaCatPanda.

Flag : rtcp{rice_tea_cat_panda}

## Web:
1. Robots. Yeah, I know, pretty obvious.
#### Problem description : </br>
So, we know that Delphine is a cook. A wonderful one, at that. But did you know that GIANt used to make robots? Yeah, GIANt robots.
#### Solution : </br>
Quite obviously a hint at `robots.txt` file. I went to https://riceteacatpanda.wtf/robots.txt to find two files `flag` and `robot-nurses`. https://riceteacatpanda.wtf/flag didn't give the flag so I tried https://riceteacatpanda.wtf/robot-nurses to obtain the flag.

Flag : rtcp{r0b0t5_4r3_g01ng_t0_t4k3_0v3r_4nd_w3_4r3_s0_scr3w3d}

## General: 
1. Basic C4
#### Problem description : </br>
A txt [file](files/da_bomb.txt) was provided and hints were provided stating the flag begins with c4 and is a 90 character long flag.
#### Solution : </br>
Decoding the base64 text in the txt file led to nothing(but an obvious remark that we are not supposed to base64 decode it). Some google searches led to http://www.cccc.io/. Uploaded the txt file to get the flag.

Flag : rtcp{c42CW3TbiGhvptM36RJJ9ScctgkskjvZPo6dG8JexzZRvzQR6hwovZJLDkYK5pZ6cq9e7fX1ShUiYUdM7H1Uuqj64G}

2. NO¯Γ̶ IX
#### Problem description : </br>
I can't seem to figure out this broken equation... a lot seems to be missing...
```
meow = Totally [Chall Title]

100-hex(meow)=flag!

```
#### Solution : </br>
Low points hinted that it should not be too complicated. So, I tried Roman numeral conversions to get `100 - hex(IX)` = `100 - hex(9)` = `f7`

Flag : rtcp{f7}

2. Treeee
#### Problem description : </br>
It appears that my cat has gotten itself stuck in a tree... It's really tall and I can't seem to reach it. Maybe you can throw a snake at the tree to find it? Oh, you want to know what my cat looks like? I put a picture in the hints.

Hint :
My cat looks like this
```
#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF#FFFFFF#FFFFFF#FFFFFF#FFC90E #FFC90E#000000#FFC90E#FFFFFF#FFFFFF#FFFFFF#FFFFFF#FFC90E#FFFFFF #FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF #FFFFFF#FFFFFF#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF #FFFFFF#FFFFFF#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF #FFFFFF#FFFFFF#FFFFFF#FFC90E#FFFFFF#FFC90E#FFFFFF#FFFFFF#FFFFFF
```

A [zip](files/treemycatisin.7z) file was provided.
#### Solution : </br>
The hex codes are color values. Although, the image dimensions are too low to display a flag I extracted the image anyway.

```
import numpy as np
import cv2
code = "#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF#FFFFFF#FFFFFF#FFFFFF#FFC90E #FFC90E#000000#FFC90E#FFFFFF#FFFFFF#FFFFFF#FFFFFF#FFC90E#FFFFFF #FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF #FFFFFF#FFFFFF#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF #FFFFFF#FFFFFF#FFC90E#FFC90E#FFC90E#FFC90E#FFC90E#FFFFFF#FFFFFF #FFFFFF#FFFFFF#FFFFFF#FFC90E#FFFFFF#FFC90E#FFFFFF#FFFFFF#FFFFFF"
code = code.split(' ')
for i in range(len(code)):
    code[i] = code[i].split('#')
    code[i].remove('')

print(np.shape(code))
img = np.zeros((6, 9, 3))
for i in range(6):
    for j in range(9):
        img[i, j, 0] = int(code[i][j][0:0+2], 16)
        img[i, j, 1] = int(code[i][j][2:2+2], 16)
        img[i, j, 2] = int(code[i][j][4:4+2], 16)
cv2.imwrite('img.jpg', img)
```
The 7z file had less file size, but the extracted directory had much larger file size hinting at repeating files and a lot of empty directories and subdirectories. It can be observed that all the directory consists of two images having a dummy flag. So, I ended up copying all `.jpg` files to a single directory and deleting all files having the file size `1496` bytes and `1718` bytes (the file size of the repeating images)

```
$ for f in $(find ./bigtree -type f); do cp $f extract/ ; done;
$ find -size 1496 -delete
$ find -size 1718 -delete
```

Flag : RTCP{MEOW_SHARP_PIDGION_RICE_TREE}

3. Motivational Message
#### Problem description : </br>
My friend sent me this motivational message because the CTF organizers made this competition too hard, but there's nothing in the message but a complete mess. I think the CTF organizers tampered with it to make it seem like my friend doesn't believe in me anymore, but it's working like reverse psychology on me!!!!

A [file](files/motivation.txt) was provided.
#### Solution : </br>
Performing `strings -a` resulted in `data`. No leads here, so I checked binwalk and stego tools.

On checking hexdump of the file, we get the output
```
~/RiceTeaCatPanda/● hexdump -C motivation.txt| head
00000000  82 60 42 ae 44 4e 45 49  00 00 00 00 df db f8 e5  |.`B.DNEI........|
00000010  19 76 cb 05 03 ff ef fe  92 3f f8 11 ec 04 01 00  |.v.......?......|
00000020  40 10 04 01 00 40 10 04  01 00 40 10 04 51 d3 6e  |@....@....@..Q.n|
```
The chunks are reversed `IEND`. This hints at reversed `PNG` file. We check the tail to get the output
```
~/RiceTeaCatPanda● hexdump -C motivation.txt| tail
00040d40  c9 24 92 49 24 92 5f a3  8e 38 e3 df 38 e3 8e 38  |.$.I$._..8..8..8|
00040d50  fb fb ff ff e3 fd dd 44  0f dd ec 5e 78 54 41 44  |.......D...^xTAD|
00040d60  49 00 20 00 00 3b 4f 36  12 00 00 00 06 08 ad 03  |I. ..;O6........|
00040d70  00 00 e8 03 00 00 52 44  48 49 0d 00 00 00 0a 1a  |......RDHI......|
00040d80  0a 0d 47 4e 50 89                                 |..GNP.|
```
It's reversed PING image, so I reversed the contents of file
```
$ file.txt xxd -p -c1 | tac | xxd -p -r > rev_file.png
```
I used `zsteg` to get flag.

Flag : rtcp{^ww3_1_b3l31v3_1n_y0u!}