# PortSwigger Web Security Academy — Lab Write-ups

My solutions and notes from the [PortSwigger Web Security Academy](https://portswigger.net/web-security), worked through with Burp Suite.

Each write-up covers what the vulnerability is, how I found and exploited it in the lab, and how a developer would prevent it. I focus on understanding the root cause, not only the payload.

> All testing was done only against PortSwigger's intentionally vulnerable lab environments. Nothing here is for use against systems you don't have permission to test.

## Progress

| Topic | Apprentice | Practitioner | Expert |
| --- | --- | --- | --- |
| SQL injection | 0 | 0 | 0 |
| Cross-site scripting (XSS) | 0 | 0 | 0 |
| Authentication | 0 | 0 | 0 |
| Access control | 0 | 0 | 0 |
| Path traversal | 0 | 0 | 0 |
| Command injection | 0 | 0 | 0 |
| SSRF | 0 | 0 | 0 |
| CSRF | 0 | 0 | 0 |
| File upload | 0 | 0 | 0 |
| Business logic | 0 | 0 | 0 |

**Total labs solved: 0**

## Structure

```
labs/
  sql-injection/
    01-where-clause-hidden-data.md
  xss/
  authentication/
  access-control/
  ...
TEMPLATE.md
```

One file per lab, numbered in the order I solved them. New write-ups start from [`TEMPLATE.md`](TEMPLATE.md).

## Tools

- Burp Suite Community Edition (Proxy, Repeater, Intruder, Decoder)
- Firefox with FoxyProxy
