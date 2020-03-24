# Webservers

## Apache Recon - Basics
This exercise focused on enumerating the Web service on the target server. I used the following to "cut to the chase" and pull some version information:

```
nmap 192.168.x.x -p80 -Pn -sV
```

That gave me the Apache version.  The next challenge was to figure out what bot was specifically disallowed from browsing the site.  From past experience I knew `robots.txt` was the file that contains this information, so I used `curl` to pull that file:

```
curl http://192.168.x.x/robots.txt
```

Looking through the  `User-agent` field identifies the naughty user agent.

## Apache Recon: Dictionary Attack
This exercise was about detecting the Apache version running on a host (which can be gleaned with `nmap -sV`) and then using command line tools to enumerate directories with various levels of protection.

With msfconsole, the `auxiliary/scanner/http/brute_dirs` tools is great at discovering content, and then `auxiliary/scanner/http/http_login` helps brute force user/pass combinations to protected directories.

Also, using `wget --user username --password password http://1.2.3.4/protected-dir` to validate creds and pull down the content behind the authentication protection.

## Nginx Recon: Basics
*Left off here*
