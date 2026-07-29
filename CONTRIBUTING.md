# Contributing

Merci de contribuer à **hermes-skills-test**. Ce document définit les conventions à respecter pour toute contribution.

## Format des messages de commit

Utiliser les [Conventional Commits](https://www.conventionalcommits.org/).

```
type(scope): résumé impératif

Corps : expliquer ce qui change et pourquoi, pas comment.
Chaque ligne ~72 caractères.

Pied (optionnel) : Closes #42 / BREAKING CHANGE: ...
```

**Règles :**
- **Sujet ≤ 70 caractères**, présent impératif (ex. `Ajoute` pas `Ajouté`), sans point final.
- **Type obligatoire**, scope optionnel, deux-points + espace après le type.
- **Corps** : décrire le quoi et le pourquoi ; les relecteurs et `git log` en dépendent.

Les 12 types :

| Type       | Usage                                |
|------------|--------------------------------------|
| `feat`     | nouvelle fonctionnalité              |
| `fix`      | correction de bug                    |
| `refactor` | changement de code sans effet métier |
| `docs`     | documentation uniquement              |
| `test`     | ajout / correction de tests          |
| `chore`    | outillage, maintenance               |
| `ci`       | configuration CI/CD                  |
| `build`    | système de compilation, dépendances  |
| `perf`     | amélioration de performance          |
| `style`    | formatage, pas de changement logique |
| `deps`     | mise à jour de dépendances           |
| `revert`   | annulation d'un commit précédent     |

## Convention de nommage des branches

Format : `<type>/<description-courte-en-kebab-case>` — minuscules, caractères alphanumériques et tirets.

Exemples :
- `feat/add-user-authentication`
- `fix/login-redirect-loop`
- `docs/update-readme`

## Taille maximale d'une pull request

Une pull request ne doit pas dépasser **500 lignes modifiées** (addition + suppression, `git diff --stat`). Au-delà, la contribution doit être découpée en plusieurs PR plus petites et indépendantes.

## Processus

1. Créer une branche depuis `dev` avec la convention ci-dessus.
2. Commiter localement en suivant Conventional Commits.
3. Publier la branche (`git push` géré par l'infrastructure).
4. Ouvrir une pull request ciblant `dev`.
5. Attendre la revue d'un autre contributeur.
6. Une fois approuvée, la PR est fusionnée (squash merge) par l'infrastructure.
