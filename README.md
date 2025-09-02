# Outil de gestion de tâche
### Sommaire
1) Introduction du projet
2) Présentation des fonctionnalitées qui seront disponibles
3) Présentation des moyens d'installations
4) Date de mise à jour & Mise en place des mises à jours automatiques
5) Technologies utilisées

### 1) Introduction du projet
Le projet d'Outils de gestion de tâche à pris vie à la suite d'un cours et à la suite de la diffusion d'un besoin auprès de l'ensemble des élèves il y a de ça quelques année.
Il aura pour but d'aider une entreprise quelque soit sa grosseur et son niveau économique a aider ses salariés à la gestion et l'organisation des tâches qu'elles soit personnelles ou professionnelles.

L'outil est vérifié par le biais de l'outil SonarQube auquel on a ajouté le plugin WASP afin d'effectuer des auto-actualisation sur ce github et une vérification des failles de sécurité les plus connus.

### 2) Présentation des fonctionnalitées qui seront disponibles
Les fonctionnalitées qui pourront être disponibles d'ici quelques mois seront les suivants :
- Connexion employée
- Ajout de tâches & rappels des tâches aux heures données
- Outils d'administration par le biais d'applications et via un compte administrateur
- Disponibilité via le réseau interne (Aucune connexion vers la connexion internet sauf si besoin)
- Contacter son administrateur

Concernant les fonctionnalitées de l'administrateur
- L'ajout de compte
- La modification du logo mis en place sur le site
- La suppression de compte
- La réinitialisation de mot de passe
- Lancement des mises à jours

### 3) Présentation du moyen d'installation
Pour l'installation de mon outil il existe deux moyens.
#### a) Installation via conteneur Docker
L'installation  via le docker en quelques étapes :
1) Récupérer l'image **.TAR** depuis la page release de ce **repository uniquement**
2) Installer l'image sur votre docker via les commandes suivantes 
```
docker load < /home/username/Downloads/tasktool.tar
docker images
```
En écrivant la commande `docker images` veuillez vérifier qu'il existe bien une image.
3) Lancer le conteneur docker
   ```
   docker run -d -p 9998:80 --name gestion tasktool
```
5) Se rendre sur le site
   Se rendre sur l'IP de la machine suivit du port 9998  
   `http://IP_DE_VOTRE_MACHINE:9998`
#### b) Installation via le ZIP délivré dans les release
Prérequis: avoir executé le fichier `preinstall.sh` dans le release
1) Télécharger le fichier `tasktool-stable.zip` depuis ce **repository seulement**
2) Le mettre dans le répertoire Apache
3) Accorder les droits  
   ```
   sudo chown -r www-data:www-data /var/www/html
   ```
5) Se rendre sur l'IP de la machine

### 4) Date de mise à jour & Mise en place des mises à jours automatiques
Les mises à jours seront mentionnées dans cette section avec un les 5 derniers caractères du `sha256sum`, celui-ci vérifiant la conformité des fichiers composant l'outils  
Concernant les mises à jours automatiques, elles devront être activé manuellement via l'outil d'administration, celui-ci à des heure fixes récuperera les patchnotes et les ajoutera automatiquement dans les fichiers du projet.  
Cependant, les mises à jours importantes devront faire l'objet d'un réinstallation totale (souvent causé par une faille)

### 5) Technologies utilisées
Afin de pouvoir faire fonctionner notre outil et dans le cas où vous n'utilisez pas Docker, vous devrez installer et activé les outils suivants : 
- SQLite
- php8
- apache


  Les outils servant à la conformité du code quant à eux sont conservé en interne, toutes propositions est accepté à conditions qu'elle soit passée par la vérification d'un socle SonarQube armé du module WASP. Screenshot d'intégration obligatoire pour effectuer une pullrequest
