![badge](https://img.shields.io/static/v1?label=Project&nbsp;OC&message=13&color=blueviolet&style=for-the-badge)
![badge](https://img.shields.io/static/v1?label=Status&message=in_progess&color=blue&style=for-the-badge)

# ocrp13-Lettings

Scale a Django Application Using Modular Architecture.

![Logo orange_county_lettings](./logos/orangecountylettings.png "Logo")

****
## Résumé

Site web d'Orange County Lettings

## Développement local

### Prérequis

- Compte GitHub avec accès en lecture à ce repository
- Git CLI
- SQLite3 CLI
- Interpréteur Python, version 3.6 ou supérieure

Dans le reste de la documentation sur le développement local, il est supposé que la commande `python` de votre 
OS shell exécute l'interpréteur Python ci-dessus (à moins qu'un environnement virtuel ne soit activé).

### macOS / Linux

#### Cloner le repository

- `cd /path/to/put/project/in`
- `git clone https://github.com/OpenClassrooms-Student-Center/Python-OC-Lettings-FR.git`

#### Créer l'environnement virtuel

- `cd /path/to/ocrp13-Lettings`
- `python -m venv venv`
- `apt-get install python3-venv` (Si l'étape précédente comporte des erreurs avec un paquet non trouvé sur Ubuntu)
- Activez l'environnement `source venv/bin/activate`
- Confirmez que la commande `python` exécute l'interpréteur Python dans l'environnement virtuel
`which python`
- Confirmez que la version de l'interpréteur Python est la version 3.6 ou supérieure `python --version`
- Confirmez que la commande `pip` exécute l'exécutable pip dans l'environnement virtuel, `which pip`
- Pour désactiver l'environnement, `deactivate`

#### Exécuter le site

- `cd /path/to/ocrp13-Lettings`
- `source venv/bin/activate`
- `pip install --requirement requirements.txt`
- `python manage.py runserver`
- Allez sur `http://localhost:8000/` dans un navigateur.
- Confirmez que le site fonctionne et qu'il est possible de naviguer (vous devriez voir plusieurs profils et locations).

#### Linting

- `cd /path/to/ocrp13-Lettings`
- `source venv/bin/activate`
- `flake8`

#### Tests unitaires

- `cd /path/to/ocrp13-Lettings`
- `source venv/bin/activate`
- `pytest -vs`

#### Base de données

- `cd /path/to/ocrp13-Lettings`
- Ouvrir une session shell `sqlite3`
- Se connecter à la base de données `.open oc-lettings-site.sqlite3`
- Afficher les tables dans la base de données `.tables`
- Afficher les colonnes dans le tableau des profils, `pragma table_info(oc_lettings_site_profile);`
- Lancer une requête sur la table des profils, `select user_id, favorite_city from 
oc_lettings_site_profile where favorite_city like 'B%';`
- `.quit` pour quitter

#### Panel d'administration

- Allez sur `http://localhost:8000/admin`
- Connectez-vous avec l'utilisateur `admin`, mot de passe `Abc1234!`

### Windows

Utilisation de PowerShell, comme ci-dessus sauf :

- Pour activer l'environnement virtuel, `.\venv\Scripts\Activate.ps1`
- Remplacez `which <my-command>` par `(Get-Command <my-command>).Path`

#### Déploiement

##### CircleCI :

Créez le contexte : `oc-lettings-context` puis ajoutez les variables suivantes :  
`DOCKERHUB_REPO`  
`DOCKERHUB_USERNAME`  
`DOCKERHUB_PASS`  

Lancement du site en local :  
Récupérez le nom de l'image générée par le dernier commit puis entrez la commande :  
`docker run -it -p 8000:8000 <nom de l'image>`

Le serveur sera accessible avec votre navigateur à l'adresse `http://localhost:8000/`
