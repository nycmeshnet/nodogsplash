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
scp nodogsplash.conf root@172.30.22.1:/etc/nodogsplash/nodogsplash.conf
```

With ssh, enable and start the splash
```
/etc/init.d/nodogsplash enable
/etc/init.d/nodogsplash start
```

Connect to the router by wifi and you should now get the splash. Different OS's handle splash screens differently. In Android it appears in the message center. If the splash appears in the browser it will take you to nycmesh.net when you click on it.


The config file only has one change at the moment. It is just a bit faster to copy the file rather than edit it. If you want to edit then here is the change:

```
# If RedirectURL is set, the user is redirected to this URL instead.
# 
RedirectURL http://nycmesh.net/
```
