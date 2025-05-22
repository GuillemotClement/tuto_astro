# Tuto Astro

## 👨🏻‍💻 Note

### Routing
Les fichiers Astro utilise l'extension `.astro`.

Le nomn du fichier correspond au path a passer.
Exemple : une page `about.astro` est accessible avec `http://localhost/about`

On utilise du HTML classique pour definir le contenu de la page.

`<a href="/about">` => pour declarer un nouveau lien et acceder a la page

### Blog

Astro facilite la creation d'une partie blog pour un site.

Le routing se base sur les dossier dans le folder `pages`. 

Par exemple, on peut creer un dossier `pages/posts`, et dans celui ci creer un ensemble de fichier qui correspond au differents arcticles de blog (`post-1.md`).


Chaque post est ensuite accessible via l'url `http://localhost/posts/post-1`.

Pour les blog, on utilise des fichiers en `.md`.

```md
---
title: 'Mon premier article de blog'
pubDate: 2022-07-01
description: "Il s'agit du premier article de mon nouveau blog Astro."
author: 'Apprenti Astro'
image:
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: "Le logo Astro sur un fond sombre avec une lueur rose."
tags: ["astro", "blogging", "apprentissage en public"]
---
# Mon premier article de blog

Publié le : 2022-07-01

Bienvenue sur mon _nouveau blog_ dédié à l'apprentissage d'Astro ! Ici, je vais partager mon parcours d'apprentissage en créant un nouveau site web.

## Ce que j'ai accompli

1. **Installation d'Astro** : Tout d'abord, j'ai créé un nouveau projet Astro et configuré mes comptes en ligne.

2. **Création de pages** : Ensuite, j'ai appris à créer des pages en créant de nouveaux fichiers `.astro` et en les plaçant dans le dossier `src/pages/`.

3. **Création d'articles de blog** : C'est mon premier article de blog ! J'ai maintenant des pages Astro et des articles en Markdown !

## Ce qui vient ensuite

Je vais terminer le tutoriel d'Astro, puis continuer à ajouter plus d'articles. Restez à l'écoute pour en savoir plus.
```
En haut du fichier, on retrouve des informations `frontmatter` qui permettent d'ajouter des metadonnees qui fournissent des informations a propos de l'article que Astro peut venir utiliser.



## 🧞 Commands

| Command                  | Action                                           |
|:-------------------------|:-------------------------------------------------|
| `npm create astro@latest` | Creation d'un nouveau projet                     |
|                          |                           |
| `npm run dev`            | Starts local dev server at `localhost:4321`      |
| `npm run build`          | Build your production site to `./dist/`          |
| `npm run preview`        | Preview your build locally, before deploying     |
| `npm run astro ...`      | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |








## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
/
├── public/
├── src/
│   └── pages/
│       └── index.astro
└── package.json
```
- `pages` : permet de declarer les differentes pages du site. Une page = un fichier.










Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.



All commands are run from the root of the project, from a terminal:




