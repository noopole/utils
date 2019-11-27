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

## PostgreSQL

### Localiser les fichiers de base de donées

`# ps aux | grep postgres | grep -- -D`

ou 

`postgres=# show data_directory ;`

