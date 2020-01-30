# Informations utiles


## Connexion via bastion

Connexion directe au serveur Linux

`# shh user_bation@serveur_bastion -t "sshclient root@serveur_cible"`

### Connexion à MobaXterm via Bastion à partir d'un lien Web sous Windows

Ajouter les clés dans la base de registre :

```
[Ordinateur\HKEY_CLASSES_ROOT\ssh]
  - (par default)   "URL:ssh Protocol"
  - URL Protocol    ""
[Ordinateur\HKEY_CLASSES_ROOT\ssh\shell\open]
  - FriendlyAppName "MobaXterm"
[Ordinateur\HKEY_CLASSES_ROOT\ssh\shell\open\command]
  - (par défaut)    "cmd /k "set arg=%1 && cmd /k C:\ssh\launch.bat""
```

Créer le fichier *launch.bat*:
```
set target=%arg:ssh:=%
echo connecting to %target%...
C:\mobaxterm\MobaXterm_Personal_12.4.exe -newtab "ssh -x 20012193@ubastion.adeo.com -t sshclient root@%target%"
```

---

## Vérifier une connexion réseau

### Utilitaires 

nc, nmap, nping

### Bash

#### Commande
**>/dev/tcp/{serveur}/{port}**

#### Exemple 
`# (echo >/dev/tcp/www.yahoo.fr/80) &>/dev/null && echo "OK" || echo "Refusé"`

____

## Lister les fichiers

`# alias ll=ls -l --color --time-style=long-iso -G -h $*`

Liste détaillée :
- en couleur, 
- avec les dates au format ISA, 
- sans le nom du groupe,
- avec la taille abrégée : K / M / G,
- avec prise en compte de paramètres supplémentaires.



----
## Filtrer

### Filtrer les lignes non commentées (par #)

`# cat file_name | grep ^[^#]`

----

## Identifier l'infrastructure

### Nombre de CPU

`# nproc`

### Quantité de mémoire RAM

`# dmidecode --type memory | grep Size | grep MB`

### Espace disques

`# df -h`

### OS distributation

```
# cat /etc/issue
# cat /etc/system-release
# cat /etc/redhat-release
# cat /etc/os-release
```

----

## Encodage

### URL Encode Base64

Sous Linux seulement !

`# echo -n "sercret_id:secret_password" | base64`

----

## Gestion des packages

### Commandes RPM

https://www.system-linux.eu/index.php?post/2008/12/21/Commande-rpm

----


## Oracle

### Trouver les instances

`# cat /etc/oratab`

ou alors (seulement les instance actives) :

`# ps -fe | grep pmon`

### Connexion a une instance

```
# su - [oracleuser]
# . oraenv
# rlwrap sqlplus / as sysdba
```

### Lister les schémas

`sql> select username from sys.all_users`

### Connexion à un schéma

`sql> connect [owner]`

### Lister les tables

`sql> select table_name from sys.all_tables where owner = '[owner]';`


### Relancer une base de données dans un état _idle_

`sql> STARTUP`

### Relancer le listerner (pour accès via TCP 1521)

```
# su - [oracleuser]
# lsnrctl start
# lsnrctl stop
# lsnrctl status
```

----

## PostgreSQL

### Localiser les fichiers de base de donées

`# ps aux | grep postgres | grep -- -D`

ou 

`postgres=# show data_directory ;`

### Lister les de bases de donées avec leur taille

`postgres=# \l+`

### Effectuer un dump 

`postgres$ pg_dump [base] > path/dump/[base].dmp`


