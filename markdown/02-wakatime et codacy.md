# Chapitre 2 – Suivi du temps et qualité du code avec WakaTime & Codacy

## 🎯 User Story

> En tant que développeur de l'association,  
> je veux mesurer mon temps de développement et améliorer la qualité de mon code,  
> afin de mieux gérer le projet, prioriser les tâches et livrer un code plus propre.

---

## ✅ Tâches

1. Créer un compte WakaTime.
2. Installer le plugin WakaTime dans l’éditeur (VS Code recommandé).
3. Lier le projet à WakaTime avec une clé API.
4. Créer un compte Codacy et connecter le repo GitHub.
5. Configurer Codacy pour analyser les PRs automatiquement.
6. Ajouter les badges de qualité et de temps dans le `README.md`.
7. Intégrer les tableaux de bord dans les démonstrations du projet.

---

## 🧪 Test (TDD)

```python
"""
Ce chapitre ne contient pas de test technique automatisé.
Cependant, on vérifiera que :
- Les métriques WakaTime sont bien visibles
- Les problèmes de qualité sont bien détectés par Codacy
"""

def test_wakatime_integration():
    """
    Vérification manuelle : 
    - Travailler 10 minutes dans VS Code avec le projet ouvert.
    - Aller sur https://wakatime.com pour vérifier que l’activité a été enregistrée.
    """
    assert True

def test_codacy_integration():
    """
    Vérification manuelle :
    - Pousser du code avec une erreur de style (ex: indentation incorrecte)
    - Vérifier que Codacy crée un commentaire ou échoue l’analyse
    """
    assert True

# Installation du plugin WakaTime sous VS Code
# Dans la marketplace, rechercher "WakaTime", cliquer sur "Install"

# Configuration WakaTime
# Lors de la première utilisation, WakaTime vous demandera votre clé API :
# Vous la trouverez dans https://wakatime.com/settings/account

# Ajout dans le README.md

## 🔧 Suivi du projet

![WakaTime](https://wakatime.com/badge/github/<UTILISATEUR>/<REPO>.svg)
![Codacy Badge](https://app.codacy.com/project/badge/Grade/<USER>/<PROJECT>)

# Codacy : se connecter sur https://www.codacy.com/
# Cliquer sur "Add project", sélectionner le dépôt GitHub
# Codacy lance automatiquement une analyse du code existant

Message de commit:
chore: intégration de WakaTime pour le suivi de temps et de Codacy pour la qualité du code
