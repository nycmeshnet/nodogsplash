# nodogsplash

NYC Mesh splash page. Currently does not work with NanoStation NSM5XW!

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


The config file has two changes. It is just a bit faster to copy the file rather than edit it. If you want to edit then here are the changes:

```
# need to allow 10.x.x.x for the .mesh domains
#  FirewallRule block to 10.0.0.0/8
```
```
# If RedirectURL is set, the user is redirected to this URL instead.
# 
RedirectURL http://nycmesh.net/
```

There is a bug launching nodogsplash on startup in qMp. Nodogsplash will only launch correctly if it is started > 10 seconds after booting. To work around this you can edit the init file and add sleep 20 

```
start_service() {
	# NYC Mesh workaround- nodogsplash is not happy launching immediately at startup
	echo "   Sleep for 20 seconds"
	sleep 20

	if test_module ;  then
```
If you copy the init file make sure to chmod 755 (-rwxr-xr-x)
```
chmod 0755 /etc/init.d/nodogsplash
```



Nodogsplash package provides the ndsctl binary to manage it. Run ndsctl without arguments to see the help.

e.g. check status
root@openWrt:~# ndsctl status