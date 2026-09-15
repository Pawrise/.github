# Guide de contribution — Pawrise

Ce document définit les règles communes de développement utilisées dans les différents dépôts de l'organisation afin de conserver un workflow cohérent, lisible et maintenable.

## Workflow général

Les développements doivent être réalisés dans une branche dédiée puis intégrés via une **Pull Request**.

Le workflow recommandé est le suivant :

```text
main
 ↑
Pull Request
 ↑
feature / fix / chore / refactor / docs
```

Les développements directs sur `main` sont à éviter.

## Branches

Chaque modification doit être réalisée dans une branche dédiée.

### Convention de nommage

Les branches doivent suivre le format :

```text
<type>/<description>
```

Types recommandés :

```text
feature/    nouvelle fonctionnalité
fix/        correction d'un bug
refactor/   modification interne sans changement fonctionnel
chore/      maintenance ou tâche technique
docs/       documentation
ci/         CI/CD et automatisation
```

Exemples :

```text
feature/pet-profile
feature/activity-history
fix/gps-position-update
refactor/auth-service
docs/api-documentation
ci/backend-pipeline
```

Les noms de branches doivent être :

* courts ;
* explicites ;
* écrits en minuscules ;
* séparés par des tirets.

## Commits

Les messages de commit suivent une convention inspirée de **Conventional Commits**.

Format :

```text
<type>: <description>
```

Types principaux :

| Type       | Utilisation                                     |
| ---------- | ----------------------------------------------- |
| `feat`     | ajout d'une fonctionnalité                      |
| `fix`      | correction d'un bug                             |
| `docs`     | documentation                                   |
| `refactor` | refactorisation sans modification fonctionnelle |
| `test`     | ajout ou modification de tests                  |
| `ci`       | CI/CD et automatisation                         |
| `chore`    | maintenance, dépendances, configuration         |

Exemples :

```text
feat: ajout de l'historique d'activité
fix: correction de la validation du token collier
docs: mise à jour de l'architecture backend
test: ajout des tests du service utilisateur
ci: ajout du pipeline backend
chore: mise à jour des dépendances
```

Les messages doivent décrire clairement la modification réalisée.

Éviter les messages tels que :

```text
update
fix
fix 2
test
jte jure ça marche
modif 3
```

## Pull Requests

Toute modification destinée à être intégrée dans `main` doit passer par une Pull Request.

Une Pull Request doit :

* avoir un titre explicite ;
* décrire les changements réalisés ;
* être limitée autant que possible à un objectif précis ;
* référencer une Issue lorsque cela est pertinent ;
* passer les vérifications automatiques disponibles ;
* être relue avant fusion.

Le modèle défini dans `PULL_REQUEST_TEMPLATE.md` doit être complété lors de la création de la Pull Request.

## Revue de code

Avant fusion, le code doit être relu par au moins un autre membre de l'équipe lorsque cela est possible.

La revue doit notamment vérifier :

* la compréhension du code ;
* le respect des conventions du projet ;
* l'absence de régression évidente ;
* la présence de tests lorsque nécessaire ;
* l'absence d'informations sensibles ;
* la cohérence avec l'architecture Pawrise.

Les remarques de revue doivent rester techniques, précises et constructives.

## Tests et validation

Avant d'ouvrir une Pull Request, le contributeur doit vérifier que :

* le projet compile ou démarre correctement ;
* les tests existants passent ;
* les nouvelles fonctionnalités sont testées lorsque cela est pertinent ;
* aucune régression connue n'a été introduite.

Les pipelines CI automatiseront progressivement ces vérifications.

Une Pull Request dont les contrôles obligatoires échouent ne doit pas être fusionnée.

## Secrets et informations sensibles

Aucun secret ne doit être ajouté dans le code ou dans l'historique Git.

Cela concerne notamment :

* mots de passe ;
* clés API ;
* tokens ;
* clés privées ;
* certificats privés ;
* secrets Kubernetes ;
* identifiants de bases de données ;
* fichiers `.env` contenant des valeurs réelles.

Les variables sensibles doivent être fournies par les mécanismes prévus par l'environnement ou la plateforme DevOps.

Les fichiers `.env` locaux doivent être exclus via `.gitignore`.

Lorsqu'un exemple de configuration est nécessaire, utiliser un fichier tel que :

```text
.env.example
```

avec uniquement des valeurs fictives :

```text
DATABASE_URL=
API_KEY=
JWT_SECRET=
```

## Dépendances

Lors de l'ajout d'une nouvelle dépendance :

* vérifier qu'elle est réellement nécessaire ;
* privilégier les bibliothèques maintenues ;
* éviter les dépendances obsolètes ;
* vérifier les vulnérabilités connues lorsque cela est possible ;
* documenter les dépendances structurantes.

Les mises à jour majeures doivent être testées avant intégration.

## Documentation

Toute modification importante de comportement, d'architecture ou de configuration doit être accompagnée d'une mise à jour de la documentation concernée.

Cela inclut notamment :

* endpoints d'API ;
* variables d'environnement ;
* architecture ;
* procédure de déploiement ;
* configuration DevOps ;
* nouvelles dépendances importantes.

## Issues

Les Issues doivent être utilisées pour tracer :

* les bugs ;
* les fonctionnalités ;
* les améliorations ;
* les tâches techniques importantes.

Les modèles disponibles dans `.github/ISSUE_TEMPLATE/` doivent être utilisés lorsque cela est possible.

Une Issue doit contenir suffisamment d'informations pour permettre à un autre membre de l'équipe de comprendre le besoin.

## Sécurité

Les vulnérabilités de sécurité ne doivent pas être publiées dans une Issue classique.

La procédure définie dans `SECURITY.md` doit être suivie.

En cas de doute sur une information sensible, ne pas la publier dans GitHub avant validation.

## Fusion des Pull Requests

Une Pull Request peut être fusionnée lorsque :

* les vérifications automatiques obligatoires sont validées ;
* les éventuels conflits sont résolus ;
* les discussions importantes sont résolues ;
* la revue de code requise est approuvée.

La branche associée peut être supprimée après fusion.

## Priorité des règles

Les règles définies dans ce dépôt représentent les conventions par défaut de l'organisation Pawrise.

Un dépôt peut définir des règles supplémentaires lorsqu'il possède des contraintes spécifiques.

Par exemple :

* développement embarqué pour `pawrise-sense` ;
* règles Python pour `pawrise-data` ou `pawrise-assistant` ;
* règles frontend pour `pawrise-vet-portal` ;
* règles d'infrastructure pour `pawrise-platform`.

Dans ce cas, les règles spécifiques du dépôt complètent les règles générales définies ici.
