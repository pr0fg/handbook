# Origin IP (Cloudflare/WAF Bypass)

## CloudFlare/Akamai Origin Leak
- Akamai
  - Look for `origin-sub.domain.com` or `origin.sub.domain.com` to find the origin
  - Try sending this header (the origin is usually in the key): `Pragma: akamai-x-get-true-cache-key`