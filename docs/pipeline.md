# Pipeline multi-agents

Le dépôt suit un flux à trois branches :

1. **feature** — chaque agent de développement (Dev-Bot, Doc-Bot, etc.) travaille
   sur sa propre branche issue de `dev`. Les changements sont atomiques, un seul
   commit par PR.
2. **dev** — branche d'intégration. Les PRs depuis les branches feature y sont
   mergeées (squash). La CI vérifie la cohésion avant de passer à `main`.
3. **main** — branche de release. Un reviewer humain ou un agent dédié fusionne
   `dev` vers `main` après validation.

Rôles par identité :

- **Dev-Bot** : implémente le code, écrit les tests, ouvre la PR vers `dev`.
- **Doc-Bot** : rédige ou met à jour la documentation.
- **Review-Bot** : relit et approuve la PR. Ne peut pas approuver ses propres PR.
- **Merge-Bot** : fusionne la PR approuvée vers `dev`, puis fusionne `dev` vers
  `main` lorsque le cycle est complet.
