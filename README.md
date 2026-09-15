# Pawrise — Configuration GitHub de l'organisation

Ce dépôt contient la configuration GitHub partagée ainsi que les règles de contribution utilisées au sein de l'organisation **Pawrise**.

## Objectif

Le dépôt `.github` centralise les conventions communes utilisées par les différents dépôts de l'organisation Pawrise.

Il permet notamment de définir :

* les règles de contribution ;
* les modèles de Pull Request ;
* les modèles d'Issues ;
* la procédure de signalement des vulnérabilités ;
* les conventions de développement partagées.

Ces éléments sont utilisés comme configuration par défaut par les dépôts Pawrise qui ne définissent pas leur propre configuration.

## Structure du dépôt

```text
.
├── README.md
├── CONTRIBUTING.md
├── SECURITY.md
├── PULL_REQUEST_TEMPLATE.md
└── .github/
    └── ISSUE_TEMPLATE/
        ├── bug.yml
        ├── feature.yml
        └── config.yml
```

## Workflow de développement

Pawrise utilise un workflow basé sur les Pull Requests.

```text
branche feature / fix / chore
            │
            ▼
       Pull Request
            │
            ▼
   Vérifications automatiques
            │
            ▼
        Code review
            │
            ▼
           main
```

Les modifications directes sur la branche `main` doivent être évitées.

Chaque évolution doit être développée dans une branche dédiée puis intégrée via une Pull Request.

## Convention de nommage des branches

Les branches doivent suivre la convention suivante :

```text
feature/<nom-feature>
fix/<nom-bug>
chore/<nom-tache>
refactor/<scope>
docs/<scope>
```

Exemples :

```text
feature/pet-profile
fix/gps-location-update
chore/update-dependencies
docs/api-documentation
```

## Convention des commits

Pawrise utilise une convention inspirée de **Conventional Commits**.

Exemples :

```text
feat: ajout de l'endpoint d'activité animale
fix: correction de la validation du token collier
docs: mise à jour de la documentation d'architecture
ci: ajout de la CI du backend
refactor: simplification du service d'authentification
chore: mise à jour des dépendances
```

## Pull Requests

Toute modification importante doit passer par une Pull Request.

Une Pull Request doit :

* décrire clairement les modifications apportées ;
* rester centrée sur un objectif précis ;
* passer les vérifications automatiques disponibles ;
* ne contenir aucun secret ou identifiant sensible ;
* mettre à jour la documentation si nécessaire ;
* être revue avant fusion.

La structure par défaut des Pull Requests est définie dans `PULL_REQUEST_TEMPLATE.md`.

## Issues

Des modèles d'Issues sont disponibles pour :

* signaler un bug ;
* proposer une nouvelle fonctionnalité.

Ces modèles permettent de garder des Issues cohérentes et suffisamment détaillées dans l'ensemble des dépôts Pawrise.

## Dépôts Pawrise

L'organisation Pawrise est notamment composée des dépôts suivants :

* `pawrise-backend`
* `pawrise-data`
* `pawrise-assistant`
* `pawrise-sense`
* `pawrise-mobile`
* `pawrise-vet-portal`
* `pawrise-platform`
* `pawrise-website`

Chaque dépôt peut définir sa propre configuration lorsque cela est nécessaire.

## DevOps

La configuration liée à l'infrastructure, au déploiement, à Kubernetes, au GitOps, à l'observabilité et à la plateforme est maintenue séparément dans :

```text
pawrise-platform
```

Le dépôt `.github` est dédié à la gouvernance GitHub, aux conventions de développement et aux standards communs de l'organisation.
