# WordPress-vs-Kali-CyberSecurity-Assignment

Exploits:

1. WordPress 4.2.3-4.8.1 – Authenticated Cross-Site Scripting (XSS) in Visual Editor

Summary:

--Vulnerability: Cross Site Scripting (XSS)

--Affected Versions: WP 4.2.3-4.8.1 (https://wpvulndb.com/vulnerabilities/8914)

--Latest Patch/Fix: 4.8.2

--Source Code: https://core.trac.wordpress.org/changeset/41395

--Steps to Recreate:

  1. Create a new post, and add an HTML img tag containing onerror=alert(1)
  2. Navigate to the post and it should send an alert to the user.

--Video Walkthrough

<img src="https://i.imgur.com/pEOEukA.gif" alt="It's not showing oof">

2. WordPress 4.2 - Unauthenticated Cross-Site Scripting (XSS) using Comment Section

Summary:

--Vulnerability: Cross Site Scripting (XSS)

--Affected Versions: 3.9.3, 4.1.1, 4.1.2, 4.2

--Latest Patch/Fix: 4.2.1

--Source Code: https://core.trac.wordpress.org/changeset?sfp_email=&sfph_mail=&reponame=&new=32311%40branches%2F4.2&old=32300%40branches%2F4.2

--Steps to Recreate:

1. As any user (no admin required), go to the comment section of any post.
2. Comment the following within an HTML "a" tag, replacing "64 KB TEXT HERE" with at least 64kb worth of characters. 

a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  64KB TEXT HERE'

3. Navigate to the post, and any user can be affected by this exploit. Scripts can actually be run on the server using this exploit.

--Video Walkthrough

<img src="https://i.imgur.com/gDsnf2O.gif" alt="Oof didn't load">
