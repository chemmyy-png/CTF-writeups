<div align="center">

# 🃁 Advertisment 🃁
  
---

 **Category:** Steganography | **Points:** 100 pts | **Difficulty:** Very Easy | **Author:** rlr

> **Description:** What was our first ads for this event?

<img width="514" height="436" alt="photo_2026-09-14_18-49-03" src="https://github.com/user-attachments/assets/898f2dcd-056f-4d82-9b36-63644571ec33" />

</div>

---

## TL;DR

Visual steganography via image manipulation. Text was embedded directly into the image's low-contrast color channels and revealed by adjusting brightness/contrast levels.

---

## Reconnaissance & Initial Analysis

The first ad for this event was advertised by a poster. Surely, there was something hidden in the poster itself. I first check the image's metada using `AperiSolve` to see if there's any hidden user comments, base64 or ROT13 text. 
<div align="center">
<img width="1160" height="485" alt="image" src="https://github.com/user-attachments/assets/152ed18c-d4bc-414b-8bf8-6179a444cb2d" />
<img width="1134" height="476" alt="image" src="https://github.com/user-attachments/assets/d9793fb7-eb72-440e-8f81-055a689466f5" />
</div>

---

# Walkthrough

AperiSolve is one of the steganography/foresnic tool where it runs multiple common CLI commands such as `exiftool`, `binwalk`, `strings`, etc without the need to type them manually in the terminal. It also analyzes input images to refine colors to check whether the image has any hidden text.

In this case, the metadata doesn't contain any suspicious contents I mentioned. But scrolling through the image color remappings, I found something inside the image.
<div align="center">
<img width="500" height="880" alt="image" src="https://github.com/user-attachments/assets/5afa3b73-f017-4be1-9c76-c0bf8c9a7c75" />
<img width="500" height="160" alt="image" src="https://github.com/user-attachments/assets/c8497f94-a726-46df-a5ae-b73962af5875" />
</div>

With this, I can already see the flag format.

---

# Flag

`DwD{yOu_4r3_r34dy_for_7h15}`
