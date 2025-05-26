### Internet connection
I encountered a problem with the internet connection with waydroid when docker is installed. One solution that has worked for me is to change a line in waydroid-net.sh

```
/usr/lib/waydroid/data/scripts/waydroid-net.sh
```
Change the line
```
LXC_USE_NFT="true"
```
to
```
LXC_USE_NFT="false"
```

This might need to be redone if waydroid is updated.

Remember to edit with a proper editor that will save it as a shell script.