<div align="center">

# 🃁 High Card Duel 🃁
  
---

 **Category:** Web Exploitation | **Points:** 200 pts | **Difficulty:** Easy | **Author:** K33P5

> **Description:** The house always wins... except when the house forgets to check which way the money is flowing. Beat the dealer, build your chip stack, and cash in the flag.

<img width="510" height="572" alt="High Card Duel" src="https://github.com/user-attachments/assets/fe5e5c28-124b-4ca2-a48a-7cdebedc3a4b" />

</div>

---

## TL;DR

The "HIGH CARD DUEL" interface requires reaching 1,000,000 chips to open the vault that contains the flag. Because playing normally with 100 starting chips is too slow or impossible to win with the random possibilities, this page points to a logic flaw or parameter tampering vulnerability. Intercepting the betting request in Burp Suite allows us to either send a negative bet amount to force a win payout or tamper with the bet value parameter directly to generate 1,000,000 chips in a single deal.

---

## Reconnaissance & Initial Analysis

Playing along with how the system works, the possibility to win or lose is completely random. 


<img width="1280" height="642" alt="photo_2026-09-14_11-27-51" src="https://github.com/user-attachments/assets/e66b7748-c40d-4cf9-a463-760eff2fd51a" />

`lose`

<img width="1280" height="642" alt="photo_2026-09-14_11-27-54" src="https://github.com/user-attachments/assets/8f70cd8e-2227-4c91-a9f5-0e991d896ed6" />

`win`

<img width="1351" height="678" alt="image" src="https://github.com/user-attachments/assets/18cf5db6-b9ba-47d6-82f8-353a7fa36820" />


When I open `network` on inspect, I noticed that 

<img width="1152" height="473" alt="image" src="https://github.com/user-attachments/assets/fb391c92-0f1b-41ce-9076-b9f6fec2787a" />

<img width="1147" height="474" alt="image" src="https://github.com/user-attachments/assets/ebda2208-5397-43ff-9550-87587e57efba" />

---

# Walkthrough

Usually when we're dealing with web exploitation, one of the common tool to use is Burp Suite. Burp Suite primarily intercepting with the proxy server. What is a proxy? It is an intermediary hardware device or software application that acts as a gateway between a client device and the internet. 

To intercept the web, we are going to turn on the intercept right after betting for the amount.

---

# Flag

``

---
# Ways to Mitigate
