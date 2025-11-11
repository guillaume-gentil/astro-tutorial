# README

- [README](#readme)
  - [Les ressources globales](#les-ressources-globales)
    - [Apprendre Astro](#apprendre-astro)
    - [Dashboard netlify](#dashboard-netlify)
    - [Obtenir de l'aide sur Astro](#obtenir-de-laide-sur-astro)
  - [Pipeline CI/CD](#pipeline-cicd)
  - [Les commandes](#les-commandes)
  - [Fonctionnement du framework `Astro`](#fonctionnement-du-framework-astro)
    - [Le Routing dans Astro](#le-routing-dans-astro)
    - [Le *frontmatter* des fichier `.md` et son format `YAML`](#le-frontmatter-des-fichier-md-et-son-format-yaml)
    - [Le *frontmatter* des fichier `.astro` et son format `JS`](#le-frontmatter-des-fichier-astro-et-son-format-js)
    - [Le JS dans les fichiers `.astro`](#le-js-dans-les-fichiers-astro)


## Les ressources globales

### Apprendre Astro

* le [tuto](https://docs.astro.build/en/tutorial/1-setup/2/)
* le [code du tuto final](https://github.com/withastro/blog-tutorial-demo)
* mon [repo sur github](https://github.com/guillaume-gentil/astro-tutorial)

### Dashboard netlify

* mon [dashboard netlify](https://app.netlify.com/teams/guillaume-gentil/projects)

>   * team: mytheme
>   * username: guillaume-gentil

### Obtenir de l'aide sur Astro

* la [communauté discorde](https://discord.com/invite/grF4GTXXYm)
* la [doc](https://docs.astro.build/en/getting-started/)



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

### Le Routing dans Astro

[File-based Routing in Astro](https://docs.astro.build/en/basics/astro-pages/#file-based-routing)

[Astro page HTML](https://docs.astro.build/en/basics/astro-pages/#astro-pages)

---

### Le *frontmatter* des fichier `.md` et son format `YAML`

Le *frontmatter*, c'est l'entête présent dans le fichiers `post-x.md` qui permet d'attribuer des propriétés au *post*.

Celui-ci est écrit en [YAML](https://assemble.io/docs/YAML-front-matter.html)

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

### Le JS dans les fichiers `.astro`

De même que l'on utilise des variables, Astro permet d'utiliser JS (ou TS) dans les fichiers `.astro`.

> Il est **obligatoire** d'insérer le code `JS` entre des `{ }` dans le `html` pour qu'il soit reconnu.

> Les fichiers de template `.astro` utilisent la syntaxe `JSX`

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
