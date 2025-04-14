# Chapitre 3 – Automatiser les tests avec GitHub Actions

Bienvenue dans ce nouveau chapitre !  
Dans un projet professionnel, automatiser les tests à chaque commit est indispensable. C’est exactement ce que nous allons faire ici grâce à **GitHub Actions**.  
Nous allons configurer un workflow qui s'exécutera à chaque push pour tester automatiquement notre code avec **Pytest**, sur notre environnement Dockerisé.

---

## 🎯 User Story

> En tant que développeur, je veux que mes tests s'exécutent automatiquement à chaque push ou pull request, afin de m'assurer que le code reste fonctionnel et fiable.

---

## ✅ Tâches

1. Créer le dossier `.github/workflows`
2. Ajouter un fichier `tests.yml` pour définir le pipeline GitHub Actions
3. Configurer un service PostgreSQL dans le workflow
4. Lancer les tests avec Pytest
5. Vérifier le retour de l'exécution des tests

---

## 🧪 Test (TDD)

```python
"""
test_dummy.py – Test de base pour vérifier que Pytest est bien exécuté par GitHub Actions
"""

def test_always_passes():
    """Ce test est utilisé pour valider que la CI fonctionne"""
    assert True


⚙️ Code : GitHub Actions – Configuration
Crée un fichier .github/workflows/tests.yml :

```yaml
name: Django Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest

    services:
      postgres:
        image: postgres:14
        env:
          POSTGRES_USER: django
          POSTGRES_PASSWORD: django
          POSTGRES_DB: django_db
        ports: ['5432:5432']
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5

    steps:
      - uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run tests
        env:
          DATABASE_URL: postgres://django:django@localhost:5432/django_db
        run: |
          pytest
```

⚙️ Code : GitHub Actions – Configuration
Crée un fichier .github/workflows/tests.yml :
```bash
git add .github/workflows/tests.yml
git commit -m "✨ Mise en place de l'intégration continue avec GitHub Actions"
```