<div align="center">

# 🃁 Hidden in Plain Sight 🃁
  
---

 **Category:** Web Exploitation | **Points:** 100 pts | **Difficulty:** Very Easy | **Author:** K33P5

> **Description:** It was hidden in our page

<img width="508" height="394" alt="photo_2026-09-14_18-48-30" src="https://github.com/user-attachments/assets/0e866b40-cb74-4eaa-a542-1295078c8424" />

</div>

---

## TL;DR

Sensitive Data Exposure (CWE-615) located in the landing page HTML source due to unstripped client-side comments. This allows an unauthenticated user to retrieve the challenge flag directly without authorization.

---

## Reconnaissance & Initial Analysis

Since the description already hinting the flag is in their page, I tried to open the source code on the challenge page and searched for the flag format `DwD{}`

<img width="1280" height="632" alt="photo_2026-09-14_18-48-59" src="https://github.com/user-attachments/assets/55492369-1036-429e-824f-f3040cea3793" />


But there was no flag in sight. So I redirected to the main page and take a look at the source code to find the flag again.

<img width="1280" height="634" alt="photo_2026-09-14_18-48-55" src="https://github.com/user-attachments/assets/926f54c2-9242-40db-b042-7857585ca4fd" />


And I found the flag. 
<img width="1280" height="640" alt="photo_2026-09-14_18-48-52" src="https://github.com/user-attachments/assets/b1df40cb-d279-4d48-9bad-7105299a0d53" />


`flag = DwD{D4mN_u_H4v3_5h4Rp_3ye5!}`










