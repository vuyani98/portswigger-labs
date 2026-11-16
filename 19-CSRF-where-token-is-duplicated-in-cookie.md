# Lab: CSRF where token is duplicated in cookie

- **Topic:** CSRF (Common flaws in CSRF token validation)
- **Level:** Practitioner
- **Solved:** 2026-11-17
- **Lab link:** https://portswigger.net/web-security/learning-paths/csrf/csrf-common-flaws-in-csrf-token-validation/csrf/bypassing-token-validation/lab-token-duplicated-in-cookie#

## Goal

Use exploit server to host an HTML page that uses a CSRF attack to change the viewer's email address.

## The vulnerability

This lab's email change functionality is vulnerable to CSRF. It attempts to use the insecure "double submit" CSRF prevention technique. It does not even check if the token is valid, only checks it's length

## How I found it

1. After logging in, i went straight to changing the email of the provided account (wiener:peter) so that the request can go to Burp's **Proxy > history**
2. In Proxy History, i found the endpoint `/my-account/change-email` which is used when changing the email and sent it to Burp Repeater
3. Upon inspection i realized the app uses double submit of the `csrf` token in cookies and in the form. I then changed a few characters on both csrf token and sumbitted a `POST` request and it worked, proving that the token does not need to be correct but of the required length (32 characters).

## Solution
1. First step was to find an endpoint that had `Set-Cookie` in its response header and i found a GET request to `/?search=something` does that, so in my exploit server, i used it in my exploit html by adding an image with the `src` equal to the search query injected with a Set-Cookie which i set to a random 32-char string which i also put in a hidden input element as the csrf token. 
2. I added an `onerror` attribute to the image which equaled to the auto submission of form and voala!


## Fix

Maintain a server-side record of tokens so that they can be validated or have a way of authenticating them and avoid behaviors that allow users/attacker to set a cookie in the browser.

## What I learned
Using signed double-submit pattern, alongside SameSite cookies and Origin/Referer validation is much better.
