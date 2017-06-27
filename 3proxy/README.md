Put config to ~/3proxy.cfg with smth like that:
```
#!/usr/local/bin/3proxy
nserver 8.8.8.8
nserver 8.8.4.4
nscache 65536
timeouts 1 5 30 60 180 1800 15 60
log /dev/stdout
logformat "L%d-%m-%Y %H:%M:%S %z %N.%p %E %U %C:%c %R:%r %O %I %h %T"
users top4ek:CL:gjcjcbgbgbcrehry
auth strong
allow top4ek
maxconn 100
socks -p27005
```

And run container like
`docker run -d --name 3proxy --restart=unless-stopped -v ~/3proxy.cfg:/etc/3proxy.cfg -p 27005:27005 top4ek/3proxy`

Default configuration opens 27005 for everyone
