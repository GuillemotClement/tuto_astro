# Tuto Astro

## Info 
Astro est le framework web pour créer des sites web axés sur le contenu tels que des blogs, des pages marketing et du commerce électronique. 

Astro est surtout connu pour être le pionnier d’une nouvelle architecture frontend visant à réduire la surcharge et la complexité de JavaScript par rapport à d’autres frameworks. 

Si vous avez besoin d’un site web qui se charge rapidement et qui a un excellent référencement, Astro est fait pour vous.

## Fonctionnalites
Astro est un framework web tout-en-un. Il comprend tout ce dont vous avez besoin pour créer un site web, de manière intégrée. Des centaines d’intégrations et de hooks d’API sont également disponibles pour personnaliser un projet en fonction de votre cas d’utilisation et de vos besoins exacts.

Voici quelques points marquants :

- Îlots : Une architecture web basée sur des composants optimisée pour les sites web axés sur le contenu.
- UI indépendante : Prend en charge React, Preact, Svelte, Vue, Solid, HTMX, les composants web, et bien plus encore.
- Priorité au serveur : Déplace le rendu coûteux hors des appareils de vos visiteurs.
- Zéro JS, par défaut : Moins de JavaScript côté client pour ralentir votre site.
- Collections de contenu : Organise, valide et fournit la sûreté du typage TypeScript pour votre contenu Markdown.
- Personnalisable : Partytown, MDX, et des centaines d’intégrations parmi lesquelles choisir.

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
- `pages` : 










Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Any static assets, like images, can be placed in the `public/` directory.



All commands are run from the root of the project, from a terminal:




