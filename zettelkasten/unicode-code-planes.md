---
created-at: 2022-12-15 20:55
role: idea
tags: unicode
---

# Unicode code planes

Unicode is divided into 17 code planes. The first code plane is for code points U+0000 - U+FFFF and is called the Basic Multilingual Plane (BMP). It contains characters for many of the most common languages.

The remaining 16 code planes contain the Supplementary Characters. These code planes contain code points U+10000 - U+10FFFF.

>> [!note]
>> Not all of the code points in the BMP correspond to a character. Some of them are [[unicode-surrogates|reserved]] for use in encoding Supplementary Characters by combining code units.

---
# References

[[Core Java - Volume 1#03 - Fundamental Programming Structures in Java]]
[[Core Java - 03.03.04-03.04.01a.pdf]]