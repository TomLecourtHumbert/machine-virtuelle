# SAE3 - Installation
## Auteur(s)
LECOURT HUMBERT Tom / FRANCHOT Logan

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

Le fonctionnement de la configuration d'apache2 : possède des répertoires
contenant les fichiers activés, stockés par type incluants "sites", "conf"
et "mods".

a2enmod est un script qui active des modules dans la configuration d'apache2,
donc cela va créer des liens système dans le dossier "mods-enabled".

Grâce à vim on arrive à créer bienvenue.html, pour le sauvegarder on fait:
Echap + Maj + ZZ
(Echap + ZQ pour quitter sans sauvegarder)

Pour la suite nous avons suivi les indications de l'énoncé.

sudo systemctl status apache2   -->   Affiche le status d'Apache2