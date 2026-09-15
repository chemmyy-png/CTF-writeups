<div align="center">

# 🃁 Fold or Call 🃁
  
---

 **Category:** Web Exploitation | **Points:** 200 pts | **Difficulty:** Easy | **Author:** K33P5

> **Description:** Every good poker player knows what not to show. Somewhere in this platform, the house told the search engines exactly which cards to fold. Can you find the hand they didn't want played?

<img width="507" height="462" alt="photo_2026-09-14_11-37-46" src="https://github.com/user-attachments/assets/188771a8-847d-4983-87bd-a27574806fbd" />
</div>

---

## TL;DR

Many web applications rely on restricted endpoints such as `/admin` or `/phpmyadmin` for internal management. Sensitive Information Exposure (CWE-200) occurred via public robots.txt configuration, where the web application listed internal operational directories within crawler exclusion rules. This allowed unauthenticated users to perform reconnaissance, discover hidden paths, and access challenge endpoints directly.

---

## Reconnaissance & Initial Analysis

The challenge description referenced search engines. Programs like Googlebot are automated client-side web crawlers used to discover, scan, and index web content. When crawling a site, these bots voluntarily parse the root `/robots.txt` file which is the standard used to specify crawling exclusion-rules to determine which paths should not be indexed.

To confirm this, I'm using `nikto` command. `Nikto` is a linux tool where it scans against the target web server to identify server misconfigurations, outdated components, and publicly exposed sensitive files.

<div align="center">
<img width="1137" height="491" alt="image" src="https://github.com/user-attachments/assets/fbc7867c-bdd7-49c3-9fe2-b3bf7e054f7f" />
</div>


```
nikto -host https://k33p5.resonode.net/
```

Command usage walkthrough
* `nikto`: The command-line executable for the Nikto web server vulnerability scanner.
* `-host`: Specifies the target host URL to scan. In this case, `https://k33p5.resonode.net/` is the target.

During the scanning, `nikto` flagged the presence of a `/robots.txt` file. The public `/robots.txt` file mistakenly leaked restricted administrative paths to unauthenticated users

This explain the Sensitive Information Exposure (CWE-200) vulnerability, as the server relies on "security through obscurity" rather than enforcing strict server-side access controls on the listed paths.

---

# Walkthrough

I added the `/robots.txt` directory to the path, and it redirects me to its content. 

<div align="center">
<img width="443" height="177" alt="photo_2026-09-14_11-37-50" src="https://github.com/user-attachments/assets/952f65f4-c01e-43de-bd7b-22e5b7477717" />
</div>


```
User-agent: *
Disallow: /admin
Disallow: /pkr-royal-vault
```

The `User-agent: *` and `Disallow:` directives tell all search engine crawlers to ignore the entire site. However, this is only a polite request, attackers and security tools can ignore it and scan the site anyway.

I want to see what both pages has to offer, so I first inspected the `/admin` page.

<img width="1280" height="713" alt="photo_2026-09-14_11-37-55" src="https://github.com/user-attachments/assets/b28b7352-a99e-416f-af71-33c85b906735" />

But the page was quick to redirect back to the login page. 

Navigating directly to `/admin` resulted in an immediate HTTP 302 redirect to the `/login` endpoint. The `/admin` path redirected straight to `/login` because the server blocks unauthenticated users.

Now, let's go to the `/pkr-royal-vault` page. Trying to open `/admin` just sent us back to `/login` because it requires a sign-in. 

However, opening `/pkr-royal-vault` worked right away without redirecting to other pages. The page loaded a card game called "YOU CALLED THE BLUFF", where you have to pick the Ace of Spades from five face-down cards to win.

<img width="1280" height="464" alt="photo_2026-09-14_11-37-58" src="https://github.com/user-attachments/assets/455625f8-831b-4081-8616-9650edd44228" />
<div align="center">
<img width="785" height="396" alt="photo_2026-09-14_11-38-01" src="https://github.com/user-attachments/assets/0ea89571-f6ed-485f-a564-2014229d662e" />
</div>

After picking cards, I hit the Ace of Spades on the 7th try. The site displayed "You hit the JACKPOT" along with an encoded base64 underneath: `RHdEe3IwYjB0c19kMG50X3BsNH1fcDBrM3JfZjRjM30=`.

Using CyberChef to convert the encode into plaintext to find out the text behind it.

<img width="1154" height="379" alt="photo_2026-09-14_11-38-08" src="https://github.com/user-attachments/assets/4b9ff89a-0cc4-417b-b93b-65c9d8152dad" />

After converting, the text revealed the flag immediately, which bring us to victory :D

---

# Flag

`DwD{r0b0ts_d0nt_pl4y_p0k3r_f4c3}`
