# Subdomain Enumeration

## Domain Flyover 
- [Aquatone](https://github.com/michenriksen/aquatone)

## Subdomain Discovery
Don't forget to provide API keys!
- [SubFinder](https://github.com/projectdiscovery/subfinder) 
- [Asset Finder](https://github.com/tomnomnom/assetfinder)
- [Sublist3r](https://github.com/aboul3la/Sublist3r)
- [subbrute](https://github.com/TheRook/subbrute)
- [knock](https://github.com/guelfoweb/knock)
- [amass](https://github.com/caffix/amass)
  - Can record changes too
- [assets-from-spf](https://github.com/yamakira/assets-from-spf)
- [domains-from-csp](https://github.com/yamakira/domains-from-csp)
- [SAN Subdomain Enum](https://github.com/appsecco/the-art-of-subdomain-enumeration/blob/master/san_subdomain_enum.py)
- [github-subdomains.py](https://github.com/gwen001/github-search/blob/master/github-subdomains.py)
- [shosubgo](https://github.com/incogbyte/shosubgo)

- Data Sites:
  - certspotter.com
  - [threatcrowd passive JSON API](https://www.google.com/url?q=http://threatcrowd.org/searchApi/v2/domain/report/?domain%3Duber.com&sa=D&ust=1600897250701000&usg=AFQjCNFJMj85pVUecp4UQA5bZj722GQlUw)
  - censys.io [tool](https://github.com/appsecco/bugcrowd-levelup-subdomain-enumeration/blob/master/subdomain_enum_censys.py)
  - crt.sh [tool](https://github.com/appsecco/bugcrowd-levelup-subdomain-enumeration/blob/master/subdomain_enum_crtsh.py)
  - google [certificate transparency](https://transparencyreport.google.com/https/certificates)
  - cloudflare [tool](https://github.com/appsecco/the-art-of-subdomain-enumeration/blob/master/cloudflare_subdomain_enum.py)

## Subdomain Name Permutation Generation
- [DNSgen](https://github.com/ProjectAnte/dnsgen)

## Link Spidering to Find Domains
- [GoSpider](https://github.com/jaeles-project/gospider)
- [subdomainizer](https://github.com/nsonaniya2010/SubDomainizer)
- [subscraper](https://github.com/m8r0wn/subscraper)

## Rapid 7 Project Sonar Database
Collects forward and reverse DNS records from scraping the web. Huge dataset available at [Project Sonar](https://opendata.rapid7.com/).

Use Cases:
- Useful for finding subdomains
- Can be used for mass subdomain takeover scanning

Related Tools:
- [DNSgrep](https://github.com/tomnomnom/dnsgrep) can be used to efficiently parse and search this dataset using binary search

## DNSEC/NSEC/NSEC3 Walking
- NSEC dumping: `dig +short NSEC <target_domain> | awk '{print $1;}'`
- [nsec3walker](https://dnscurve.org/nsec3walker.html)
- [nsec3map](https://github.com/anonion0/nsec3map)
- NSEC [walker](https://github.com/hnw/go-dnssec-walker)

## DNS Zone Transfer
- Using dig: `dig AXFR @ns1.iitk.ac.in. iitk.ac.in`

## DNS Record Enumeration
- [massdns](https://github.com/blechschmidt/massdns)
- [shuffledns](https://github.com/projectdiscovery/shuffledns) wrapper for massdns