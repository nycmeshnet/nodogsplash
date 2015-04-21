# nodogsplash

NYC Mesh splash page

The files live here on the router:

```
/etc/nodogsplash/htdocs/splash.html
/etc/nodogsplash/nodogsplash.conf
```

To install nodogsplash, ssh into the router and:
 
```
opkg update
opkg install --force-depends nodogsplash
```

"--force-depends" is needed to override the error warnings :-(

Copy the files from your computer to the router-
```
scp splash.html root@172.30.22.1:/etc/nodogsplash/htdocs/splash.html
scp nodogsplash.conf root@10.30.43.1:/etc/nodogsplash/nodogsplash.conf
```

With ssh, enable and start the splash
```
/etc/init.d/nodogsplash enable
/etc/init.d/nodogsplash start
```

The config file only has one change at the moment:
```
# If RedirectURL is set, the user is redirected to this URL instead.
# 
RedirectURL http://nycmesh.net/
```
