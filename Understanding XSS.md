Bug bounty hunting is a fun way to earn money by finding security issues in websites and apps. If you’re just starting, don’t worry! In this article, I’ll teach you how to find 5 **easy bugs** step by step.

You don’t need to be an expert, just follow these simple methods, examples, and commands, and you’ll be on your way to your first bug bounty!

# 1. Find an XSS (Cross-Site Scripting) Bug

XSS allows an attacker to insert malicious scripts into a website. It’s one of the easiest bugs to find.

## Example: Basic XSS Test in Search Bar

Let’s say you’re testing a website and it has a search bar. Try typing the following code into the search bar:

![](https://miro.medium.com/v2/resize:fit:700/1*GwQeM9gXSA-dztTHlz4A_g.png)

```
<script>alert('==XSS== Found!')</script>
```

If you see a pop-up alert saying “XSS Found!”, you’ve found a vulnerability! This means the website is allowing your script to run, which can be dangerous.

## Steps:

1. Go to a website with a search or input box.
2. Enter the script above and hit enter.
3. If an alert box pops up, you’ve found an XSS bug.

## Practice:

- You can practice XSS on websites like **Google Gruyere** or **bWAPP**.
- Try finding XSS bugs on bug bounty platforms like **HackerOne** and **Bugcrowd**.

# 2. Find an Open Redirect Bug

Open Redirect happens when a website allows users to be redirected to any URL without proper validation. This can be used to trick users into going to malicious sites.

![](https://miro.medium.com/v2/resize:fit:477/1*_laIpoJM2L87BVTWwUlaAQ.png)

## Example: Testing a Redirect URL

Let’s say you find a URL on a website like this:

![](https://miro.medium.com/v2/resize:fit:483/1*viweSf47OAw-VV9ky_jQZg.png)

https://example.com/redirect?url=https://goodsite.com

Try changing the `goodsite.com` to another website, like:

![](https://miro.medium.com/v2/resize:fit:472/1*itKwMVkWvCeE_5FZtjF1Ew.png)

https://example.com/redirect?url=https://evilsite.com

If the website takes you to `evilsite.com`, you’ve found an **Open Redirect** bug!

## Steps:

1. Look for URLs that contain “redirect” or “url=”.
2. Change the destination URL to something else (like `[https://evilsite.com](https://evilsite.com\).)`[).](https://evilsite.com\).)
3. If the website sends you to that new URL, you’ve found a bug.

## Practice:

- Try finding Open Redirect bugs on bug bounty programs. Look for URLs with parameters like `url=`, `redirect=`, or `next=`.

# 3. Find a CSRF (Cross-Site Request Forgery) Bug

CSRF tricks a user into making unwanted requests, like changing their password, without their knowledge.

![](https://miro.medium.com/v2/resize:fit:477/1*WZIBfj9REj35hIDmW8pnFw.png)

## Example: Basic CSRF Attack

If you find a form to change a password on a website, try crafting a fake form like this:

```

<form method="POST" action="https://example.com/change_password">  
  <input type="hidden" name="new_password" value="hackedpassword123" />  
  <input type="submit" value="Submit" />  
</form>

```

If this fake form can change the password without the user’s permission, the website is vulnerable to CSRF.

## Steps:

1. Find a form that performs a critical action (like changing a password).
2. Copy the form’s action URL and inputs.
3. Create a fake form using HTML like the example above.
4. Try submitting the form and see if it performs the action without authentication.

## Practice:

- You can practice CSRF on websites like **DVWA (Damn Vulnerable Web App)** or **bWAPP**.

# 4. Find a SQL Injection Bug

SQL Injection happens when you can manipulate a website’s database by inserting malicious SQL code. This is one of the most dangerous bugs but also easy to find.

# Example: SQL Injection in a Login Form

If you find a login form on a website, try entering the following into the username or password field:

![](https://miro.medium.com/v2/resize:fit:463/1*bowC7jI4AX7ZPX7LtZXO9w.png)

' OR 1=1 --

This code tricks the website into thinking you’re logged in without needing a password.

## Steps:

1. Find a login form or input field.
2. In the username or password field, enter the SQL code above.
3. If you gain access or see an error related to SQL, you’ve found a bug.

## Practice:

- Try SQL injection on platforms like **SQLi Labs** or **DVWA**.

# 5. Find a Subdomain Takeover

Subdomain Takeover happens when a subdomain points to a service that is no longer in use, but you can take control of it.

## Example: Finding Vulnerable Subdomains

Use a tool like **Sublist3r** to find subdomains:

sublist3r -d example.com

If a subdomain points to a service like Amazon S3, but the bucket doesn’t exist anymore, you can take over the subdomain and potentially find sensitive data.

## Steps:

1. Use **Sublist3r** or similar tools to find subdomains.
2. Look for subdomains that point to services like Amazon S3 or Heroku.
3. Check if the service is no longer in use by visiting the subdomain.
4. If it’s unclaimed, you can take over the subdomain.

## Tools:

- **Sublist3r**: Finds subdomains of a website.

## Learn More:

- [Sublist3r on GitHub](https://github.com/aboul3la/Sublist3r)

# Final Tips:

- **Practice Makes Perfect**: Use platforms like **HackerOne**, **Bugcrowd**, and **Open Bug Bounty** to find real bug bounty opportunities.
- **Use Tools**: Tools like **Burp Suite**, **OWASP ZAP**, and **Sublist3r** will help you automate some of the searching.

# Recap:

Here’s a quick summary of the easiest bugs to find:

1. **XSS**: Insert scripts into input fields and check for alerts.
2. **Open Redirect**: Modify URLs with `redirect=` or `url=` to test where they take you.
3. **CSRF**: Create fake forms to test if sensitive actions can be performed.
4. **SQL Injection**: Insert SQL code into login fields to manipulate the database.
5. **Subdomain Takeover**: Use tools to find subdomains that point to abandoned services.
