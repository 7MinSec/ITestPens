# Memcached Recon Basics
In this exercise, I needed to retrieve the value of a flag dumped from a memcached server.  I started with an nmap ping sweep to find live hosts:

```
nmap 192.168.x.x/24 -sn
```

Once I found the live host that wasn't my gateway, I did a full port scan on it:

```
nmap 192.168.x.x -
```

That returned one port open on the target server: `11211`

From there I wanted to see what nmap scripts (relative to memcached) were available to run against the host.  But I didn't know where nmap was on the host so I tried to locate it with:

`locate nmap`

But the terminal gave me this nonsense:

```
locate: can not stat () `/var/lib/mlocate/mlocate.db': No such file or directory
```

So I updated the database with:

```
updatedb
```

Then ran the `locate` command again and found nmap and the accompanying scripts directory.  From that directory I listed all scripts that had `mem` in them with:

`ls *mem*`

And it returned one result:

```
memcached-info.nse
```
I ran the script against the target host with:

```
nmap 192.168.x.x -p11211 --script=memcached-info.nse
```

That gave me some info about the used CPU, uptime, current connections, etc.  But not the memory dump info I really wanted.  I loaded up Metasploit to see what other info I could glean from the server:

```
msfconsole
search memcached
use auxiliary/gather/memcached_extractor
```

I set the target with `set rhosts` and then ran the exploit with `run` to find the flag!
