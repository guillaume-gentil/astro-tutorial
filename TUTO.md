# README

## Les ressources


> la [communauté discorde](https://discord.com/invite/grF4GTXXYm)
> 
> la [doc](https://docs.astro.build/en/getting-started/)
> 
> le [tuto](https://docs.astro.build/en/tutorial/1-setup/2/)
> 
> le [code du tuto final](https://github.com/withastro/blog-tutorial-demo)


> mon propre [repo sur github](https://github.com/guillaume-gentil/astro-tutorial)
>
> mon [dashboard netlify](https://app.netlify.com/teams/guillaume-gentil/projects)
>   * team: mytheme
>   * username: guillaume-gentil

---

## L'hébergement / Le versionning

🐙 Le **versionning** est assuré par `Git` / `Github`.

🖥️ L'**hébergement** est confié à `netlify`,

- création d'un compte gratuit
- connexion de netlify à github => installation de netlify sur le repo Github du tuto (tout est guidé par le wizard)

✅ Une fois la connexion entre netlify et github créée, le déploiement est automatique par défaut.

🔥 À chaque commit, le site sera mis à jour, netlify se charge du build.

---

## Les commandes

- initialiser un projet

```sh
node -v
# "The current minimum supported versions of each are: v18.20.8, v20.3.0, and v22.0.0. (v19 and v21 are not supported.)"

npm create astro@latest

# use minimal (empty) template with dependencies and git
```

- désactiver la télémétrie (anonyme)

```sh
cd ./tutorial

npm run astro telemetry disable
```

- démarrer le serveur de développement local

```sh
cd ./tutorial

npm run dev  # quit with ctrl+c
# http://localhost:4321/
```
