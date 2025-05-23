# Tuto Astro

## 👨🏻‍💻 Note

### Routing
Les fichiers Astro utilisent l'extension `.astro`.

Le nom du fichier correspond au endpoint.

***Exemple : une page `about.astro` est accessible avec `http://localhost/about`***

On utilise du HTML classique pour definir le contenu de la page.

Pour definir un lien, on utilise la balise classique `<a href="/about">`

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

### Variables

On peut venir ajouter du JS dans le frontmatter d'un fichier astro.

Pour utiliser une variable : `{variable_name}`

On peut definir des variables TS ou JS.
```astro
---
// definition d'une variable
const pageTitle = "A propos de mois";
---

<html lang="en">
<head>
  <meta charset="utf-8" />
  <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
  <meta name="viewport" content="width=device-width" />
  <meta name="generator" content={Astro.generator} />
  // utilisation de la varaible
  <title>{pageTitle}</title>
</head>
<body>
<a href="/">Accueil</a>
<a href="/about/">À propos</a>
<a href="/blog/">Blog</a>
<h1>{pageTitle}</h1>
```

On peut utiliser n'importe quel expression JS (fonction, expression et operateurs logique)

```astro 
---
const pageTitle = "À propos de moi";

const identity = {
  firstName: "Sarah",
  country: "Canada",
  occupation: "Rédactrice technique",
  hobbies: ["photographie", "observation des oiseaux", "baseball"],
};

const skills = ["HTML", "CSS", "JavaScript", "React", "Astro", "Rédaction de documentation"];
---
```
On peut ensuite venir parcourir la liste dans le fichier 

```astro
<p>Voici quelques faits me concernant :</p>
<ul>
  <li>Je m'appelle {identity.firstName}.</li>
  <li>Je vis au {identity.country} et je travaille en tant que {identity.occupation}.</li>
  // on parcour la liste declarer dans le frontmatter
  {identity.hobbies.length >= 2 &&
    <li>Deux de mes loisirs sont : {identity.hobbies[0]} et {identity.hobbies[1]}</li>
  }
</ul>
<p>Voici mes compétences :</p>
<ul>
// on parcour la liste declarer dans le frontmatter
  {skills.map((skill) => <li>{skill}</li>)}
</ul>
```


### Affichage conditionnnelle

```astro
const happy = true;
const finished = false;
const goal = 3;
```

Ensuite dans le template :

```astro 
{happy && <p>Je suis heureux d'apprendre Astro !</p>}

{finished && <p>J'ai terminé ce tutoriel !</p>}

{goal === 3 ? <p>Mon objectif est de terminer en 3 jours.</p> : <p>Mon objectif n'est pas de 3 jours.</p>}
```






### CSS

Pour ajouter du css, on peut utiliser les balises `<style></style>`

Le style definis via les balises seront limiter a la page dans laquel on le declare.
```astro
<style>
  h1 {
    color: purple;
    font-size: 4rem;
  }
  .skill {
    color: green;
    font-weight: bold;
  }
</style>
```

Pour ajouter une classe
```astro
<p>Mes compétences sont :</p>
<ul>
  {skills.map((skill) => <li class="skill">{skill}</li>)}
</ul>
```

Les balises `<style>` peut egalement referencer des variables du Js provenant du frontmatter avec la directive `define:vars={ {...} }`
On peut definir ces variables dans le front matter et les utiliser dans la balise `<style>`

```astro
---
const skillColor = "navy";
---
```

On peut ensuite l'utiliser 

```astro 
<style define:vars={{skillColor}}>
  .skill {
    color: green;
    color: var(--skillColor);
    font-weight: bold;
  }
</style>
```

### Style globale

Pour definir un style global, on creer un fichier `global.css` que l'on vient ensuite importer dans les differentes pages.

On viens placer ce fichier dans `src/styles/global.css`.

Dans ce fichier, on declare les differentes styles que l'on souhaite appliquer au niveau global.

On viens ensuite importer ce fichier dans chacun de nos fichiers 

```astro
---
import '../styles/global.css';
---
```

### Composant

Les composants Astro permettent de reutiliser du code.

Par exemple un composant header, footer, etc 

Ces composants viendront se placer dans un dossier `src/components/Navigation.astro`

```astro
---
---
<a href="/">Accueil</a>
<a href="/a-propos/">À propos</a>
<a href="/blog/">Blog</a>
```

Une fois le composant definis, on peut venir l'importer dans les fichiers ayant besoin 

```astro 
---
import Navigation from '../components/Navigation.astro';
import "../styles/global.css";

const pageTitle = "Page d'accueil";
---
```

Puis on place le composant 

```astro
<Navigation />
```


Il est possible d'utiliser un composant dans un composant.

### JavaScript

Dans un dossier `src/scripts/fichier.js`, on viens y placer les scripts que l'on as besoin

```js
document.querySelector('.hamburger').addEventListener('click', () => {
  document.querySelector('.nav-links').classList.toggle('expanded');
});
```

on viens ensuite l'importer dans les fichiers

```astro
  <Footer />
  <script>
    document.querySelector('.hamburger')?.addEventListener('click', () => {
      document.querySelector('.nav-links')?.classList.toggle('expanded');
    });

    import "../scripts/menu.js";
  </script>
</body>
```
### Mise en page

Pour des composants qui sont sont rendu de maniere repeter sur chaque page, on peut mettre en place un layout.

Dans un dosier `src/layouts`, on viens placer nos fichier de layout

Par exemple, un fichier `BaseLayout.astro` permet de definir la mise en page general de l'app 

Le composant `<slot/>` permet d'injecter le composant enfant '

```astro 
---
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';
import '../styles/global.css';
const pageTitle = "Page d'accueil";
---
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
  <meta name="viewport" content="width=device-width" />
  <meta name="generator" content={Astro.generator} />
  <title>{pageTitle}</title>
</head>
<body>
<Header />
<h1>{pageTitle}</h1>
<slot />
<Footer />
<script>
  import "../scripts/menu.js";
</script>
</body>
</html>
```
Pour venir utiliser le layout, on viens importer et placer ce composant :

```astro 
---
import BaseLayout from '../layouts/BaseLayout.astro';
const pageTitle = "Page d'accueil";
---
<BaseLayout>
  <h2>Mon sous-titre de blog génial</h2>
</BaseLayout>
```
Pour transmettre des donneees dans le composant enfants 

```astro 
// index.astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
const pageTitle = "Page d'accueil";
---
<BaseLayout pageTitle={pageTitle}>
  <h2>Mon sous-titre de blog génial</h2>
</BaseLayout>
```
Pour utiliser cette variable dans le composant enfant, on viendras utiliser `Astro.props` qui est un objet qui contient tous les props fournis par le composant parent

```astro 
// BaseLayout.astro
---
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';
import '../styles/global.css';
const { pageTitle } = Astro.props;
---
```

### Ajouter une mise en page au fichiers md 

Avec la prop `layout` dans le frontmatter des `.md`, toutes les valeurs YAML du frontmatter sont disponible dans la mise en page.

De cette maniere, on peut definir un layout pour tous les articles de blog.

```astro
//src/layouts/MarkdownPostLayout.astro
---
const { frontmatter } = Astro.props;
---
<meta charset="utf-8" />
<h1>{frontmatter.title}</h1>
<p>Écrit par : {frontmatter.author}</p>
<slot />
```
On peut ensuite definir le layout dans le frontmatter du `.md`
```md
//src/pages/posts/post-1.md
---
// on appelle le layout de base
layout: ../../layouts/MarkdownPostLayout.astro
title: 'Mon premier article de blog'
pubDate: 2022-07-01
description: 'Ceci est le premier article de mon nouveau blog Astro.'
author: 'Apprenti Astro'
image:
url: 'https://docs.astro.build/assets/rose.webp'
alt: 'Le logo Astro sur un fond sombre avec une lueur rose.'
tags: ["astro", "blogging", "apprentissage en public"]
---
```
### API

Avec `Object.values(import.meta.glob(<path>, { eager: true }))` on peut retourner tous les fichiers md present dans un dossier. Cette prop retourner un tableau d'objets, un par fichier.

```astro 
---
import BaseLayout from '../layouts/BaseLayout.astro'
const allPosts = Object.values(import.meta.glob('./posts/*.md', { eager: true }));
const pageTitle = "Mon blog d'apprentissage Astro";
---
<BaseLayout pageTitle={pageTitle}>
  <p>C'est ici que je vais publier sur mon parcours d'apprentissage d'Astro.</p>
  <ul>
    <li><a href="/posts/post-1/">Article 1</a></li>
    <li><a href="/posts/post-2/">Article 2</a></li>
    <li><a href="/posts/post-3/">Article 3</a></li>
  </ul>
</BaseLayout>
```
On peut ensuite venir generer de maniere dynamique les listes des articles :

```astro 
---
import BaseLayout from '../layouts/BaseLayout.astro'
const allPosts = Object.values(import.meta.glob('./posts/*.md', { eager: true }));
const pageTitle = "Mon blog d'apprentissage Astro";
---
<BaseLayout pageTitle={pageTitle}>
  <p>C'est ici que je vais publier sur mon parcours d'apprentissage d'Astro.</p>
  <ul>
    <li><a href="/posts/post-1/">Article 1</a></li>
    <li><a href="/posts/post-2/">Article 2</a></li>
    <li><a href="/posts/post-3/">Article 3</a></li>

    {allPosts.map((post: any) => <li><a href={post.url}>{post.frontmatter.title}</a></li>)}
  </ul>
</BaseLayout>
```

### Page d'etiquettes

On peut creer des ensembles de pages dynamiquement en utilisant des fichier `.astro` qui exportent la fonction `getStaticPath()`

Dans un dossier `src/pages/tags/[tag].astro` :
```astro

---
import BaseLayout from '../../layouts/BaseLayout.astro';

export async function getStaticPaths() {
  return [
    { params: { tag: "astro" } },
    { params: { tag: "réussites" } },
    { params: { tag: "communauté" } },
    { params: { tag: "blogging" } },
    { params: { tag: "obstacles" } },
    { params: { tag: "apprentissage en public" } },
  ];
}

const { tag } = Astro.params;
---
<BaseLayout pageTitle={tag}>
  <p>Articles étiquetés avec {tag}</p>
</BaseLayout>
```
`getStaticPath()` retourne un tableau de routes de page, et toutes les pages correspondant a ces routes utiliseront le meme modele definis dans le fichier.

On pourras ensuite acceder a ces pages `http://localhost:4321/tags/astro` ou `astro` correspond a une etiquette definis dans le fichier










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
|   |- components/
|       |-- Navitation.astro
|   |- styles/
|       |-- global.css
└── package.json
```
- `pages` : permet de declarer les differentes pages du site. Une page = un fichier.










Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.



All commands are run from the root of the project, from a terminal:




