# 04 — Branche `fonctionnalite-3`

## Contexte

`fonctionnalite-3` est créée **depuis la fin de `fonctionnalite-2`** — elle hérite donc de ses deux commits.  
On ajoute deux nouveaux commits qui introduisent le contenu qui va **plus tard provoquer un conflit** avec `fonctionnalite-4`.

---

## Création depuis `fonctionnalite-2`

```bash
git checkout -b fonctionnalite-3
```

**Point de départ :** commit `3f520e3` (dernier commit de `fonctionnalite-2`).  
`fonctionnalite-3` hérite donc de tout l'historique de `fonctionnalite-2`.

---

## Premier commit — Début des travaux sur la v3

```bash
# Modification de README.md...
git add README.md
git commit -m "Début des travaux sur la v3"
```

| Info | Valeur |
|---|---|
| Commit | `ae42337` |
| Modification | 1 ligne modifiée |

---

## Deuxième commit — Ajout du texte de test

```bash
# Modification de README.md...
git add README.md
git commit -m "Ajout du texte de test sur v3"
```

| Info | Valeur |
|---|---|
| Commit | `287a06a` |
| Modification | +3 lignes dans `README.md` |

> C'est ce contenu — "Ceci est le texte de la branche 3." — qui entrera en conflit avec `fonctionnalite-4` à l'étape suivante.

---

## Publication

```bash
git push origin fonctionnalite-3
```

---

## `git log` — Visualiser l'historique

```bash
git log --oneline
```

Affiche l'historique condensé (une ligne par commit) :

```
287a06a Ajout du texte de test sur v3
ae42337 Début des travaux sur la v3
3f520e3 Ajustement et finition de la v2
27111b9 Ajout des fonctionnalités de la v2
b28023e first commit
```

> **Variantes utiles :**
> ```bash
> git log --oneline --graph --all   # vue graphique de toutes les branches
> git log --author="Fanny"          # filtrer par auteur
> git log --since="2026-06-01"      # filtrer par date
> ```

---

## `git branch` — Lister les branches

```bash
git branch        # branches locales
git branch -a     # branches locales + distantes
```

À ce stade, on a :
```
  fonctionnalite-1
  fonctionnalite-2
* fonctionnalite-3   ← branche courante
  main
```

---

<p align="center">
  <a href="03-branche-1-et-2.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="05-conflit.md"><img src="https://img.shields.io/badge/-SUIVANT-0d8f91?style=for-the-badge" alt="Suivant"></a>
</p>
