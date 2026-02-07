# Installation de GLPI sur Debian 11

##  Objectif
Ce document décrit l’installation de **GLPI 10.0.6** sur un serveur **Debian 11**, dans un contexte de support informatique professionnel.
L’objectif est de disposer d’un outil de gestion des tickets fonctionnel et prêt à être configuré pour un workflow de support IT **(N1/N2)**.


## Environnement utilisé

- OS : Debian 11 (Bullseye)
- Serveur Web : Apache 2.4
- PHP : 7.4
- Base de données : MariaDB
- GLPI : 10.0.6
- Accès : Navigateur web (client)

## Installation des prérequis
#### Mise à jour du système

``` bash 
 apt update && apt upgrade -y
```

#### Installation d’Apache, PHP et MariaDB
```bash
apt install -y apache2 mariadb-server mariadb-client php php-cli php-fpm php-mysql php-gd php-curl php-xml php-mbstring php-ldap php-zip php-intl php-bcmath php-imap
```
#### Vérification des services
```bash
systemctl status apache2 
systemctl status mariadb
```
#### Sécurisation de MariaDB
```bash
mysql_secure_installation 
```
Recommandé : mot de passe root, suppression des utilisateurs anonymes, désactivation de l’accès distant root  

#### Création database GLPI
```bash
mysql -u root -p
```
```sql
CREATE DATABASE glpidb;
CREATE USER 'glpiuser'@'localhost' IDENTIFIED BY 'àdéfinir!';
GRANT ALL PRIVILEGES ON glpidb.* TO 'glpiuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

#### Téléchargement et installation de GLPI
```bash
cd /tmp
wget https://github.com/glpi-project/glpi/releases/download/10.0.6/glpi-10.0.6.tgz
```
#### Décompression et déplacement
```bash
tar -xvzf glpi-10.0.6.tgz
mv glpi /var/www/html/
```
#### Permissions et sécurité
```bash
chown -R www-data:www-data /var/www/html/glpi
chmod -R 755 /var/www/html/glpi
```
#### Configuration Apache
##### Créer un VirtualHost GLPI

```bash 
nano /etc/apache2/sites-available/glpi.conf
```
#### Modifier le fichier glpi.conf
```apache
<VirtualHost *:80>
    ServerName support.localdomain.lan
    DocumentRoot /var/www/html/glpi

    <Directory /var/www/html/glpi>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/glpi_error.log
    CustomLog ${APACHE_LOG_DIR}/glpi_access.log combined
</VirtualHost>
```
#### Activation du site et des modules
```bash
a2ensite glpi.conf
a2enmod rewrite
systemctl reload apache2
```
#### Désactiver le site par défaut d'Apache

```bash
a2dissite 000-default.conf
```
#### Installation via l’interface Web
1. Ouvrir un navigateur :
```arduino
http://<IP_SERVEUR>/glpi
```
1. Choisir la langue
1. Accepter la licence
1. Sélectionner Installation
1. Renseigner :
    - Serveur DB : localhost
    - Base : glpidb
    - Utilisateur : glpiuser
    - Mot de passe : celui défini
1. Finaliser l’installation
1. Sécurisation post-installation
```bash
rm -rf /var/www/html/glpi/install
```  

#### Activation d'un certificat auto-signé
````bash
# Générer clé privée et certificat
openssl req -x509 -newkey rsa:4096 -keyout /etc/ssl/private/autosign.key -out /etc/ssl/certs/autosign.crt -days 365 -nodes

# Donner les bonnes permissions
chmod 600 /etc/ssl/private/autosign.key
````  

####  Installer le certificat comme CA de confiance
```bash
# Copier dans le magasin de certificats système
cp /etc/ssl/certs/autosign.crt /usr/local/share/ca-certificates/

# Mettre à jour la base de données
update-ca-certificates
```  

#### Vérifier l'installation
```bash
# Lister tous les certificats
ls -la /etc/ssl/certs/

# Vérifier si votre certificat est présent
openssl x509 -in /etc/ssl/certs/autosign.pem -text -noout
```  

#### Accès par défaut
```arduino
http://<IP_SERVEUR>/glpi
```
    
Compte administrateur par défaut :  
        - Utilisateur : glpi  
        - Mot de passe : glpi  
À changer immédiatement après la première connexion.
