# 06 — Branche `fonctionnalite-5` et fusion finale

## Branche `fonctionnalite-5` — Le commit de clôture

### Création depuis `fonctionnalite-4`

```bash
git checkout -b fonctionnalite-5
```

**Point de départ :** commit `20a858d` (dernier commit de `fonctionnalite-4`).

---

### Commit final

```bash
git add README.md
git commit -m "Commit 10: Fin de l entrainement Git"
```

| Info | Valeur |
|---|---|
| Commit | `281a563` |
| Note | C'est le **10e commit** de l'exercice (en comptant le merge commit) |

```bash
git push origin fonctionnalite-5
```

---

## Pull Request #3 — Fusion sur GitHub

Une **Pull Request** est ouverte sur GitHub pour proposer la fusion de `fonctionnalite-5` dans `main`.

> **Pourquoi une Pull Request et pas un merge direct ?**  
> La PR permet à d'autres développeurs de **relire le code**, laisser des commentaires, et approuver les changements avant qu'ils n'intègrent `main`. C'est la base du travail collaboratif.

GitHub crée automatiquement un **merge commit** lors de la fusion :

| Info | Valeur |
|---|---|
| Commit | `7dda6fc` |
| Message | `Merge pull request #3 from fannysaez/fonctionnalite-5` |

---

## Retour en local — Synchronisation avec `main`

### `git checkout` — Basculer sur `main`

```bash
git checkout main
```

Bascule la copie de travail locale sur la branche `main`.

---

### `git pull` — Récupérer le merge

```bash
git pull origin main
```

**Ce que ça fait :** Récupère les nouveaux commits depuis GitHub (dont le merge commit de la PR #3) et les intègre dans la branche locale `main`.

C'est l'équivalent de :

```bash
git fetch origin main   # télécharge sans intégrer
git merge origin/main   # intègre dans la branche locale
```

**Résultat :** La branche locale `main` est à jour avec le dépôt distant.

---

### `git reset` — Vérification d'état

```bash
git reset HEAD
```

**Ce que ça fait :** Remet la zone de staging à l'état du dernier commit, sans toucher aux fichiers.  
Utilisé ici pour s'assurer que rien n'est accidentellement stagé.

> `git reset HEAD` est non-destructif : les fichiers ne sont pas modifiés, seul le staging est nettoyé.

---

## `git fetch` vs `git pull`

| Commande | Effet |
|---|---|
| `git fetch` | Télécharge les changements distants **sans** les intégrer à la branche locale |
| `git pull` | Télécharge **et** intègre en une seule commande (`fetch` + `merge`) |

> **Bonne pratique :** Utiliser `git fetch` d'abord pour inspecter ce qui arrive, puis `git merge` pour intégrer en connaissance de cause.

---

## `git stash` — Mettre des modifications de côté

```bash
git stash
```

**Situation :** Tu as des modifications en cours sur ta branche, mais tu dois changer de branche sans les committer (elles ne sont pas prêtes, ou tu n'as pas envie de faire un commit incomplet).

**Ce que ça fait :** Git **sauvegarde** temporairement toutes les modifications non commitées (fichiers modifiés + fichiers stagés) dans une pile, et remet le répertoire de travail dans l'état du dernier commit. La branche est propre, tu peux naviguer librement.

```bash
# Exemple concret :
# Tu travailles sur fonctionnalite-4, tu as des modifs non commitées
git stash                  # → modifs mises de côté, répertoire propre
git checkout fonctionnalite-3   # → changement de branche sans problème
```

> Le stash fonctionne comme une **pile** (LIFO) : le dernier stash créé est le premier récupéré.

---

## `git stash pop` — Récupérer les modifications mises de côté

```bash
git stash pop
```

**Ce que ça fait :** Réapplique les dernières modifications stashées sur la branche courante **et** les supprime de la pile du stash.

```bash
git checkout fonctionnalite-4   # retour sur la branche de travail
git stash pop                   # → les modifs sont restaurées
```

> **`git stash pop` vs `git stash apply` :**
> - `git stash pop` : restaure **et** supprime le stash de la pile
> - `git stash apply` : restaure **sans** supprimer (le stash reste disponible)

---

## Commandes stash utiles

```bash
git stash list              # liste tous les stashs sauvegardés
git stash show              # aperçu du dernier stash
git stash drop              # supprime le dernier stash sans l'appliquer
git stash clear             # supprime tous les stashs
git stash push -m "message" # stash avec un nom personnalisé
```

---

<p align="center">
  <a href="05-conflit.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="07-recapitulatif.md"><img src="https://img.shields.io/badge/-SUIVANT-0d8f91?style=for-the-badge" alt="Suivant"></a>
</p>
