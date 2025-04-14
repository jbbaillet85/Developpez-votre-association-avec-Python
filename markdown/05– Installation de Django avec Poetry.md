# Chapitre 6 – Installation de Django avec Poetry

## 🎯 User Story

En tant que développeur de l'association,  
je veux installer Django avec Poetry dans mon environnement Ubuntu  
afin de disposer d'une gestion professionnelle des dépendances pour notre projet.

---

## ✅ Tâches

- Installer Poetry
- Initialiser le projet avec Poetry
- Ajouter Django comme dépendance
- Lancer le projet avec `runserver`
- Générer un fichier `requirements.txt` pour Docker
- Tester que Django fonctionne avec un test automatisé
- Versionner le tout avec un commit propre

---

## 🔧 Étape 1 : Installer Poetry

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

Ajoute ensuite Poetry au PATH (si ce n’est pas automatique) :
```bash
export PATH="$HOME/.local/bin:$PATH"
```

Vérifie l’installation :
```bash
poetry --version
```

## 🛠 Étape 2 : Initialiser un projet Python avec Poetry
Depuis le dossier racine de ton dépôt :

```bash
poetry init
```

Réponds aux questions, ou utilise l’option automatique :
```bash
poetry init --no-interaction
```

📦 Étape 3 : Ajouter Django
```bash
# Cela installe Django et l’ajoute automatiquement dans le fichier pyproject.toml.
poetry add django
```

## 🔨 Étape 4 : Initialiser le projet Django
Crée un dossier src et navigue dedans :

```bash
mkdir src && cd src
poetry run django-admin startproject config .
```
## 🚀 Étape 5 : Lancer le serveur Django
Dans le répertoire src :

```bash
poetry run python manage.py runserver
Accède à : http://127.0.0.1:8000
```
## 📄 Étape 6 : Générer un requirements.txt (pour Docker)
```bash
poetry export -f requirements.txt --output requirements.txt
```

## ✅ Test (TDD)
Créons un premier test pour vérifier que Django est bien installé et fonctionne.

tests/test_homepage.py

```python
"""
Test de vérification de la page d'accueil de Django.
"""

from django.test import Client, TestCase

class HomepageTestCase(TestCase):
    def test_homepage_status_code(self):
        """
        Vérifie que la page d'accueil renvoie bien un code HTTP 200.
        """
        client = Client()
        response = client.get('/')
        self.assertEqual(response.status_code, 200)
```
⚠️ Si le dossier tests/ n'existe pas, crée-le dans le dossier src.

## ✅ Code source
Rien de plus à ce stade, mis à part la structure Django générée dans src/asso_project.

## 💻 Code

```bash
poetry add django
poetry run django-admin startproject config .
poetry run python manage.py runserver
```

---

### 📂 Arborescence obtenue

```
.
├── config/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── manage.py
```

## ✅ Message de commit
```bash
git add .
git commit -m "feat: installation de Django avec Poetry et configuration initiale du projet"
```