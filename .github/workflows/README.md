# Reusable workflows Pawrise

CI centralisée pour toute l'organisation. Ces workflows sont écrits **une seule fois**
ici, et appelés par chaque repo avec un fichier appelant de quelques lignes
(`.github/workflows/ci.yml`). Corriger un bug de CI = 1 seul endroit.

> Prérequis : dans chaque repo appelant → *Settings → Actions → General →
> « Access » → Allow enterprise/organization repositories* pour autoriser l'appel
> des workflows de ce repo `.github`.

## Workflows disponibles

| Workflow | Pour | Étapes |
|---|---|---|
| `secret-scan.yml` | **tous** les repos | gitleaks (scan de secrets) |
| `python-ci.yml` | pawrise-data, pawrise-assistant | uv sync · ruff (lint) · ruff format · pytest |
| `rust-ci.yml` | pawrise-backend | fmt · clippy · test · cargo audit |
| `node-ci.yml` | pawrise-vet-portal, website | npm ci · lint · typecheck · test · build |

> À venir quand les repos auront du code : `mobile` (Kotlin/Android, Swift/iOS)
> et `firmware` (C/Zephyr). CI plus spécialisée, on l'ajoutera le moment venu.

## Exemple d'appelant

Fichier `.github/workflows/ci.yml` dans le repo consommateur :

```yaml
name: CI
on:
  pull_request:
  push:
    branches: [main]

jobs:
  secret-scan:
    uses: Pawrise/.github/.github/workflows/secret-scan.yml@main

  python:
    uses: Pawrise/.github/.github/workflows/python-ci.yml@main
    with:
      python-version: "3.12"
```

> Le chemin `Pawrise/.github/.github/workflows/...` a bien un double `.github` :
> le 1er est le **nom du repo**, le 2ème le **dossier** des workflows.

## Politique actuelle (phase 1)

- Lint **bloquant**, format **non bloquant** (à durcir quand la base de code est alignée).
- Tests tolérants tant qu'il n'y en a pas encore.
- Pas encore de build Docker / push GHCR : ça viendra en **phase 2** (sur merge `main`),
  et se branchera sur ces mêmes workflows.
