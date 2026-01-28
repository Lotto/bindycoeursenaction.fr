# Bindy Coeurs en Action

Site web officiel de l'association Bindy Coeurs en Action, une association loi 1901 à but non lucratif.

## Mission

Organiser des événements solidaires (Koh-Lanta, Pékin Express) pour collecter des fonds au profit d'associations caritatives comme [Les Papillons](https://www.associationlespapillons.org/).

## Technologies

- **Jekyll** - Générateur de site statique
- **GitHub Pages** - Hébergement gratuit
- **HTML/CSS** - Design moderne et responsive

## Développement local

### Prérequis

- Ruby (version 2.7 ou supérieure)
- Bundler

### Installation

```bash
# Installer les dépendances
bundle install

# Lancer le serveur de développement
bundle exec jekyll serve

# Le site sera accessible sur http://localhost:4000
```

### Commandes utiles

```bash
# Build du site
bundle exec jekyll build

# Serveur avec rechargement automatique
bundle exec jekyll serve --livereload

# Mode développement avec brouillons
bundle exec jekyll serve --drafts
```

## Déploiement

Le site est automatiquement déployé sur GitHub Pages lors d'un push sur la branche `main`.

## Structure du projet

```
.
├── _config.yml          # Configuration Jekyll
├── _layouts/            # Templates HTML
│   └── default.html
├── index.html           # Page d'accueil
├── Gemfile              # Dépendances Ruby
└── README.md
```

## Licence

© 2025 Bindy Coeurs en Action - Tous droits réservés
