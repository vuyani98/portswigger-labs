# Lab: <lab title exactly as on PortSwigger>

- **Topic:** Cross-site request forgery (CSRF)
- **Level:** Apprentice 
- **Solved:** 2026-11-15
- **Lab link:** [<https://portswigger.net/web-security/...>](https://portswigger.net/web-security/learning-paths/csrf/csrf-common-flaws-in-csrf-token-validation/csrf/bypassing-token-validation/lab-token-not-tied-to-user-session)

## Goal

Use your exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address

## The vulnerability

The app does not validate that the CSRF Token is from the same user session, thereby allowing using one user's session and CSRF token to change another user's email address.

## How I found it

1. After logging in, I first changed my email address
2. I then looked though Burp Suite's **Proxy > HTTP history** for a request that changed the email address.
3. After i found the request, i sent it to **Burp Suite's Repeater**


## Exploit

```
<The payload or modified request. Keep it short.>
```

<One line on why this payload works.>

## Fix

<How a developer should prevent this, e.g. parameterised queries, output encoding, server-side access checks.>

## What I learned

- <One takeaway you'd mention in an interview.>
