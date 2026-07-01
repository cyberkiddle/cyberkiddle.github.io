---
layout: post
title: Galaxy dash
date: 20-04-2025
categories: [Meddium]
tags: [exfiltration, blind, commandinjection, wget]
image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSEnQcMgVcMOJq7E-5REO-co9MRYc4WHQnnSc5WDBqTtzu1dEGZcNBhZsY&s=10"
---


# Start register account test

see on the clicent side how inputs are handled by js

```
onClick: async () => {
  const html = (await cr.get(`/api/invoices/${e}/download`)).data;
  const win = window.open("", "_blank");
  win && (win.document.write(html), win.document.close());
}
```
This means there is XSS vulneurability on downloading the pdf
<img width="1920" height="986" alt="image" src="https://github.com/user-attachments/assets/f22f8be2-8f95-41bf-915e-dbbf7730ab34" />

tried to create multiple and see if the XSS is on description but not

lets try another place
<img width="1920" height="986" alt="image" src="https://github.com/user-attachments/assets/8dfc65fd-e101-4466-b5d6-4a99ee90a73e" />

<img width="1728" height="816" alt="image" src="https://github.com/user-attachments/assets/479275ff-49ef-4c82-baad-f8d1c6fa31e0" />

Found the reason is on bold
```
&lt;test&gt; <b>bold</b> ' " `
```
<img width="1484" height="670" alt="image" src="https://github.com/user-attachments/assets/a92e8c8e-b7bf-477d-bb5c-43dafa45e991" />

Now lets download
<img width="1920" height="1013" alt="image" src="https://github.com/user-attachments/assets/0a183e6b-8e98-4b19-a61a-3689c0d02973" />

Boom proved but not yed lets try to hook the admin token see if we can have 'IsAdmin'




