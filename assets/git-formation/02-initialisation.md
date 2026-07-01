# 02 — Initialisation du dépôt

## Contexte

Tout commence ici : création du dépôt local, premier fichier, et envoi sur GitHub.

---

## `git init`

```bash
git init
```

**Ce que ça fait :** Crée un nouveau dépôt Git dans le dossier courant. Un sous-dossier caché `.git/` est créé — c'est lui qui contient tout l'historique.  
**Quand l'utiliser :** Une seule fois, au tout début d'un projet, pour "activer" le suivi de versions.

---

## `git add`

```bash
git add README.md
```

**Ce que ça fait :** Place le fichier `README.md` dans la **zone de staging** (aussi appelée "index"). Les fichiers stagés sont ceux qui seront inclus dans le prochain commit.

**Analogie :** C'est comme mettre des affaires dans une boîte avant de la fermer. On choisit ce qu'on met dedans avant de sceller.

> **Variantes utiles :**
> ```bash
> git add .           # stage tous les fichiers modifiés du dossier courant
> git add -A          # stage toutes les modifications (ajouts + suppressions)
> git add *.md        # stage tous les fichiers .md
> ```

---

## `git commit`

```bash
git commit -m "first commit"
```

**Ce que ça fait :** Enregistre un instantané de tous les fichiers stagés dans l'historique Git. Le `-m` permet d'écrire le message directement dans la commande.

**Résultat :** Commit `b28023e` — le tout premier commit du dépôt, sur la branche `main`.

> **Bonne pratique :** Un message de commit doit être court, clair, et au présent ou à l'infinitif.  
> ✅ `"Ajout de la page d'accueil"`  
> ❌ `"modification des trucs"`

---

## `git push`

```bash
git push origin main
```

**Ce que ça fait :** Envoie les commits locaux vers le dépôt distant (`origin` = GitHub). `main` est le nom de la branche à pousser.

**Résultat :** Le dépôt GitHub reçoit le premier commit — il est maintenant visible en ligne.

> `origin` est le nom par défaut du dépôt distant. On peut avoir plusieurs remotes avec des noms différents.

---

<p align="center">
  <a href="01-introduction.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="03-branche-1-et-2.md"><img src="https://img.shields.io/badge/-SUIVANT-0d8f91?style=for-the-badge" alt="Suivant"></a>
</p>
