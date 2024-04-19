# SAE3 - Installation
## Auteur(s)
LECOURT HUMBERT Tom / FRANCHOT Logan

## 1. Gestion des services : systemd
man systemctl : On apprend que systemctl contrôle le systemd et le service
manager de la machine. Systemd forunit des composants système pour les
systèmes d'exploitation Linux et gère les dépendances entre services.
On peut aussi voir dans le manuel des unités (UNIT) avec des informations :
si ils sont lancés, si ils sont acitfs et son stade d'activation, ainsi que
sa description.
Quand on lance la commande systemctl, on a la même chose présentée dans le
manuel avec les différentes unités (UNIT) de la machine.

Le ssh fonctionne, il était déjà installé, ensuite si on stoppe le service
sshd on remarque qu'on ne peut plus se reconnecter (sudo systemctl stop ssh).
En le relançant on peut de nouveau se connecter.

## 2. Serveur Web apache2
### Installation de base du serveur
Le fonctionnement de la configuration d'apache2 : possède des répertoires
contenant les fichiers activés, stockés par type incluants "sites", "conf"
et "mods".

a2enmod est un script qui active des modules dans la configuration d'apache2,
donc cela va créer des liens système dans le dossier "mods-enabled".

Grâce à vim on arrive à créer bienvenue.html, pour le sauvegarder on fait:
Echap + Maj + ZZ
(Echap + ZQ pour quitter sans sauvegarder)

Utilisation de chmod avant acl (oublie de l'énoncé)

[sudo systemctl status apache2   -->   Affiche le status d'Apache2]

### Installation du serveur Web virtuel
nslookup --> nom DNS de la machine virtuelle (2a4v3-31uvm0413).
Création du répertoire mon_serveur (+ chmod temporaire dû à l'oubli de l'énoncé).
Documentation des lignes de commandes dans ~/history.txt

## 3. Serveur Web sécurisé https
Problème à l'énoncé : création d'un répertoire non souhaité, nous avons dû trouver la source du problème avec "sudo systemctl status apache2".
Aucun paquet n'était à installer.
Avec les indications de l'énoncé nous avons réussi à créer la connection HTTPS, le navigateur prévient que le serveur n'est pas forcément sûr, c'est une protection en plus qui marche.

## 4. Langage de programmation PHP
Installation php (sudo apt-get install php).
Installation libapache2-mod-php (sudo apt-get install libapache2-mod-php).
php -v pour connaître la version de php.
Puis création du fichier index.php (touch public_html/index.php).

## 5. Serveur de base de données MySQL
Mot de passe mysql admin : Bonjour01/
Mot de passe de mysqltest : Bonjour01@

Dans un premier temps : installation mysql-server et configuration (problème récurrent sur le mot de passe).
Création de l'utilisateur mysql avec les commandes données dans l'énoncé (voir historique mysql dans la machine virtuelle).

## 6. Outil d'administration de bases de données phpMyAdmin
Problème sur l'installation du paquet phpmyadmin --> aucun mot de passe ne marche donc initialisation sans mot de passe (codes d'erreur liés sur le serveur).
Activation du module mbstring (sudo phpenmod mbstring).
Redémarrage de apache2.
Connection avec mysql concluante.

## 7. Installation de la plateforme MediaWiki
Téléchargement de l'archive, installation du paquet unzip (sudo apt install unzip), extraction de l'archive dans le dossier mon_serveur et création de la base de données my_wiki comme dit dans l'énoncé.
Création de la base de données my_wiki et de wikiuser (voir phpMyAdmin).
Mot de passe wikiuser : database_wiki
Création du wiki, voir captures d'écran (mot de passe admin_wiki : admin_wiki)
Téléchargement de LocalSettings.php créé grâce à la création du wiki.
Recopiage de LocalSettings.php dans la machine virtuelle.
Relancement de "2a4v3-31uvm0413.ad-urca.univ-reims.fr/mediawiki-1.41.1",
le wiki marche !

## 2. Complément acl
Installation du paquet acl.
setfacl -m u:www-data:rx ~/mon_serveur
setfacl -m u:www-data:rx ~/public_html
setfacl -m u:www-data:rx ~/