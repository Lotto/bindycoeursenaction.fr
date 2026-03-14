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

**Note** : Le build local peut échouer à cause de conflits de gems (github-pages vs jekyll 4.3). Le build se fait sur GitHub Pages directement lors du push sur `main`.

## Architecture

### Structure Jekyll

- `_config.yml` - Configuration globale (titre, URL, plugins)
- `_layouts/default.html` - Layout principal (head, body, SEO, favicon)
- `_includes/` - Composants HTML partiels réutilisables
- `index.html` - Page d'accueil (landing page)
- `aventure-solidaire-rouen-2026.html` - Page dédiée premier événement
- `_site/` - Dossier de build (généré automatiquement, ignoré par git)

### Includes (composants partagés)

- `_includes/navbar.html` - HTML de la navigation (logo, liens, hamburger, overlay)
- `_includes/navbar-styles.html` - CSS navbar, dropdown, hamburger, mobile menu
- `_includes/navbar-script.html` - JS menu mobile (toggleMenu, closeMenu, toggleDropdownMobile)
- `_includes/footer.html` - HTML du footer (3 colonnes : asso, navigation, contact)
- `_includes/footer-styles.html` - CSS du footer

### Comment ajouter une page

1. Créer `ma-page.html` à la racine avec front matter (`layout: default`, `title`, `permalink`)
2. Inclure les styles : `{% include navbar-styles.html %}` et `{% include footer-styles.html %}` dans le `<style>`
3. Inclure les composants : `{% include navbar.html %}` et `{% include footer.html %}` dans le HTML
4. Inclure le script : `{% include navbar-script.html %}` en fin de page
5. Ajouter le lien dans `_includes/navbar.html` (dropdown) et `_includes/footer.html`

### Front Matter YAML

Chaque page commence par un bloc YAML :
```yaml
---
layout: default
title: Page Title
permalink: /url-de-la-page
---
```

### Variables Jekyll importantes

- `{{ site.title }}` - Titre du site (depuis _config.yml)
- `{{ site.description }}` - Description
- `{{ content }}` - Contenu de la page dans un layout
- `{{ page.title }}` - Titre de la page courante
- `{{ site.baseurl }}` - Préfixe URL (vide pour ce site)

## Déploiement GitHub Pages

Le site est automatiquement déployé lors d'un push sur `main`. GitHub Pages utilise Jekyll nativement.

### Configuration requise

Dans les paramètres du repo GitHub :
- Pages > Source : Deploy from a branch
- Branch : main / (root)

Le site est accessible sur `https://bindycoeursenaction.fr`.

## Conventions

- **Langue** : Français (contenu et attributs `lang="fr"`)
- **Design** : Moderne, responsive, dégradés violets/turquoise (#667eea, #7c3aed, #06b6d4)
- **Emoji** : Utiliser ❤️ comme symbole de l'association
- **Accessibilité** : Balises sémantiques HTML5, textes alternatifs
- **Liens internes** : Toujours utiliser `{{ site.baseurl }}/` pour les liens entre pages
- **Menu mobile** : Hamburger menu avec panneau latéral droit, géré par JS dans navbar-script.html
- **Bandeaux d'annonce** : Positionnés sous la navbar (top: 65px), z-index: 999

## Pages existantes

| Page | Fichier | URL |
|------|---------|-----|
| Accueil | `index.html` | `/` |
| Événement Rouen 2026 | `aventure-solidaire-rouen-2026.html` | `/aventure-solidaire-rouen-2026` |

## Important

- Le build local peut échouer (conflits gems) — tester via push sur GitHub Pages
- Le fichier `Gemfile.lock` est ignoré pour permettre à GitHub Pages d'utiliser ses propres versions
- Les styles CSS sont inline dans chaque page, les styles partagés sont dans les includes
- Pour modifier le menu ou le footer : éditer les fichiers dans `_includes/` (une seule fois pour toutes les pages)
