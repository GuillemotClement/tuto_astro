# Tuto Astro

## 👨🏻‍💻 Note

Les fichiers Astro utilise l'extension `.astro`.

Le nomn du fichier correspond au path a passer.
Exemple : une page `about.astro` est accessible avec `http://localhost/about`

On utilise du HTML classique pour definir le contenu de la page.

`<a href="/about">` => pour declarer un nouveau lien et acceder a la page
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




