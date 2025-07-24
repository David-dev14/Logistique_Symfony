
#  Projet Logistique_Symfony

##  Présentation

**Logistique_Symfony** est une application web de gestion logistique développée avec le framework PHP **Symfony**.
 Elle permet de gérer les produits, commandes, utilisateurs et points de vente via une interface structurée et sécurisée,
 en suivant le modèle **MVC (Modèle-Vue-Contrôleur)**.

---

##  Pré-requis

| Outil           | Version recommandée         | Lien de téléchargement                                                                                                            |<br>
| PHP             | ≥ 8.1                       | [php.net/downloads](https://www.php.net/downloads.php)                                                                                            |<br>
| Composer        | Dernière version            | [getcomposer.org](https://getcomposer.org/download/)                                                                                              |<br>
| Symfony CLI     | Dernière version            | [symfony.com/download](https://symfony.com/download)                                                                                              |<br>
| Base de données | MySQL, PostgreSQL ou SQLite | [MySQL](https://dev.mysql.com/downloads/)
                                                  [PostgreSQL](https://www.postgresql.org/download/)
                                                  [SQLite](https://www.sqlite.org/download.html) 

###  Commandes d'installation par système :

pour pouvoir installer les techs de macOS. <br>besoin de<br>
homebrew : /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"<br>
faire export<br> PATH="/usr/local/bin:$PATH"

#### **PHP ≥ 8.1**

| Système     | Commande                                                                 |
| ----------- | ------------------------------------------------------------------------ |
| **Ubuntu**  | `sudo apt install php php-cli php-mbstring php-xml php-curl php-sqlite3`  |
| **macOS**   | `brew install php`                                                       |
| **Windows** | Télécharger depuis [php.net](https://windows.php.net/download)           |

Vous pouvez installer un serveur local tel que : xampp, lamp, mamp et wamp en fonction de votre systeme d'exploitation. sachant que xammp est valable pour tout systeme (liux, mac, windows)

pour installer composer, il faut se rendre sur le site : getcomposer.org

####  **Composer**

| Système     | Commande                                                                                   |
| ----------- | ------------------------------------------------------------------------------------------ |
| **Ubuntu**  | [instructions manuelles](https://getcomposer.org/download/)  |
| **macOS**   | `brew install composer`                                                                    |
| **Windows** | [Installer officiel](https://getcomposer.org/Composer-Setup.exe)                           |


#### **Symfony CLI**

| Système     | Commande ou lien                                                                              |                                                                     |
| ----------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Ubuntu**  | \`\`\`curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | <br> sudo -E bash
sudo apt install symfony-cli |
| **macOS**   | `brew install symfony-cli/tap/symfony-cli`                                                    |                                                                     |
| **Windows** | [Télécharger l’exécutable](https://github.com/symfony-cli/symfony-cli/releases/latest)        |                                                                     |

---
Sous Windows, vous pouvez utiliser **[Scoop](https://scoop.sh/)**, un gestionnaire de paquets en ligne de commande, pour installer Composer et d'autres outils comme PHP ou Symfony CLI de façon plus rapide et centralisée.
Installer Composer avec Scoop :

scoop install composer

https://scoop.sh/

Vous pouvez également installer PHP, Symfony CLI, Node.js, etc. via Scoop :

scoop install php <br>
scoop install symfony-cli


##  Installation du projet

### 1. **Cloner le dépôt**

```bash
git clone https://github.com/nom-utilisateur/Logistique_Symfony.git
cd Logistique_Symfony
```

### 2. **Installer les dépendances PHP**

```bash
composer install
```

### 3. **Configurer l’environnement**

Copiez le fichier `.env` en `.env.local` :

```bash
cp .env .env.local
```

Puis modifiez la variable `DATABASE_URL` pour correspondre à votre configuration locale.


```dotenv
DATABASE_URL="mysql://utilisateur:motdepasse@127.0.0.1:3306/nom_bdd?serverVersion=5.7&charset=utf8mb4"
```



### 4. **Créer et migrer la base de données**

## **Attention – Préparation de la base de données !**

Avant d’exécuter les commandes Doctrine ci-dessous, vous devez créer manuellement la base de données dans phpMyAdmin (ou via un outil SQL) en lui donnant exactement le même nom que celui configuré dans votre fichier .env.local (champ DATABASE_URL).

Cependant, ne créez aucun tableau (table) dans cette base : laissez-la vide, car ce sont les commandes Doctrine qui se chargeront de générer la structure (tables, colonnes, relations, etc.) à partir de vos entités PHP et fichiers de migration.

```bash
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```

### 5. **Lancer le serveur local Symfony**

```bash
symfony serve
```

Accédez ensuite à votre application sur : `http://127.0.0.1:8000`

---

##  Fonctionnalités principales

* Authentification (Symfony Security)
*  Gestion des utilisateurs
*  Gestion des produits
*  Panier & commandes
*  Téléversement de fichiers (VichUploaderBundle)
*  Génération de factures
*  Notifications email
*  Traduction multilingue

---

##  Technologies utilisées

* **Symfony** (PHP framework)
* **Doctrine ORM** (gestion base de données)
* **Twig** (moteur de template)
* **AssetMapper & Stimulus** (gestion JS moderne sans Webpack)
* **VichUploaderBundle** (upload de fichiers)
* **Symfony Mailer** (envoi d’e-mails)
* **PHPUnit** (tests unitaires)

---

## Bonnes pratiques

* Utilisation du **pattern MVC**
* Entités propres et annotées
* Routes centralisées
* Sécurité avec firewall et encodeur de mots de passe
* Utilisation d’un environnement `.env.local` pour l’adaptabilité

---

##  Commandes utiles

```bash
symfony server:start              # Lancer le serveur local
php bin/console make:controller  # Générer un nouveau contrôleur
php bin/console make:entity      # Créer une nouvelle entité
php bin/console make:migration   # Générer un fichier de migration
php bin/console doctrine:migrations:migrate # Appliquer les migrations
php bin/phpunit                  # Lancer les tests
```

---

## Tests

Les tests unitaires sont situés dans le dossier `/tests`. Ils utilisent **PHPUnit**.

```bash
php bin/phpunit
```

---

## Contribution

1. Forkez le projet
2. Créez une branche (`git checkout -b feature/NomFonction`)
3. Commitez vos modifications (`git commit -m "Ajout d'une fonctionnalité"`)
4. Pushez votre branche (`git push origin feature/NomFonction`)
5. Ouvrez une Pull Request

---



##  Structure du projet

```
├── assets/                 # Fichiers front-end (JS, CSS, images)
├── bin/                    # Fichiers exécutables (console Symfony, tests)
├── config/                 # Fichiers de configuration (services, sécurité, routes)
├── migrations/             # Fichiers de migration de base de données
├── public/                 # Racine web (index.php, images publiques)
├── sql/                    # Scripts SQL (initialisation, etc.)
├── src/                    # Code source principal (MVC)
│   ├── Controller/         # Contrôleurs HTTP
│   ├── Entity/             # Entités Doctrine (tables DB)
│   ├── Enum/               # Énumérations PHP
│   ├── Form/               # Formulaires Symfony
│   ├── Repository/         # Requêtes personnalisées Doctrine
│   ├── Security/           # Logique de sécurité (authentification, vérification)
│   └── Kernel.php          # Fichier principal de démarrage Symfony
├── templates/              # Vues Twig (HTML)
├── tests/                  # Tests unitaires
└── translations/           # Traductions i18n
```
## Licence

Projet open-source – Licence libre.




