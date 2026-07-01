# 08 — Évolution du fichier `README.md` par branche

Ce fichier retrace **l'état réel du `README.md`** après chaque étape clé de l'exercice.  
C'est ce fichier qui a servi de terrain d'entraînement tout au long — modifié, fusionné, mis en conflit, puis résolu.

---

## Après `first commit` — `main` / `fonctionnalite-1`

```
(fichier vide)
```

---

## Après `fonctionnalite-2` — 2 commits

```
Ceci est le texte de la branche 4.
Version 2.1.1
```

> `fonctionnalite-2` a introduit le contenu de base : une première ligne et un numéro de version.

---

## Après `fonctionnalite-3` — 2 commits (hérite de v2)

```
Ceci est le texte de la branche 4.
Version 2.1.1

Ceci est le texte de la branche 3.
```

> `fonctionnalite-3` a ajouté la ligne "branche 3" — c'est cette ligne qui créera le conflit avec `fonctionnalite-4`.

---

## Sur `fonctionnalite-4` — avant le merge

```
Ceci est le texte de la branche 4.
```

> `fonctionnalite-4` est repartie du premier commit (fichier vide) et a écrit sa propre ligne, **en parallèle** de `fonctionnalite-3`. Les deux branches ont modifié la même zone : conflit garanti.

---

## Pendant le conflit — ce que Git écrit dans le fichier

```
<<<<<<< HEAD
Ceci est le texte de la branche 4.
=======
Ceci est le texte de la branche 3.

Mise à jour v4.1
>>>>>>> fonctionnalite-3
```

> Git a marqué les deux versions. Il faut éditer manuellement pour fusionner ou choisir.

---

## Après résolution du conflit

```
Ceci est le texte de la branche 4.

Ceci est le texte de la branche 3.

Mise à jour v4.1
```

> Les deux contenus coexistent. La résolution a choisi de **tout garder**.

---

## Après les commits suivants sur `fonctionnalite-4`

```
Ceci est le texte de la branche 4.
Version 2.1.1

Ceci est le texte de la branche 3.

Mise à jour v4.1

Ligne de préparation pour le conflit final
```

---

## État final — après merge de `fonctionnalite-5` dans `main`

```
Ceci est le texte de la branche 4.
Version 2.1.1

Ceci est le texte de la branche 3.

Mise à jour v4.1

Ligne de préparation pour le conflit final

Fin de l'exercice !
```

> C'est le contenu actuel du fichier — résultat de l'ensemble des branches, commits, conflits et merges réalisés pendant cet entraînement.

---

<p align="center">
  <a href="07-recapitulatif.md"><img src="https://img.shields.io/badge/-PR%C3%89C%C3%89DENT-0d8f91?style=for-the-badge" alt="Précédent"></a> &nbsp;&nbsp; <a href="../../README.md"><img src="https://img.shields.io/badge/-RETOUR-0d8f91?style=for-the-badge" alt="Retour à l'index"></a>
</p>
