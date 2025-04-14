# Chapitre 2 – Mise en place de l’environnement de développement (Ubuntu + GitHub + Docker)

---

## 🎯 User story

**En tant que** développeur d’une application pour une association,  
**je veux** mettre en place un environnement de développement stable sous Ubuntu,  
**afin de** pouvoir travailler efficacement, collaborer via GitHub, et tester localement avec Docker.

---

## 🛠️ Tâches

1. Installer les outils de base sous Ubuntu (Python, Git, Docker, Docker Compose)
2. Initialiser un dépôt Git local, connecter à GitHub
3. Créer la structure de projet Django dans un conteneur Docker
4. Lancer le projet en local via Docker Compose
5. Configurer le `.gitignore` et les fichiers de config
6. Commencer un premier commit propre

---

## 🧪 Test – TDD

```bash
# Test manuel initial : vérifier que l’application Django est accessible en local
curl http://localhost:8000
```
# Résultat attendu :
# HTML de la page d'accueil par défaut Django (avec le rocket bleu)

💻 Code & Configuration
1. 📦 Installation des outils sous Ubuntu
```bash
sudo apt update && sudo apt install -y python3-pip python3-venv git docker.io docker-compose
```
2. 🧱 Création du dossier de projet
```bash
mkdir mon_association
cd mon_association
git init
```
3. 🐳 Dockerfile
```dockerfile
# Dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .  
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```
4. 🧾 requirements.txt
```
Django>=5.0
psycopg2-binary
```
5. 🔧 docker-compose.yml
```yaml
version: '3.9'

services:
  db:
    image: postgres
    environment:
      POSTGRES_DB: association
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - postgres_data:/var/lib/postgresql/data

  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/app
    ports:
      - "8000:8000"
    depends_on:
      - db

volumes:
  postgres_data:
```
6. 🔃 Initialisation Django
```bash
docker-compose run web django-admin startproject config .
```

🧼 Fichier .gitignore
```bash
__pycache__/
*.pyc
*.sqlite3
.env
.venv
*.log
/static/
media/
```

🧪 Docstring Python
Ajoute systématiquement dans tes fichiers Python :

```python
"""
Fichier principal de configuration Django pour le projet associatif.

Contient la configuration par défaut générée par `startproject`.
"""
```

✅ Message de commit associé
```bash
git commit -m"🔧 Initialisation du projet Django avec Docker et PostgreSQL"
````
![Diagramme UML des cas d’usage](/images/dev_env_django_docker.png)

🚀 Étape suivante
Maintenant que notre environnement est prêt, nous allons organiser notre travail avec GitHub Projects et rédiger nos premières User Stories. On passe en mode agile !