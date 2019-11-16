[![License](https://img.shields.io/badge/license-GPLv2-green.svg)](https://raw.githubusercontent.com/urbanadventurer/whatweb/master/LICENSE)

bingip2hosts is a Bing.com web scraper that discovers websites by IP address.

INTRODUCTION
------------
Bing.com is a search engine owned by Microsoft, formerly known as MSN Search and Live Search. It has a unique feature to search for websites hosted on a specific IP address. This feature is can be used with the IP: parameter in the search query, eg. "IP:1.2.3.4"

Bing-ip2hosts uses this feature to enumerate all hostnames which Bing has indexed for a specific IP address. This technique is considered best practice during the reconnaissance phase of a penetration test in order to discover a larger potential attack surface. Bing-ip2hosts is written in the Bash scripting language for Linux.

HELP
-------
Use the following command for usage information.

```
bing-ip2hosts is a Bing.com web scraper that discovers websites by IP address.
Use for OSINT and discovering attack-surface of penetration test targets.

Find hostnames that share an IP address with your target which can be a hostname or an IP address.
This uses the Bing.com feature of seaching by IP address, e.g. "IP:40.112.72.205".

Usage: ./bing-ip2hosts [OPTIONS] IP|hostname

OPTIONS are:
-o FILE	Output hostnames to FILE.
-n NUM	Stop after NUM scraped pages return no new results (Default: 5).
-l	Select the language for use in the setlang parameter (Default: en-us).
-m	Select the market for use in the setmkt parameter (Default is unset).
-u	Only display hostnames. Default is to include URL prefixes.
-i	CSV output. Outputs the IP and hostname on each line, separated by a comma.
-q	Quiet. Disable output except for final results.
-t DIR	Use this directory instead of /tmp.
```

INSTALL
-------
sudo cp ./bing-ip2hosts /usr/local/bin/


KNOWN ISSUES
------------
* Will stop scraping pages when a CAPTCHA is presented by Bing

LINKS
-----
- Homepage: http://www.morningstarsecurity.com/research/bing-ip2hosts/
- Source: https://github.com/urbanadventurer/bing-ip2hosts
- Kali Linux Tools: https://tools.kali.org/information-gathering/bing-ip2hosts
