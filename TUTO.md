# README

- [README](#readme)
  - [Les ressources globales](#les-ressources-globales)
    - [Apprendre Astro](#apprendre-astro)
    - [Dashboard netlify](#dashboard-netlify)
    - [Obtenir de l'aide sur Astro](#obtenir-de-laide-sur-astro)
  - [Pipeline CI/CD](#pipeline-cicd)
  - [Les commandes](#les-commandes)
  - [Pour aller plus loin](#pour-aller-plus-loin)
    - [Le Routing dans Astro](#le-routing-dans-astro)


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

## Pour aller plus loin

### Le Routing dans Astro

[File-based Routing in Astro](https://docs.astro.build/en/basics/astro-pages/#file-based-routing)

[Astro page HTML](https://docs.astro.build/en/basics/astro-pages/#astro-pages)
