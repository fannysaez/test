# Documentation Git — Entraînement complet

> Historique complet et expliqué de toutes les commandes Git utilisées dans ce dépôt, du premier `git init` jusqu'au merge final sur `main`.

---

## Table des matières

- [Vue d'ensemble du dépôt](#vue-densemble-du-dépôt)
- [Gitnuro — Interface visuelle Git](#gitnuro--interface-visuelle-git)
- [Évolution du fichier README.md par branche](#évolution-du-fichier-readmemd-par-branche)
- [Schéma des branches](#schéma-des-branches)
- [Étape 1 — Initialisation du dépôt](#étape-1--initialisation-du-dépôt)
- [Étape 2 — Branche `fonctionnalite-1`](#étape-2--branche-fonctionnalite-1)
- [Étape 3 — Branche `fonctionnalite-2`](#étape-3--branche-fonctionnalite-2)
- [Étape 4 — Branche `fonctionnalite-3`](#étape-4--branche-fonctionnalite-3)
- [Étape 5 — Branche `fonctionnalite-4` et résolution de conflit](#étape-5--branche-fonctionnalite-4-et-résolution-de-conflit)
- [Étape 6 — Branche `fonctionnalite-5`](#étape-6--branche-fonctionnalite-5)
- [Étape 7 — Fusion finale sur `main`](#étape-7--fusion-finale-sur-main)
- [Récapitulatif de toutes les commandes](#récapitulatif-de-toutes-les-commandes)
- [Lexique Git](#lexique-git)

---

## Vue d'ensemble du dépôt

Ce dépôt est un **exercice d'entraînement Git complet** réalisé le 29 juin 2026 par **Fanny Saez**.  
Il couvre les notions essentielles : création de branches, commits successifs, gestion d'un conflit de fusion, et Pull Requests sur GitHub.

| Élément | Détail |
|---|---|
| Dépôt GitHub | https://github.com/fannysaez/test |
| Branches créées | `main`, `fonctionnalite-1` à `fonctionnalite-5` |
| Nombre de commits | 11 (dont 1 merge commit) |
| Conflit résolu | 1 conflit entre `fonctionnalite-3` et `fonctionnalite-4` |
| Pull Requests | 3 PR fusionnées sur GitHub |

---

## Gitnuro — Interface visuelle Git

**Gitnuro** est un client Git graphique open source, léger et multiplateforme (Windows, macOS, Linux).  
Il permet de visualiser l'historique des commits, gérer les branches, stager des fichiers et effectuer des pushs/pulls — sans taper de commandes dans un terminal.

### Ce que montre la capture ci-dessous

![Capture Gitnuro — historique du dépôt test](assets/img/gitNuro/gitNuro.png)

| Zone | Description |
|---|---|
| **Panneau gauche** | Liste des branches locales (6 au total : `main` + `fonctionnalite-1` à `5`) et le dépôt distant `origin` |
| **Colonne Graph** | Représentation visuelle de l'arbre des commits — on voit clairement la divergence et la convergence des branches |
| **Colonne Message** | Nom du commit, branches associées (local + `origin/`) et date |
| **Panneau droit** | Zone de staging — affiche les fichiers modifiés prêts à être commités |
| **Barre du haut** | Actions rapides : `Pull`, `Push`, `Branch`, `Stash`, `Pop stash`, `Terminal` |

> **Pourquoi utiliser Gitnuro ?**  
> Il est particulièrement utile pour visualiser les conflits, comprendre la structure des branches, et effectuer des opérations Git sans mémoriser toutes les commandes. Idéal en apprentissage.

---

## Évolution du fichier README.md par branche

Ce tableau montre **l'état réel du fichier `README.md`** après chaque étape clé — c'est le fichier qui a servi de terrain d'entraînement tout au long de l'exercice.

---

### Après `first commit` — branche `main` / `fonctionnalite-1`
```
(fichier vide)
```

---

### Après `fonctionnalite-2` — 2 commits
```
Ceci est le texte de la branche 4.
Version 2.1.1
```
> `fonctionnalite-2` a introduit le contenu de base : une première ligne et un numéro de version.

---

### Après `fonctionnalite-3` — 2 commits (hérite de v2)
```
Ceci est le texte de la branche 4.
Version 2.1.1

Ceci est le texte de la branche 3.
```
> `fonctionnalite-3` a ajouté la ligne "branche 3" — c'est cette ligne qui créera le conflit avec `fonctionnalite-4`.

---

### Après `fonctionnalite-4` — avant le merge (commit concurrent)
```
Ceci est le texte de la branche 4.
```
> `fonctionnalite-4` est partie du premier commit (dépôt vide), a écrit sa propre ligne — en parallèle de `fonctionnalite-3`. Les deux branches ont modifié la même zone du fichier : **conflit garanti**.

---

### Pendant le conflit — ce que Git affiche dans le fichier
```
<<<<<<< HEAD
Ceci est le texte de la branche 4.
=======
Ceci est le texte de la branche 3.

Mise à jour v4.1
>>>>>>> fonctionnalite-3
```
> Git a marqué les deux versions. Il faut éditer manuellement pour choisir/fusionner.

---

### Après résolution du conflit + suite des commits sur `fonctionnalite-4`
```
Ceci est le texte de la branche 4.
Version 2.1.1

Ceci est le texte de la branche 3.

Mise à jour v4.1

Ligne de préparation pour le conflit final
```
> Les deux contenus coexistent. Les commits suivants ont ajouté les lignes manquantes.

---

### État final — après merge de `fonctionnalite-5` dans `main`
```
Ceci est le texte de la branche 4.
Version 2.1.1

Ceci est le texte de la branche 3.

Mise à jour v4.1

Ligne de préparation pour le conflit final

Fin de l'exercice !
```
> C'est le contenu actuel du fichier — résultat de l'ensemble des branches, commits, conflits et merges.

---

## Schéma des branches

```
main          ●─────────────────────────────────────────────────●  (Merge PR #3)
               \                                                /
fonctionnalite-5 \                                             ● Commit 10: Fin de l'entrainement
fonctionnalite-4  ●──●──M──●──●                               (M = merge de fonctionnalite-3)
                  ↑  ↑  ↑
fonctionnalite-3  │  │  └──●──●  (v3: 2 commits)
fonctionnalite-2  │  └──●──●    (v2: 2 commits)
fonctionnalite-1  └── (branche vide, sert de point de départ)
```

---

## Étape 1 — Initialisation du dépôt

### Contexte
Tout commence ici : création du dépôt local, premier fichier, et envoi sur GitHub.

---

### `git init`
```bash
git init
```
**Ce que ça fait :** Crée un nouveau dépôt Git dans le dossier courant. Un sous-dossier caché `.git/` est créé — c'est lui qui contient tout l'historique.  
**Quand l'utiliser :** Une seule fois, au tout début d'un projet, pour "activer" le suivi de versions.

---

### `git add`
```bash
git add README.md
```
**Ce que ça fait :** Place le fichier `README.md` dans la **zone de staging** (aussi appelée "index"). Les fichiers stagés sont ceux qui seront inclus dans le prochain commit.  
**Analogie :** C'est comme mettre des affaires dans une boîte avant de la fermer. On choisit ce qu'on met dedans avant de sceller.

---

### `git commit`
```bash
git commit -m "first commit"
```
**Ce que ça fait :** Enregistre un instantané de tous les fichiers stagés dans l'historique Git. Le `-m` permet d'écrire le message directement dans la commande.  
**Résultat :** Commit `b28023e` — le tout premier commit du dépôt, sur la branche `main`.

---

### `git push`
```bash
git push origin main
```
**Ce que ça fait :** Envoie les commits locaux vers le dépôt distant (`origin` = GitHub). `main` est le nom de la branche à pousser.  
**Résultat :** Le dépôt GitHub est créé avec le premier commit.

---

## Étape 2 — Branche `fonctionnalite-1`

### Contexte
Bonne pratique : on ne travaille jamais directement sur `main`. On crée une branche dédiée pour chaque fonctionnalité.

---

### `git checkout -b`
```bash
git checkout -b fonctionnalite-1
```
**Ce que ça fait :** Crée une nouvelle branche **et** bascule dessus en une seule commande. Équivaut à :
```bash
git branch fonctionnalite-1   # crée la branche
git checkout fonctionnalite-1 # bascule dessus
```
**Résultat :** On est maintenant sur `fonctionnalite-1`, qui pointe sur le même commit que `main` (`b28023e`).

---

### `git push origin fonctionnalite-1`
```bash
git push origin fonctionnalite-1
```
**Ce que ça fait :** Publie la branche `fonctionnalite-1` sur GitHub, ce qui permet d'ouvrir une Pull Request.

> **Note :** Cette branche ne contient aucun commit propre — elle sert de **point de départ** pour les branches suivantes.

---

## Étape 3 — Branche `fonctionnalite-2`

### Contexte
On crée `fonctionnalite-2` depuis `fonctionnalite-1` (même point de départ que `main`). Cette branche reçoit deux commits successifs.

---

### Création de la branche
```bash
git checkout -b fonctionnalite-2
```
**Résultat :** Nouvelle branche créée depuis `fonctionnalite-1` (commit `b28023e`).

---

### Premier commit sur v2
```bash
# Modification de README.md...
git add README.md
git commit -m "Ajout des fonctionnalités de la v2"
```
**Commit créé :** `27111b9`  
**Ce qui change :** Ajout d'une ligne dans `README.md` (+1 ligne).

---

### Deuxième commit sur v2
```bash
# Modification de README.md...
git add README.md
git commit -m "Ajustement et finition de la v2"
```
**Commit créé :** `3f520e3`  
**Ce qui change :** Modification d'une ligne existante dans `README.md`.

---

### Publication de la branche
```bash
git push origin fonctionnalite-2
```
**Résultat :** La branche avec ses 2 commits est visible sur GitHub. Une Pull Request peut être ouverte.

---

## Étape 4 — Branche `fonctionnalite-3`

### Contexte
`fonctionnalite-3` est créée **depuis la fin de `fonctionnalite-2`** — elle hérite donc de ses deux commits. On ajoute deux nouveaux commits.

---

### Création depuis fonctionnalite-2
```bash
git checkout -b fonctionnalite-3
```
**Résultat :** Nouvelle branche depuis le commit `3f520e3` (dernier commit de `fonctionnalite-2`).

---

### Premier commit sur v3
```bash
git add README.md
git commit -m "Début des travaux sur la v3"
```
**Commit créé :** `ae42337`

---

### Deuxième commit sur v3
```bash
git add README.md
git commit -m "Ajout du texte de test sur v3"
```
**Commit créé :** `287a06a`

---

### Publication de la branche
```bash
git push origin fonctionnalite-3
```

---

## Étape 5 — Branche `fonctionnalite-4` et résolution de conflit

### Contexte
C'est l'étape la plus complexe. `fonctionnalite-4` est créée depuis le **premier commit** (`b28023e`), en repassant par `fonctionnalite-1`. Elle va modifier le même fichier que `fonctionnalite-3`, créant un **conflit de fusion**.

---

### Retour sur fonctionnalite-1 puis création de fonctionnalite-4
```bash
git checkout fonctionnalite-1
git checkout -b fonctionnalite-4
```
**Ce que ça fait :** On revient sur `fonctionnalite-1` (qui pointe sur `b28023e`) pour créer `fonctionnalite-4` à partir de ce point, **indépendamment** de `fonctionnalite-2` et `fonctionnalite-3`.  
**Pourquoi :** Simuler deux développeurs qui travaillent en parallèle sur le même fichier — c'est ce qui va provoquer le conflit.

---

### Premier commit sur v4
```bash
git add README.md
git commit -m "Ajout du texte concurrent sur v4"
```
**Commit créé :** `68938d1`  
**Ce qui change :** Ajout d'une ligne dans `README.md` — ligne qui entre en conflit avec le contenu de `fonctionnalite-3`.

---

### Publication intermédiaire
```bash
git push origin fonctionnalite-4
```

---

### `git merge` — Fusion avec conflit

```bash
git merge fonctionnalite-3
```
**Ce que ça fait :** Tente d'intégrer les commits de `fonctionnalite-3` dans `fonctionnalite-4`.  
**Résultat :** Git détecte que les deux branches ont modifié la même zone de `README.md` → **CONFLIT**.

Git marque le fichier en conflit avec des balises spéciales :
```
<<<<<<< HEAD
Ceci est le texte de la branche 4.
=======
Ceci est le texte de la branche 3.
>>>>>>> fonctionnalite-3
```

- `<<<<<<< HEAD` : contenu de la branche courante (`fonctionnalite-4`)  
- `=======` : séparateur  
- `>>>>>>> fonctionnalite-3` : contenu de la branche à fusionner

**Résolution :** On édite manuellement le fichier pour garder les deux contenus (ou choisir l'un des deux), puis on supprime les balises.

---

### Validation de la résolution du conflit
```bash
git add README.md
git commit -m "Résolution du conflit et fusion de v3 dans v4"
```
**Commit créé :** `e20685b` — c'est un **merge commit** (il a deux parents : `68938d1` et `287a06a`).  
**Ce qui change :** +4 lignes, -1 ligne dans `README.md` — les deux contenus sont maintenant fusionnés.

---

### Publication après résolution
```bash
git push origin fonctionnalite-4
```

---

### Suite des commits sur fonctionnalite-4
```bash
git add README.md
git commit -m "Ajout de details sur l avancement"
git push origin fonctionnalite-4
```
**Commit créé :** `e0581d3` — Ajout de 2 lignes.

```bash
git add README.md
git commit -m "Preparation de la version finale"
git push origin fonctionnalite-4
```
**Commit créé :** `20a858d` — Ajout de 3 lignes, modification de 1.

---

## Étape 6 — Branche `fonctionnalite-5`

### Contexte
Dernière branche. Créée depuis la fin de `fonctionnalite-4`, elle porte le commit de clôture de l'exercice.

---

### Création depuis fonctionnalite-4
```bash
git checkout -b fonctionnalite-5
```
**Résultat :** Nouvelle branche depuis le commit `20a858d` (dernier commit de `fonctionnalite-4`).

---

### Commit final
```bash
git add README.md
git commit -m "Commit 10: Fin de l entrainement Git"
```
**Commit créé :** `281a563` — C'est le **10e commit** de l'exercice (en comptant le merge commit).

---

### Publication
```bash
git push origin fonctionnalite-5
```

---

## Étape 7 — Fusion finale sur `main`

### Contexte
Sur GitHub, une **Pull Request #3** est ouverte pour fusionner `fonctionnalite-5` dans `main`. Elle est acceptée et mergée via l'interface GitHub.

---

### Pull Request GitHub (interface web)
Une PR permet à d'autres développeurs de **relire le code** avant qu'il n'intègre `main`. GitHub crée automatiquement un **merge commit** lors de la fusion :

**Commit créé :** `7dda6fc` — `Merge pull request #3 from fannysaez/fonctionnalite-5`

---

### `git checkout` — Retour sur main
```bash
git checkout main
```
**Ce que ça fait :** Bascule la copie de travail locale sur la branche `main`.

---

### `git pull` — Récupération du merge
```bash
git pull origin main
```
**Ce que ça fait :** Récupère les nouveaux commits depuis GitHub (dont le merge commit de la PR #3) et les intègre dans la branche locale `main`.  
**Résultat :** La branche locale `main` est maintenant à jour avec le dépôt distant.

---

### `git reset` — Vérification d'état
```bash
git reset HEAD
```
**Ce que ça fait :** Remet la zone de staging à l'état du dernier commit, sans toucher aux fichiers. Utilisé ici pour s'assurer que rien n'est accidentellement stagé.  
**Impact :** Aucun fichier modifié — le dépôt est propre.

---

## Récapitulatif de toutes les commandes

| # | Commande | Branche | Effet |
|---|---|---|---|
| 1 | `git init` | — | Initialise le dépôt local |
| 2 | `git add README.md` | `main` | Stage le README |
| 3 | `git commit -m "first commit"` | `main` | Premier commit (`b28023e`) |
| 4 | `git push origin main` | `main` | Publie sur GitHub |
| 5 | `git checkout -b fonctionnalite-1` | `main` → `fonctionnalite-1` | Crée et bascule sur la branche |
| 6 | `git push origin fonctionnalite-1` | `fonctionnalite-1` | Publie la branche |
| 7 | `git checkout -b fonctionnalite-2` | `fonctionnalite-1` → `fonctionnalite-2` | Crée et bascule |
| 8 | `git add` + `git commit` ×2 | `fonctionnalite-2` | 2 commits (`27111b9`, `3f520e3`) |
| 9 | `git push origin fonctionnalite-2` | `fonctionnalite-2` | Publie |
| 10 | `git checkout -b fonctionnalite-3` | `fonctionnalite-2` → `fonctionnalite-3` | Crée et bascule |
| 11 | `git add` + `git commit` ×2 | `fonctionnalite-3` | 2 commits (`ae42337`, `287a06a`) |
| 12 | `git push origin fonctionnalite-3` | `fonctionnalite-3` | Publie |
| 13 | `git checkout fonctionnalite-1` | → `fonctionnalite-1` | Retour sur fonctionnalite-1 |
| 14 | `git checkout -b fonctionnalite-4` | `fonctionnalite-1` → `fonctionnalite-4` | Crée depuis le 1er commit |
| 15 | `git add` + `git commit` | `fonctionnalite-4` | Commit concurrent (`68938d1`) |
| 16 | `git push origin fonctionnalite-4` | `fonctionnalite-4` | Publie |
| 17 | `git merge fonctionnalite-3` | `fonctionnalite-4` | **Déclenche un conflit** |
| 18 | Résolution manuelle | `fonctionnalite-4` | Édition du fichier en conflit |
| 19 | `git add` + `git commit` | `fonctionnalite-4` | Merge commit (`e20685b`) |
| 20 | `git push origin fonctionnalite-4` | `fonctionnalite-4` | Publie |
| 21 | `git add` + `git commit` ×2 | `fonctionnalite-4` | 2 commits (`e0581d3`, `20a858d`) |
| 22 | `git push` ×2 | `fonctionnalite-4` | Publie les 2 commits |
| 23 | `git checkout -b fonctionnalite-5` | `fonctionnalite-4` → `fonctionnalite-5` | Crée et bascule |
| 24 | `git add` + `git commit` | `fonctionnalite-5` | Commit final (`281a563`) |
| 25 | `git push origin fonctionnalite-5` | `fonctionnalite-5` | Publie |
| 26 | Pull Request #3 (GitHub) | `fonctionnalite-5` → `main` | Merge via interface web |
| 27 | `git checkout main` | → `main` | Retour sur main |
| 28 | `git pull origin main` | `main` | Récupère le merge de la PR |
| 29 | `git reset HEAD` | `main` | Vérifie l'état du staging |

---

## Lexique Git

| Terme | Définition |
|---|---|
| **dépôt (repository)** | Dossier versionné contenant l'historique complet du projet |
| **commit** | Instantané enregistré dans l'historique avec un message et un identifiant unique (SHA) |
| **branche** | Ligne de développement indépendante — un simple pointeur vers un commit |
| **HEAD** | Pointeur vers le commit actuel (ou la branche actuelle) |
| **staging / index** | Zone intermédiaire où on prépare les fichiers avant un commit |
| **origin** | Nom par défaut du dépôt distant (GitHub) |
| **merge** | Fusion de deux branches — crée un commit avec deux parents si nécessaire |
| **conflit** | Quand deux branches modifient la même zone d'un fichier — Git demande à l'humain de choisir |
| **Pull Request (PR)** | Proposition de fusion sur GitHub, avec discussion et relecture avant intégration |
| **push** | Envoyer des commits locaux vers le dépôt distant |
| **pull** | Récupérer les commits distants et les intégrer localement |
| **reflog** | Journal interne de Git qui enregistre tous les déplacements de HEAD — très utile pour récupérer un commit perdu |

---

*Documentation générée à partir du reflog et de l'historique complet du dépôt — 29 juin 2026.*
