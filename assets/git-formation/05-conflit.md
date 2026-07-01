# 05 — Branche `fonctionnalite-4` et résolution de conflit

## Contexte

C'est l'étape la plus complexe. `fonctionnalite-4` repart du **premier commit** (`b28023e`) — en parallèle de `fonctionnalite-3`.  
Les deux branches modifient la même zone du même fichier : **le conflit est inévitable**.

---

## Retour sur `fonctionnalite-1` et création de `fonctionnalite-4`

```bash
git checkout fonctionnalite-1
git checkout -b fonctionnalite-4
```

**Pourquoi repasser par `fonctionnalite-1` ?**  
Elle pointe sur `b28023e` (premier commit). Créer `fonctionnalite-4` depuis là, c'est repartir d'une base vierge — **indépendamment** de `fonctionnalite-2` et `fonctionnalite-3`.

Cela simule deux développeurs travaillant en parallèle sur le même fichier.

---

## Commit concurrent sur `fonctionnalite-4`

```bash
# Modification de README.md...
git add README.md
git commit -m "Ajout du texte concurrent sur v4"
```

| Info | Valeur |
|---|---|
| Commit | `68938d1` |
| Modification | +1 ligne : "Ceci est le texte de la branche 4." |

```bash
git push origin fonctionnalite-4
```

---

## `git merge` — Fusion et déclenchement du conflit

```bash
git merge fonctionnalite-3
```

**Ce que ça fait :** Tente d'intégrer tous les commits de `fonctionnalite-3` dans `fonctionnalite-4`.

**Résultat :** Les deux branches ont modifié la même zone de `README.md` → **CONFLIT DE FUSION**.

Git arrête le merge et marque le fichier :

```
<<<<<<< HEAD
Ceci est le texte de la branche 4.
=======
Ceci est le texte de la branche 3.

Mise à jour v4.1
>>>>>>> fonctionnalite-3
```

| Balise | Signification |
|---|---|
| `<<<<<<< HEAD` | Contenu de la branche courante (`fonctionnalite-4`) |
| `=======` | Séparateur entre les deux versions |
| `>>>>>>> fonctionnalite-3` | Contenu de la branche à fusionner |

---

## Résolution manuelle du conflit

On édite le fichier pour **garder les deux contenus** et on supprime les balises Git :

```
Ceci est le texte de la branche 4.

Ceci est le texte de la branche 3.

Mise à jour v4.1
```

> Il n'y a pas de règle universelle : on garde ce qui a du sens selon le contexte. Parfois on garde les deux, parfois une seule version.

---

## Validation de la résolution

```bash
git add README.md
git commit -m "Résolution du conflit et fusion de v3 dans v4"
```

| Info | Valeur |
|---|---|
| Commit | `e20685b` |
| Type | **Merge commit** — deux parents : `68938d1` et `287a06a` |
| Modification | +4 lignes, -1 ligne |

```bash
git push origin fonctionnalite-4
```

---

## Suite des commits sur `fonctionnalite-4`

```bash
git add README.md
git commit -m "Ajout de details sur l avancement"
git push origin fonctionnalite-4
```

Commit `e0581d3` — +2 lignes.

```bash
git add README.md
git commit -m "Preparation de la version finale"
git push origin fonctionnalite-4
```

Commit `20a858d` — +3 lignes, modification de 1.

---

## `git diff` — Voir les différences

```bash
git diff                   # modifications non stagées
git diff --staged          # modifications stagées (prêtes pour commit)
git diff fonctionnalite-3  # différences entre la branche courante et fonctionnalite-3
```

Très utile avant un merge pour anticiper les conflits potentiels.

---

<p align="center">
  <a href="04-branche-3.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="06-finalisation.md"><img src="https://img.shields.io/badge/-SUIVANT-0d8f91?style=for-the-badge" alt="Suivant"></a>
</p>
