# Informations utiles


## Vérifier une connexion réseau

### Utilitaires 

nc, nmap, nping

### Bash

#### Commande
**>/dev/tcp/{serveur}/{port}**

#### Exemple 
`# (echo >/dev/tcp/www.yahoo.fr/80) &>/dev/null && echo "OK" || echo "Refusé"`


## Lister les fichiers

`# alias ll=ls -l --color --time-style=long-iso -G -h $*`

Liste détaillée :
- en couleur, 
- avec les dates au format ISA, 
- sans le nom du groupe,
- avec la taille abrégée : K / M / G,
- avec prise en compte de paramètres supplémentaires.


