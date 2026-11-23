# Lab: SameSite Strict bypass via client-side redirect

- **CSRF**
- **Level:** Practitioner 
- **Solved:** 2026-11-23
- **Lab link:** https://portswigger.net/web-security/learning-paths/csrf/csrf-bypassing-samesite-restrictions-using-on-site-gadgets/csrf/bypassing-samesite-restrictions/lab-samesite-strict-bypass-via-client-side-redirect

## Goal
Perform a CSRF attack that changes the victim's email address.

## The vulnerability
The email function in this site is vulnerable to CSRF because SameSite restrictions can be paased using client side redirestion.

## How I found it

First i changed the email of the user given in the lab and sent the POST request to Burp Repeater to examine it. I changed the method from POST to GET and put the params email & submit in the request url. Turns out the endpoint does change the email via a GET request and that was the first crucial finding. After some hours of trial and error, i discover the site has a script that handles redirects after commenting and it takes the postid from the query param and redirects to it. 

## Exploit

```
<script>
    window.location.href="https://0a0a00e203c7f24f805603840036005d.web-security-academy.net/post/comment/confirmation?postId=../../my-account/change-email?submit=1%26email=new%40email%2eco"
</script>
```

This works because i simply replace the value of postId with the path to the email change url that has the necessary parameters and thereby redirecting to it and bypassing samesite restrictions.

## Fix
Avoid functions that change critical data using a simple GET request and always make sure SameSite restrictions work.
