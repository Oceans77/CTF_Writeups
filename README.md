# b01lersCTF2021-pyjailgolf_1

Challenge:

You have 10 characters to get the flag. Have fun!

nc chal.b01lers.com 1334
```python
line = input('>>> ')

flag="[REDACTED]"

if len(line) > 10:
    raise Exception()

try:
    eval(line)
except:
    pass
``` 
To do this I just played around with built-in functions until I found the "help()" function and passed the flag into the parameter

.>>> help(flag)

![Example](https://i.ibb.co/K2M20cN/2021-04-04-08h24-23.png)
```text
pctf{JusT_a5k_4_h3lP!}
```
