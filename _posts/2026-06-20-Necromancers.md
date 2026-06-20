---
layout: post
title: Necromancers Notebook
date: 20-06-2026
categories: [Basics]
tags: [exfiltration, blind, commandinjection, wget]
image: "https://cf.geekdo-images.com/hiXwF2UFSIWSXkuSNwoOIQ__opengraph/img/iTjB-p00DArT4o02t3N1kdHr0tk=/0x0:894x469/fit-in/1200x630/filters:strip_icc()/pic5060418.jpg"
---

## Start the Instance
create an account 
name: kid
password: 123456

open source code and find the password signin the token is 
```
pumpkin
```
Lets try crack it prove
<img width="1920" height="445" alt="image" src="https://github.com/user-attachments/assets/23d91461-abee-42c8-a1fb-7d606251c985" />
lets sign the token to user kid and use it to retreave the flag using the bew
```
curl http://<target>/api/admin/flag \
  -H "Authorization: Bearer <forged_token>"
```
<img width="1920" height="537" alt="Screenshot From 2026-06-20 10-45-02" src="https://github.com/user-attachments/assets/22f7dab9-4635-422c-9f46-5650d6729748" />

Mission completed successfully

<img width="1268" height="444" alt="image" src="https://github.com/user-attachments/assets/0380aab3-87c2-4d75-a953-8d5836ae3bb3" />

# bye bye no more token tilll monday 
