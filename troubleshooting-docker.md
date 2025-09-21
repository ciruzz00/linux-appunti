# troubleshooting docker 

Errore:
```bash
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```
Controllo:
```bash
systemctl status docker
```
Se `active(running)` allora docker e attivo 
se `inactive o failed` devi avviarlo 

Soluzione:
```bash
sudo systemctl start docker
```
Oppure per avviarlo automaticamente:
```bash
sudo systemctl enable docker
```

Aggiungere l'utente al gruppo docker 
```bash
sudo usermod -aG docker $USER
```
