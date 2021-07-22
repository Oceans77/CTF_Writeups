# Sh*tty Ransomware Write-up
A write up regarding the Forensics challenge Sh*tty Ransomware

So the challenge tells us about a peice of malware that infected someones computer</br>
disguised as a game and we're asked to find the IP and PORT number associated with it

To begin we start off by downloading a file called
```
Sh*ttyRansomware.raw
```
A simple strings search of the file shows a ton of info regarding a windows machine</br>
![Strings Return](https://i.ibb.co/yn1FNbv/strings.png)
Lets trying running Volatility on it to see if we're playing with a Dump file. </br>
```
python vol.py -f ShittyRansomware.raw imageinfo
```
Sure enough! Now we can extract some data
![imageinfo](https://i.ibb.co/zn5XYs1/imageinfo.png)

Now lets look at web history of this user</br>
I'm using the plugin - [Chromehistory](https://github.com/superponible/volatility-plugins) from 'superponible'
```
python vol.py -f ShittyRansomware.raw --profile=Win7SP1x64 chromehistory
```
![chromehistory](https://i.ibb.co/JykSMX2/chromehistory.png)
</br>
Here we can see 2 interesting links
> Google Drive - Pro Evolution Soccer</br>
> Pastebins - pro10 light version

If we take a look at the pastebins file we see some interesting info
![pastebins](https://i.ibb.co/SKR5Jc3/pastebins.png)</br>
A link to the game and a password for the file

After downloading and extracting the files we now have the malware executable
![malware](https://i.ibb.co/pPZtgLY/malware.png)

Now we need to see where its pointing...</br>
Lets load up wireshark and capture the packets while running the malware.

We can see an HTTP GET request was made
![wireshark1](https://i.ibb.co/n7NHfHj/wireshark1.png)

If we follow the HTTP stream we can now see the IP and PORT the malware was trying to contact
![httpstream](https://i.ibb.co/y4vJRYV/httpstream.png)
</br>
Now if we follow the IP and PORT
> http://23.97.198.147:32841

We will return the flag
```
Good job here is your flag Poseidon{HUh_u'R3_G0OD_4t_D1gG1nG}
```
![flag](https://i.ibb.co/9nMT4qq/flag.png)
