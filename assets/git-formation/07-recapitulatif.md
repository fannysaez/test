# 07 — Récapitulatif & Lexique

## Toutes les commandes utilisées

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
| **fetch** | Télécharger les changements distants sans les intégrer |
| **reflog** | Journal interne de Git enregistrant tous les déplacements de HEAD — utile pour récupérer un commit perdu |
| **SHA / hash** | Identifiant unique d'un commit (ex: `b28023e`) — calculé à partir du contenu |
| **remote** | Dépôt distant (GitHub, GitLab…) lié au dépôt local |
| **stash** | Mise de côté temporaire de modifications non commitées — permet de changer de branche sans committer |
| **stash pop** | Restaure les modifications mises de côté par `git stash` et les supprime de la pile |

---

<p align="center">
  <a href="06-finalisation.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="08-evolution-readme.md"><img src="https://img.shields.io/badge/-SUIVANT-0d8f91?style=for-the-badge" alt="Suivant"></a>
</p>
