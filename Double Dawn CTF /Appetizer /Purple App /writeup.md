<div align="center">

# 🃁 Purple App 🃁
  
---

 **Category:** Misc | **Points:** 100 pts | **Difficulty:** Very Easy | **Author:** rlr

> **Description:** Just like the title:33 

<img width="507" height="397" alt="photo_2026-09-14_18-49-23" src="https://github.com/user-attachments/assets/b5829530-26cc-4473-94bd-caaa82258a0d" />

</div>

---

## TL;DR

Hidden information and simple encoding via public Discord server recon. The flag was located in a Discord channel's topic description disguised as a hex-encoded string, which was converted using CyberChef.

---

## Reconnaissance & Initial Analysis

When I opened the event's discord server, there's a description I noticed written `Discord Flag [number]` on the announcement channel's topic. So I clicked it and found out it wasn't any random numbers. The format was hex-encoded that can be converted into ASCII string.
<div align="center">
<img width="1172" height="696" alt="image" src="https://github.com/user-attachments/assets/c7260aa9-695c-476d-8293-47f7d8b4b867" />

<img width="490" height="179" alt="image" src="https://github.com/user-attachments/assets/4af0bef6-5498-4f2f-9d0a-09e028965eb6" />
</div>

hex code = `64 61 77 6E 63 6F 72 64`

So I copy the hex code to convert them using CyberChef. CyberChef is a common CTF tool used for converting from one format to another.
<div align="center">
<img width="922" height="354" alt="image" src="https://github.com/user-attachments/assets/6ffb07fb-4411-4d5f-ab94-dbc461bddaca" />
</div>

Using the `from Hex` option, the output shows the string as `dawncord`, indicated that it was a hidden flag encoded into hex format.

`flag = DwD{dawncord}`

