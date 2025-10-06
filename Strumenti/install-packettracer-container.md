# Come installare Cisco packet tracer su altre distro Linux senza installare Debian:

### Installazione di distrobox:
per fedora:
``` 
sudo dnf install -y distrobox 
``` 
per arch: 
``` 
sudo pacmand -S distrobox 
```
### Utilizzare distro box:
 crea il container: 
 ```
distrobox create -n ubuntu-packettracer-scuola --image ubuntu:22.04
```
 entra nel container: 
 ```
distrobox enter ubuntu-packettracer-scuola
```
 aggiorna il container:  
 ``` 
sudo apt update && sudo apt upgrade -y 
```
installa dipendenze:
```
 sudo apt install libqt5multimedia5 libqt5xml5 libqt5script5 libqt5scripttools5 libqt5sql5
```

### Packet tracer:
installa packet tracer:  

```
cd Scaricati // cartella dove hai scaricato il paccheto .deb di packet tracer
sudo apt install ./Cisco…deb
```

esegui packet tracer:

```
packettracer
```
esporta packet tracer dal container per trovarlo nell’os host: 
```
 distrobox-export --app packettracer
```

