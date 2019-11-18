[![License](https://img.shields.io/badge/license-GPLv3-green.svg)](https://raw.githubusercontent.com/urbanadventurer/whatweb/master/LICENSE) [![made-with-bash](https://img.shields.io/badge/Made%20with-Bash-1f425f.svg)](https://www.gnu.org/software/bash/)

# Bing-ip2hosts

Bing-ip2hosts is a Bing.com web scraper to discover hostnames by IP address.

## Description

Bing-ip2hosts is a Bing.com web scraper that discovers hostnames by IP address. Bing is the flagship Microsoft search engine formerly known as MSN Search and Live Search. 

> It provides a feature unique to search engines - it allows searching by IP address. Bing-ip2hosts uses this feature.

It can be used to discover subdomains and other related domains. It also helps to identify websites hosted in a shared hosting environment. This technique follows best practices during the reconnaissance phase of a penetration test or bug bounty, to expand the target's attack surface.

Unlike other many other recon tools that web scrape Bing, this tool has smart scraping behaviour to maximize the discovery of hostnames.

### Features

- Smart scraping behaviour to maximize hostname discovery.
- Console user interface showing scraping progress.
- Discovers subdomains and hostnames by IP address.
- Can search by hostname or IP address.
- Output with or without URL prefix.
- Output to file, in list or CSV format.
- Bing API key not required.
- Select the search language and market.
- Specify targets from the commandline or from a file.
- Lightweight Bash shell script without heavy dependencies.


## Bing Web Scraping

Bing provides a feature unique to search engines - it allows searching by IP address. To try this, go to Bing.com and search for `IP:40.113.200.201`. It should show you results from microsoft.com. If it shows empty results, then add a single dot.

### Smart Scraping Behaviour

Unlike other Bing web scrapers that stop after scraping 10 result pages, bing-ip2hosts can scrape thousands of results. It continues scraping search result pages until it no longer finds new results. 

Scraping completes when any of the following conditions are met:
- After a configurable threshold of pages fail to return new results (default: 5).
- A single page of search results, e.g. 10 or less results.
- The last page of search results.
- Empty results.

It also alerts the user when Bing reports that some results have been removed.

### Avoid Empty Search Results

If searching by an IP address returns empty search results, add a single dot. Bing-ip2hosts always appends a single dot (%2e) to the query to avoid this issue.

### Search Language and Market

By default this tool specifies the search langauge as "en-us". The market is left as unset, as this seems to maximize results. 

The following URL parameters can be configured:
- setlang (Language)
- setmkt (Market code)

Both these parameters can affect how many results are returned.

A full list of market codes can be found at [docs.microsoft.com/en-us/azure/cognitive-services/bing-web-search/language-support](https://docs.microsoft.com/en-us/azure/cognitive-services/bing-web-search/language-support).

### Repeating Search Result Pages

Sometimes Bing does not permit the user to reach the end of search result pages.

For example, in a search that shows 3 pages of results, it will not always allow the user to reach the 3rd page. Instead it will return the first page of results. This can be demonstrated by searching for `ip:8.8.8.8 .`. Note that it is not always the first page that it returned to.

## Help

Use the following command for usage information.

```
bing-ip2hosts is a Bing.com web scraper that discovers websites by IP address.
Use for OSINT and discovering attack-surface of penetration test targets.

Usage: ./bing-ip2hosts [OPTIONS] IP|hostname

OPTIONS are:
-o FILE	Output hostnames to FILE.
-i FILE	Input list of IP addresses or hostnames from FILE.
-n NUM	Stop after NUM scraped pages return no new results (Default: 5).
-l	Select the language for use in the setlang parameter (Default: en-us).
-m	Select the market for use in the setmkt parameter (Default is unset).
-u	Only display hostnames. Default is to include URL prefixes.
-c	CSV output. Outputs the IP and hostname on each line, separated by a comma.
-q	Quiet. Disable output except for final results.
-t DIR	Use this directory instead of /tmp.
-V	Display the version number of bing-ip2hosts and exit.
```

## Installation

### Dependencies

bing-ip2hosts requires wget. This is installed by default in Ubuntu Linux and Kali Linux.

It can be installed in macOS with homebrew. 
```sh
homebrew install wget
```

It can be installed in Debian and Ubuntu Linux with apt. 
```sh
sudo apt install wget
```


### Install

Copy bing-ip2hosts into a folder in your $PATH. 
```sh
sudo cp ./bing-ip2hosts /usr/local/bin/
```

## Compatibility

Bing-ip2hosts uses the Bash scripting language.

It is known to work with the following systems.

* Ubuntu Linux

```
GNU bash, version 4.4.20(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

* macOS Catalina

The version of Bash bundled with macOS was published in 2007 and is the most recent version licenced with GPLv2. More recent versions are licenced with GPLv3, with licence terms that preclude Apple from bundling it in macOS.

```
GNU bash, version 3.2.57(1)-release (x86_64-apple-darwin19)
Copyright (C) 2007 Free Software Foundation, Inc.
```

## Links

- Homepage: http://www.morningstarsecurity.com/research/bing-ip2hosts/
- Source: https://github.com/urbanadventurer/bing-ip2hosts
- Kali Linux Tools: https://tools.kali.org/information-gathering/bing-ip2hosts
- Kali Linux Package: https://gitlab.com/kalilinux/packages/bing-ip2hosts/tree/kali/master
- Homebrew Kali: https://github.com/b-ramsey/homebrew-kali
- ArchLinux Package: https://aur.archlinux.org/packages/bing-ip2hosts/
- ArchStrike : https://archstrike.org/packages/bing-ip2hosts
- BlackArch : https://blackarch.org/recon.html


## Related Projects

Here's a list of projects that also search Bing by IP address.
- [HostHunter](https://github.com/SpiderLabs/HostHunter/) by SpiderLabs

Here's a list of other related projects for recon using Bing. Note that these do not search Bing by IP address.
- [Sublist3r](https://github.com/aboul3la/Sublist3r/) by aboul3la 
- [recon-ng](https://github.com/lanmaster53/recon-ng) by lanmaster53 


## Author

Copyright Andrew Horton, aka urbanadventurer.


## Licensing

This project is licensed under GPL version 3. See the attached `LICENSE.txt`.


## Contributing

If you have any ideas, just open an issue and tell me what you think.

If you'd like to contribute, please fork the repository and make changes as you'd like. Pull requests are warmly welcome.


## Acknowledgments

This project uses:
- [bash](https://www.gnu.org/software/bash/)
- [wget](https://www.gnu.org/software/wget/)
- [grep](https://www.gnu.org/software/grep/)
- [sed](https://www.gnu.org/software/sed/)
