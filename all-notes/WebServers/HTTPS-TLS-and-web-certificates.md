# HTTPS, TLS, and Web Certificates
- most websites didn't need to protect user info

## HTTPS and TLS
- secure version of HTTP is **Secure Hypertext Transport Protocol** or **HTTPS**
    - HTTP with a secure connection before any data is exchanged
- having secure connection means all data encrypted using **TLS protocol**
    - negotiates a shared secret that is then used to encrypt data
    - use `curl -v` to see the actual negotiation
    - `>/dev/null` throws away actual HTTP response
    - browser will compare the certificate domain name to the one represented in the URL and if they don't match, or the certificate is invalid or out of date, it will display a massive warning

## Web Certificates
- generated by a trusted 3rd party using public/private key encryption
- **Let's Encrypt** made it so you could get certificates for free
- Caddy uses Let's Encrpyt to generate a web certificate every time an HTTPS request is made for a domain name that Caddy doesn't have a web certificate for

## Enabling HTTPS
- should always support HTTPS (most web browsers exclusively support it)
- obtain, and renew, a web certificate by enabling the ACME protocol for your web server and communicating with Let's Encrypt
### Caddy
- Caddy has ACME support built into it by default, and so all you need to do is configure Caddy with the domain name