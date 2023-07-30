# DOWN BAD

Challenge Description:
> The flag is right there!

The file given for this challenge is called "down_bad.png", shown below
![down_bad.png](https://i.ibb.co/zGdVvj2/2023-07-30-11h46-06.png)

To solve this challenge you need to modify the IHDR in hex to change the size of the image.
To do this I just used a simple program called [TweakPNG](https://entropymine.com/jason/tweakpng/) and modify the chunk to `3ECA0FBA`

![tweakpng](https://i.ibb.co/nnFXv1d/2023-07-30-11h55-11.png)

After saving the file we can open the png and reveal the flag

![flag](https://i.ibb.co/qM8Jkmr/down-bad.png)

Flag: `TFCCTF{28ae25c96850245ffdd70a880158f9f3}`
