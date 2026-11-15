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

1. After logging in, I first changed wiener's email address
2. I then looked though Burp Suite's **Proxy > HTTP history** for a request that changed the email address.
3. After i found the request, i sent it to **Burp Suite's Repeater**
4. In incognito, i logged into the other account (carlos) provided in the lab, inspected the form, found the CSRF token and copied it
5. I then went back to Burp Repeater to that request and changed only the CSRF token from wiener's to carlos's and a new email address.
6. I then refreshed each account's "/my-account" page and saw that wiener's email had changed but using carlos' CSRF

## Exploit
``` html
<form method="POST" action="<LAB_URL/my-account/change-email">
  <input type="hidden" name="email" value="new-email@mail.net" />
  <input type="hidden" name="CSRF" value="MY_CSRF_TOKEN"/>
</form>
<script> document.forms[0].submit() </script>
```

## Fix
Validate session tokens and csrf to make sure they come from the same user making the request

