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
*Coming soon*
