# FlashNet75

Site WordPress complet avec constructeur de pages visuel, gestion de formulaires et création de sliders.

## Aperçu

FlashNet75 est une installation WordPress 6.6.2 configurée pour la gestion de contenu web. Elle intègre un ensemble de plugins professionnels permettant la création de pages visuelles, de formulaires avancés et de sliders interactifs.

## Stack technique

| Composant | Technologie |
|-----------|------------|
| CMS | WordPress 6.6.2 |
| Langage serveur | PHP 7.2.24+ (recommandé 7.4+) |
| Base de données | MySQL 5.5.5+ ou MariaDB 10.5+ |
| Serveur web | Apache (mod_rewrite requis) |

## Prérequis

- PHP >= 7.2.24 (7.4+ recommandé)
- MySQL >= 5.5.5 ou MariaDB >= 10.5
- Apache avec le module `mod_rewrite` activé
- HTTPS recommandé en production

## Installation

### 1. Cloner le dépôt

```bash
git clone <url-du-depot> flashNet75
```

### 2. Créer la base de données

```sql
CREATE DATABASE FlashNet75 CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'votre_utilisateur'@'localhost' IDENTIFIED BY 'votre_mot_de_passe';
GRANT ALL PRIVILEGES ON FlashNet75.* TO 'votre_utilisateur'@'localhost';
FLUSH PRIVILEGES;
```

### 3. Configurer WordPress

Copiez le fichier de configuration exemple et éditez-le :

```bash
cp wp-config-sample.php wp-config.php
```

Modifiez les valeurs suivantes dans `wp-config.php` :

```php
define( 'DB_NAME', 'FlashNet75' );
define( 'DB_USER', 'votre_utilisateur' );
define( 'DB_PASSWORD', 'votre_mot_de_passe' );
define( 'DB_HOST', 'localhost' );
```

Générez des clés de sécurité uniques via [https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/) et remplacez les valeurs correspondantes dans `wp-config.php`.

### 4. Finaliser l'installation

Accédez à votre site dans un navigateur et suivez l'assistant d'installation :

```
http://localhost/flashNet75/wp-admin/install.php
```

## Structure du projet

```
flashNet75/
├── index.php               # Point d'entrée frontend
├── wp-config.php           # Configuration (DB, clés, debug)
├── wp-config-sample.php    # Modèle de configuration
├── .htaccess               # Réécriture d'URL Apache
│
├── wp-admin/               # Interface d'administration
├── wp-includes/            # Bibliothèques core WordPress
│
└── wp-content/
    ├── plugins/            # Extensions installées
    ├── themes/             # Thèmes installés
    ├── uploads/            # Médias téléversés
    └── languages/          # Fichiers de traduction
```

## Plugins installés

| Plugin | Version | Rôle |
|--------|---------|------|
| Elementor Website Builder | 3.24.7 | Constructeur de pages drag-and-drop |
| Elementor Header & Footer Builder | 1.6.44 | En-têtes et pieds de page personnalisés |
| Formidable Forms | 6.15 | Formulaires avancés, sondages, quiz |
| Depicter Slider & Popup Builder | 3.5.1 | Sliders, carrousels et popups |
| Akismet Anti-spam | 5.3.3 | Protection contre le spam |

## Thèmes installés

| Thème | Description |
|-------|-------------|
| **Neve** (actif) | Thème léger et polyvalent, optimisé pour Elementor |
| **Twenty Twenty-Four** | Thème officiel WordPress avec support de l'éditeur de blocs |

## Points d'accès

| URL | Description |
|-----|-------------|
| `/` | Site public |
| `/wp-admin/` | Tableau de bord administrateur |
| `/wp-login.php` | Page de connexion |

## Configuration avancée

### Activer le mode debug (développement uniquement)

Dans `wp-config.php` :

```php
define( 'WP_DEBUG', true );
define( 'WP_DEBUG_LOG', true );
define( 'WP_DEBUG_DISPLAY', false );
```

### WP-CLI (optionnel)

WP-CLI permet de gérer WordPress en ligne de commande :

```bash
# Mettre à jour WordPress
wp core update

# Mettre à jour tous les plugins
wp plugin update --all

# Vider le cache
wp cache flush

# Exporter la base de données
wp db export backup.sql
```

## Mise à jour

### Mise à jour automatique

- Connectez-vous à l'administration WordPress.
- Allez dans **Tableau de bord > Mises à jour**.
- Suivez les instructions.

### Mise à jour manuelle

1. Sauvegardez vos fichiers et votre base de données.
2. Supprimez les anciens fichiers WordPress, en conservant `wp-content/` et `wp-config.php`.
3. Téléversez les nouveaux fichiers.
4. Ouvrez `http://votre-site/wp-admin/upgrade.php`.

## Sécurité en production

- Remplacer le mot de passe de base de données vide (configuré pour le dev local)
- Activer HTTPS avec un certificat SSL valide
- Désactiver `WP_DEBUG`
- Protéger `wp-config.php` avec les permissions appropriées (chmod 600)
- Désactiver XML-RPC si non utilisé (`xmlrpc.php`)

## Support

- [Documentation officielle WordPress](https://wordpress.org/documentation/)
- [Forums de support WordPress](https://wordpress.org/support/)
- [Documentation Elementor](https://elementor.com/help/)
- [Documentation Formidable Forms](https://formidableforms.com/knowledgebase/)

## Licence

WordPress est distribué sous licence [GNU General Public License v2](license.txt) ou ultérieure.
