# Informations utiles


## Vérifier une connexion réseau

### Utilitaires 

nc, nmap, nping

### Bash

#### Commande
**>/dev/tcp/{serveur}/{port}**

#### Exemple 
`# (echo >/dev/tcp/www.yahoo.fr/80) &>/dev/null && echo "OK" || echo "Refusé"`
