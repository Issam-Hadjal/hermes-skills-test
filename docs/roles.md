# Rôles du pipeline multi-agents

Ce document décrit les quatre rôles du pipeline GitHub multi-agents, leurs
responsabilités et leurs permissions.

## Dev-Bot

Implémenteur autonome. Reçoit une carte kanban, écrit le code, exécute les
tests, commit, et ouvre une pull request vers `dev`.

**Peut :**
- lire les issues et les cartes kanban
- cloner le dépôt et travailler dans son workspace
- créer, modifier et supprimer des fichiers dans ses branches
- publier une branche et ouvrir une PR vers `dev`
- commenter sur les issues et les PRs
- relancer la CI
- signaler un blocage via kanban_block

**Ne peut pas :**
- approuver une PR (même la sienne)
- merger une PR
- modifier les règles de protection ou les workflows CI
- accéder aux secrets ou tokens

## Doc-Bot

Rédacteur de documentation. Crée, met à jour et vérifie la cohérence de la
documentation du projet.

**Peut :**
- lire les issues et les cartes kanban
- créer et modifier des fichiers de documentation
- ouvrir une PR vers `dev` pour ses changements
- relancer la CI

**Ne peut pas :**
- implémenter du code fonctionnel
- approuver ou merger une PR
- modifier les workflows CI

## Review-Bot

Relecteur de code. Examine les PRs, vérifie la qualité, la sécurité et la
conformité aux conventions du projet.

**Peut :**
- lire les PRs, les commentaires et les rapports de CI
- approuver ou demander des changements sur une PR
- commenter sur le code (revue ligne par ligne)

**Ne peut pas :**
- merger une PR
- approuver ses propres PR (la règleset le bloque)
- modifier le code directement
- modifier les règles de protection

## Merge-Bot

Fusionneur. Intègre les PRs approuvées vers `dev`, puis `dev` vers `main`
lorsque le cycle est complet.

**Peut :**
- merger une PR vers `dev` (squash, avec commit_title obligatoire)
- merger `dev` vers `main`
- lire l'état des PRs et de la CI

**Ne peut pas :**
- modifier le code
- approuver des PRs
- modifier les workflows ou les règles de protection

---

## Principe général

Chaque rôle est strictement séparé. Aucun agent ne peut cumuler les permissions
d'un autre rôle. GitHub Rulesets enforce ces séparations au niveau du dépôt.
