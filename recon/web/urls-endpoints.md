# URLs & Endpoint Discovery

## Enumerating Old URLs
Wayback machine has a public API where you can provide a domain name and it will return a JSON array of all known URLs seen in the past.

Use Cases:
- Find endpoint names specific to a domain to generate better wordlists for brute-forcing

Tools:
- [Wayback URLs](https://github.com/tomnomnom/waybackurls) can mass fetch this data from the API

## Brute-Forcing URLs
Find all the things, obviously.

Use Cases:
- Find old scripts, vulnerable apps, etc.

Tools:
- [Meg](https://github.com/tomnomnom/meg) can be used to mass brute force from a list of domains and a wordlist. It will interleave requests as to not take any servers offline.
- [gospider](https://github.com/jaeles-project/gospider)

## Site Spidering

Tools
- [GoSpider](https://github.com/jaeles-project/gospider)

## Exposed Files / Directory Scanner
- [gobuster](https://github.com/OJ/gobuster)
- [dirsearch](https://github.com/maurosoria/dirsearch)
- Burp Content Discovery
- Check for `robots.txt` disallowed

## Discover Links in JS Files
- [LinkFinder](https://github.com/GerbenJavado/LinkFinder)
- Burp Plugin: [JSLinkFinder](https://github.com/PortSwigger/js-link-finder)