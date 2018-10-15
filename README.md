# Project 7 - WordPress Pentesting

Time spent: **6** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) WordPress 4.2.3-4.8.1 – Authenticated Cross-Site Scripting (XSS) in Visual Editor
  - [x] Summary: 
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2.3-4.8.1 (https://wpvulndb.com/vulnerabilities/8914)
    - Fixed in version: 4.8.2
  - [x] GIF Walkthrough: <img src="https://i.imgur.com/pEOEukA.gif" alt="It's not showing oof">
  - [x] Steps to recreate: 
    1. Create a new post, and add an HTML img tag containing onerror=alert(1)
    2. Navigate to the post and it should send an alert to the user.
  - [x] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/changeset/41395)
2. (Required) WordPress 4.2 - Unauthenticated Cross-Site Scripting (XSS) using Comment Section
  - [x] Summary: 
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 3.9.3, 4.1.1, 4.1.2, 4.2
    - Fixed in version: 4.2.1
  - [x] GIF Walkthrough: <img src="https://i.imgur.com/gDsnf2O.gif" alt="Oof didn't load">
  - [x] Steps to recreate: 
  1. As any user (no admin required), go to the comment section of any post.
  2. Comment the following within an HTML "a" tag, replacing "64 KB TEXT HERE" with at least 64kb worth of characters. 

  a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  64KB TEXT HERE'

  3. Navigate to the post, and any user can be affected by this exploit. Scripts can actually be run on the server using this exploit if an admin is affected.
  - [x] Affected source code:
    - [Link 2](https://core.trac.wordpress.org/changeset?sfp_email=&sfph_mail=&reponame=&new=32311%40branches%2F4.2&old=32300%40branches%2F4.2)
3. (Required) WordPress 4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [x] Summary: 
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.0 - 4.7.2
    - Fixed in version: 4.7.3
  - [x] GIF Walkthrough: 
  <img src="https://i.imgur.com/PvOQVuj.gif" alt="OOF!!!! didn't load either lmao">
  - [x] Steps to recreate: 
  1. As a user with at least contributor permissions, create a post, and embed a youtube URL.
  2. At the end of the URL, add in scripts between the two character sets \x3csvg and \x3e which represent <svg and > respectively, where <svg is "scalable vector graphics" in html which is generally used for embedding.
  3. Any user who navigates to this post can be affected by this exploit, here I used just a simple alert(1)
  - [x] Affected source code:
    - [Link 3](https://core.trac.wordpress.org/changeset/40160/trunk/src/wp-includes/embed.php?old=38361&old_path=trunk%2Fsrc%2Fwp-includes%2Fembed.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [ScreenToGif](https://www.screentogif.com/).

## Notes

Describe any challenges encountered while doing the work

In the youtube exploit, I actually mixed single and double quotes at one point and it wasn't functioning properly.

For the comment section exploit, finding 64kb of text was a bit rough, and it repeatedly sends alerts so it can be very damaging to users.

## License

    Copyright [2018] [Tam Phan]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
