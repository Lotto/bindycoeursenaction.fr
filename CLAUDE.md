# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projet

Site web de l'association **Bindy Coeurs en Action**, association loi 1901 à but non lucratif qui organise des événements solidaires (Koh-Lanta, Pékin Express) pour collecter des fonds au profit d'associations caritatives comme Les Papillons.

## Technologies

- **Jekyll 4.3** - Générateur de site statique
- **GitHub Pages** - Hébergement
- **HTML/CSS** - Sans framework JavaScript

## Commandes de développement

```bash
# Installation des dépendances
bundle install

# Serveur de développement (http://localhost:4000)
bundle exec jekyll serve

# Serveur avec rechargement automatique
bundle exec jekyll serve --livereload

# Build du site (génère dans _site/)
bundle exec jekyll build

# Mode développement avec brouillons
bundle exec jekyll serve --drafts

# Nettoyer les fichiers générés
bundle exec jekyll clean
```

## Architecture

### Structure Jekyll

- `_config.yml` - Configuration globale (titre, URL, plugins)
- `_layouts/` - Templates HTML réutilisables
- `_includes/` - Composants HTML partiels (à créer si nécessaire)
- `index.html` - Page d'accueil (landing page)
- `_site/` - Dossier de build (généré automatiquement, ignoré par git)

### Front Matter YAML

Chaque page commence par un bloc YAML :
```yaml
---
layout: default
title: Page Title
---
```

### Variables Jekyll importantes

- `{{ site.title }}` - Titre du site (depuis _config.yml)
- `{{ site.description }}` - Description
- `{{ content }}` - Contenu de la page dans un layout
- `{{ page.title }}` - Titre de la page courante

## Déploiement GitHub Pages

Le site est automatiquement déployé lors d'un push sur `main`. GitHub Pages utilise Jekyll nativement.

### Configuration requise

Dans les paramètres du repo GitHub :
- Pages > Source : Deploy from a branch
- Branch : main / (root)

Le site sera accessible sur `https://bindycoeursenaction.fr` (après configuration DNS).

## Conventions

- **Langue** : Français (contenu et attributs `lang="fr"`)
- **Design** : Moderne, responsive, dégradés violets (#667eea, #764ba2)
- **Emoji** : Utiliser 🦋 comme symbole de l'association
- **Accessibilité** : Balises sémantiques HTML5, textes alternatifs

## Important

- Toujours tester localement avec `bundle exec jekyll serve` avant de commit
- Les modifications CSS inline dans `index.html` peuvent être déplacées vers un fichier CSS séparé si le site grandit
- Le fichier `Gemfile.lock` est ignoré pour permettre à GitHub Pages d'utiliser ses propres versions
