# 03 — Branches `fonctionnalite-1` et `fonctionnalite-2`

## Pourquoi travailler en branches ?

Bonne pratique fondamentale : **on ne travaille jamais directement sur `main`**.  
On crée une branche dédiée pour chaque fonctionnalité, correction ou expérimentation.  
Cela permet de développer en parallèle sans risquer de casser le code stable.

---

## `git checkout -b` — Créer et basculer sur une branche

```bash
git checkout -b fonctionnalite-1
```

**Ce que ça fait :** Crée une nouvelle branche **et** bascule dessus en une seule commande.  
C'est un raccourci pour :

```bash
git branch fonctionnalite-1    # crée la branche
git checkout fonctionnalite-1  # bascule dessus
```

**Résultat :** On est maintenant sur `fonctionnalite-1`, qui pointe sur le même commit que `main` (`b28023e`).

> **Commande moderne (Git 2.23+) :**
> ```bash
> git switch -c fonctionnalite-1
> ```
> `switch` remplace `checkout` pour changer de branche. Les deux fonctionnent.

---

## Publier la branche sur GitHub

```bash
git push origin fonctionnalite-1
```

Publie la branche sur GitHub pour permettre d'ouvrir une Pull Request.

> **Note :** `fonctionnalite-1` ne contient aucun commit propre — elle sert de **point de départ commun** pour les branches suivantes.

---

## Branche `fonctionnalite-2` — Deux commits successifs

### Création depuis `fonctionnalite-1`

```bash
git checkout -b fonctionnalite-2
```

Nouvelle branche créée depuis `fonctionnalite-1` (commit `b28023e`).

---

### Premier commit

```bash
# Modification de README.md...
git add README.md
git commit -m "Ajout des fonctionnalités de la v2"
```

| Info | Valeur |
|---|---|
| Commit | `27111b9` |
| Modification | +1 ligne dans `README.md` |

---

### Deuxième commit

```bash
# Modification de README.md...
git add README.md
git commit -m "Ajustement et finition de la v2"
```

| Info | Valeur |
|---|---|
| Commit | `3f520e3` |
| Modification | 1 ligne modifiée dans `README.md` |

---

### Publication

```bash
git push origin fonctionnalite-2
```

La branche avec ses 2 commits est visible sur GitHub. Une Pull Request peut être ouverte.

---

## `git status` — Vérifier l'état du dépôt

```bash
git status
```

À utiliser régulièrement pour voir :
- Les fichiers modifiés non stagés
- Les fichiers stagés prêts pour le commit
- La branche courante

---

<p align="center">
  <a href="02-initialisation.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="04-branche-3.md"><img src="https://img.shields.io/badge/-SUIVANT-0d8f91?style=for-the-badge" alt="Suivant"></a>
</p>
