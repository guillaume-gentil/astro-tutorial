# README

- [README](#readme)
  - [Les ressources globales](#les-ressources-globales)
    - [Dashboard netlify](#dashboard-netlify)
    - [Apprendre Astro](#apprendre-astro)
    - [Obtenir de l'aide sur Astro](#obtenir-de-laide-sur-astro)
  - [Pipeline CI/CD](#pipeline-cicd)
  - [Les commandes](#les-commandes)
  - [Fonctionnement du framework `Astro`](#fonctionnement-du-framework-astro)
    - [Structure des dossiers d'un projet Astro](#structure-des-dossiers-dun-projet-astro)
    - [Le Routing dans Astro](#le-routing-dans-astro)
    - [Le *frontmatter* des fichier `.md` et son format `YAML`](#le-frontmatter-des-fichier-md-et-son-format-yaml)
    - [Le *frontmatter* des fichier `.astro` et son format `JS`](#le-frontmatter-des-fichier-astro-et-son-format-js)
    - [Le JS dans les fichiers `.astro` (server-side)](#le-js-dans-les-fichiers-astro-server-side)
    - [Les scripts JS pour ajouter de l'interactivité sur un site web Astro (client-side)](#les-scripts-js-pour-ajouter-de-linteractivité-sur-un-site-web-astro-client-side)
  - [Personnaliser les styles](#personnaliser-les-styles)
    - [`<style>` basique local](#style-basique-local)
    - [Les variables de style locales](#les-variables-de-style-locales)
    - [Ajouter un style global](#ajouter-un-style-global)
  - [Gestion des composants](#gestion-des-composants)
    - [Composant simple](#composant-simple)
    - [Composant enfant et passage de `props`](#composant-enfant-et-passage-de-props)


## Les ressources globales

### Dashboard netlify

* mon [dashboard netlify](https://app.netlify.com/teams/guillaume-gentil/projects)

>   * team: mytheme
>   * username: guillaume-gentil

---

### Apprendre Astro

* le [tuto](https://docs.astro.build/en/tutorial/1-setup/2/)
* le [code du tuto final](https://github.com/withastro/blog-tutorial-demo)
* mon [repo sur github](https://github.com/guillaume-gentil/astro-tutorial)

---

### Obtenir de l'aide sur Astro

* la [doc](https://docs.astro.build/en/getting-started/)
* la [communauté discorde](https://discord.com/invite/grF4GTXXYm)
* le site d'[astuces](https://astro-tips.dev/) partagées par la communauté, et notament comment utiliser [GSAP dans mon projet Astro](https://astro-tips.dev/tips/how-to-add-gsap/)

---

## Pipeline CI/CD

🐙 Le **versionning** est assuré par `Git` / `Github`.

🖥️ L'**hébergement** est confié à `netlify`,

- création d'un compte gratuit
- connexion de netlify à github => installation de netlify sur le repo Github du tuto (tout est guidé par le wizard)

✅ Une fois la connexion entre netlify et github créée, le déploiement est automatique par défaut.

🔥 À chaque commit, le site sera mis à jour, netlify se charge du build.

---

## Les commandes

Initialiser un projet,

```sh
node -v
# "The current minimum supported versions of each are: v18.20.8, v20.3.0, and v22.0.0. (v19 and v21 are not supported.)"

npm create astro@latest

# use minimal (empty) template with dependencies and git
```

Désactiver la télémétrie (bien qu'anonymes),

```sh
cd ./tutorial

npm run astro telemetry disable
```

Démarrer le serveur de développement local,

```sh
cd ./tutorial

npm run dev  # quit with ctrl+c
# http://localhost:4321/
```

## Fonctionnement du framework `Astro`

### Structure des dossiers d'un projet Astro

La structure des dossier a son importance car Astro de va "interpréter" différement les fichiers selon leur emplacement.

Ce sera le cas notamment pour les Page vs Componsants

```md
└── src
    ├── components
    |   ├── Footer.astro
    |   ├── Navigation.astro
    |   └── Social.astro
    ├── pages
    |   ├── posts
    |   |   ├── post-1.md
    |   |   ├── post-2.md
    |   |   └── post-3.md
    |   ├── about.astro
    |   ├── blog.astro
    |   └── index.astro
    ├── scripts
    |   ├── script-1.js
    |   └── script-2.js
    └── styles
        ├── reset.css
        └── global.css
```

### Le Routing dans Astro

[🟢 File-based Routing in Astro](https://docs.astro.build/en/basics/astro-pages/#file-based-routing)

[🟢 Astro page HTML](https://docs.astro.build/en/basics/astro-pages/#astro-pages)

---

### Le *frontmatter* des fichier `.md` et son format `YAML`

Le *frontmatter*, c'est l'entête présent dans le fichiers `post-x.md` qui permet d'attribuer des propriétés au *post*.

Celui-ci est écrit en [🟢 YAML](https://assemble.io/docs/YAML-front-matter.html)

```yaml
# exemple du fichier post.md

---
title: 'My Third Blog Post'
author: 'Astro Learner'
description: "I had some challenges, but asking in the community really helped!"
image: 
    url: 'https://docs.astro.build/assets/rose.webp'
    alt: 'The Astro logo on a dark background with a pink glow.'
tags: ["astro", "blogging", "learning in public"]
pubDate: 2025-11-06
---
It wasn't always smooth sailing, but I'm enjoying building with Astro. And, the [Discord community](https://astro.build/chat) is really friendly and helpful!
```

---

### Le *frontmatter* des fichier `.astro` et son format `JS`

Il est tout a fait possible d'utiliser JavaScript ou TypeScript dans un fichier `page.astro`, la méthode la plus simple est de l'ajouter dans le *frontmatter* et de l'appeler dans le html en utilisant les `{ }`.

> le frontmatter des fichiers `.astro` ne peut contenir que du `JS` ou du `TS`

```js
// page.astro

---
const pageTitle = "Mon titre dynamique";
---

<h1>{ pageTitle }</h1>
```

---

### Le JS dans les fichiers `.astro` (server-side)

De même que l'on utilise des variables, Astro permet d'utiliser JS (ou TS) dans les fichiers `.astro`.

> Il est **obligatoire** d'insérer le code `JS` entre des `{ }` dans le `html` pour qu'il soit reconnu.

> Les fichiers de template `.astro` utilisent la syntaxe `JSX` à [🟢 quelques différences](https://docs.astro.build/en/reference/astro-syntax/#differences-between-astro-and-jsx) prêt

> 🚨 le JS inclus dans le frontmatter n'a pas vocation à être utilisé comme script côté client.
> 
> Il sert seulement à construire le template HTML via Node (server-side).
> 
> Nous verrons par la suite comment créer un `script client-side` pour rendre le site interactif.
>
> Pour aller plus loin, il faut se pencher sur la [🟢 notion d'`Islands architecture` propre à Astro](https://docs.astro.build/en/concepts/islands/)

Quelques exemples,

```js
// page.astro

<ul>
    <li>My name is { identity.firstName }.</li>
    <li>
      I live in { identity.country } and I work as a { identity.occupation }.
    </li>
    { identity.hobbies.length >= 2 && (
      <li>
        Two of my hobbies are:
        { identity.hobbies[0] } and { identity.hobbies[1] }
      </li>
    ) }
</ul>
```

```js
// page.astro

<ul>
    { skills.map(
      ( skill ) => <li>{ skill }</li>
    ) }
</ul>
```

Pour aller plus loin, [🟢 la doc donne quelques exemples d'utilisation courante](https://docs.astro.build/en/reference/astro-syntax/#jsx-like-expressions).

---

### Les scripts JS pour ajouter de l'interactivité sur un site web Astro (client-side)

Pour ajouter du JS *client-side* aux pages et composants Astro, il faut insérer le code dans une balise `<script>...</script>`, en pied de page comme on le ferait pour du html standard.

Une autre solution est possible et passe par l'importation d'un fichier `src/scripts/mon-script.js` dédié puis, de l'importer en pied de page.

Exemple de fichier `src/scripts/mon-script.js`,

```js
const menu = document.querySelector('.menu');

menu?.addEventListener('click', () => {
const isExpanded = menu.getAttribute('aria-expanded') === 'true';
menu.setAttribute('aria-expanded', `${!isExpanded}`);
});
```

Et son importation depuis le pied de la page avant la fermeture de la balise `</body>` sur chaque Page,

```astro
<!-- ... -->
</footer>

<script>
  import "../scripts/menu.js";
</script>
```

Pour bien comprendre comment Astro gère les scripts, lire la [🟢 page de la doc dédiée](https://docs.astro.build/en/guides/client-side-scripts/).

On y apprend notament que :

- Par défaut, Astro traite les balises `<script>` qui ne contiennent aucun attribut (autre que `src`) selon les points suivants
  - tous les scripts sont lu comme du code `TypeScript` par défaut,
  - tous les imports (fichiers locaux, modules npm) sont regroupés lors du build,
  - les scripts sont traités automatiquement comme des `type="module"`,
  - si un composant contenant un `<script>` est utilisé plusieurs fois sur une page, le script ne sera inclus qu'une seule fois,
  - si le script est suffisamment petit, Astro l'intégrera directement dans le HTML lors du build afin de réduire le nombre de requêtes.

---

## Personnaliser les styles

### `<style>` basique local

Les fichiers `.astro` acceptent la balise `<style>` comme un fichier `.html`

Voir aussi [🟢 la page de la doc astro à ce sujet](https://docs.astro.build/en/guides/styling/#styling-in-astro).

---

### Les variables de style locales

Il est tout à fait possible d'utiliser des variable JS et de les lire dans le CSS,

```html
---
const skillColor = "orange";
const fontWeight = "bold";
const textCase = "uppercase";
---

<html lang="en">
<head>
  <!-- ... -->
  <style define:vars={{skillColor, fontWeight, textCase}}>
      h1 {
          color: purple;
          font-size: 4rem;
      }
      .skill {
          color: var(--skillColor);
          font-weight: var(--fontWeight);
          text-transform: var(--textCase);
      }
  </style>
</head>
<body>
  <ul>
    { skills.map(
      ( skill ) => <li class="skill">{ skill }</li>
    ) }
  </ul>
</body>
```

[🟢 Consulter la doc](https://docs.astro.build/en/guides/styling/#css-variables) pour aller plus loin.

---

### Ajouter un style global

Il est très facile d'utiliser une feuille de style globale (par exemple pour un reset, normalize,...). Pour cela, il suffit d'importer la ou les feuilles de styles dans le *frontmatter* du fichier `.astro` comme ceci,

```astro
---
import '../styles/global.css';
// puis, le reste du code JS
---
<!-- enfin, le code HTML de la page -->
```

> Ce style s'applique globalement mais si le fichier contient du `<style>` localement, celui-ci sera prioritaire.

---

## Gestion des composants

> Astro permet de penser son interface en terme de composants réutilisables.
>
> Exemples :
> - Navigations (responsive)
> - Footer
> - Média Sociaux

Les composants sont placés dans le dossier `src/components/` et possèdent l'extension `.astro`.

Le dossier `components` est important pour siginifier à Astro que ce ne sont pas de page mais bien des composants.

> 🟢 Aller plus loin sur l'[utilisation des composants dans Astro](https://docs.astro.build/en/basics/astro-components/).

---

### Composant simple

Exemple du composant `src/components/Navigation.astro`,

```astro
<!-- si il n'y a rien a mettre dans le frontmatter, il est inutile de mettre les `---` ouvrantes et fermantes -->

<a href="/">Home</a>
<a href="/about/">About</a>
<a href="/blog/">Blog</a>
```

Et son utilisation (via un import JS) dans un fichier `.astro`,

```astro
---
import Navigation from '../components/Navigation.astro';

import '../styles/global.css';

// ...
---
<!-- ... -->
<body>
  <Navigation />
  <!-- ... -->
</body>
```

---

### Composant enfant et passage de `props`

Prenons l'exemple d'un `Footer` dans lequel sera utilisé le composant `Social`.

```
└── src
    ├── components
    |   ├── Footer.astro
    |   ├── Social.astro
```

Le composant `Social` avec ses propriétés et son style,

```astro
---
const { platform, username } = Astro.props;
---
<a href={`https://www.${platform}.com/${username}`}>{platform}</a>

<style>
  a {
    padding: 0.5rem 1rem;
    color: white;
    background-color: #4c1d95;
    text-decoration: none;
  }
</style>
```

Et le composant `Footer` qui transmet des `props` au composant `Social` ainsi que son style,

```astro
---
import Social from './Social.astro';
---
<style>
  footer {
    display: flex;
    gap: 1rem;
    margin-top: 2rem;
  }
</style>

<hr>
<footer>
    <Social platform="twitter" username="astrodotbuild" />
    <Social platform="github" username="withastro" />
    <Social platform="youtube" username="astrodotbuild" />
</footer>
```
