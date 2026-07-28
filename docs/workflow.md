# Parcours d'une demande (request pipeline)

Ce document décrit le cycle de vie complet d'une demande, de la création
d'un ticket sur GitHub jusqu'à son intégration dans la branche `main`.

## 1. Création du ticket (issue)

Une demande commence par la création d'une **issue** sur GitHub. Le ticket
contient une description fonctionnelle et les critères d'acceptation.
L'issue est associée au projet et priorisée par l'équipe.

## 2. Implémentation par le rôle Dev

Le rôle **Dev-Bot** prend en charge l'issue et réalise les étapes suivantes :

- Crée une branche de travail à partir de `main`.
- Implémente la fonctionnalité dans son espace de travail local.
- Valide localement ses changements avec `git commit`.
- Publie sa branche sur le dépôt distant.
- Ouvre une **Pull Request** (PR) ciblant la branche `dev`.

Une fois la PR ouverte, Dev-Bot passe la main au réviseur.

## 3. Revue et intégration dans `dev`

Le rôle **Review-Bot** examine la PR :

- Vérifie la couverture fonctionnelle (critères d'acceptation).
- Vérifie la qualité du code et l'absence de régressions.
- Vérifie que les tests passent et que la CI est verte.
- Peut demander des modifications via des commentaires de revue.
- Approuve la PR une fois satisfait.
- Fusionne la PR dans la branche `dev`.

## 4. Intégration de `dev` vers `main`

Le rôle **Merge-Bot** assure le passage de `dev` vers `main` :

- Vérifie que `dev` contient les changements validés par le réviseur.
- Ouvre une PR de `dev` vers `main`.
- Vérifie l'état de la CI sur cette PR.
- Fusionne la PR vers `main` une fois la CI verte.

La boucle est ainsi bouclée : la demande est passée d'une simple issue
à un changement livré dans `main`, prêt à être déployé.
