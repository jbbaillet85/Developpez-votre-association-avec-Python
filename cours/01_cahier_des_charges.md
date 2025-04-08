![Illustration - Cahier des charges](/images/cahier_des_charges.png)

---
# Cahier des charges – Projet : Plateforme de gestion associative avec Django

---

## 📌 Contexte du projet

Notre client est une **association loi 1901** qui souhaite moderniser sa gestion interne. Jusqu’ici, tout se faisait à la main ou avec des outils dispersés (tableurs, mails, documents Word...).

L’objectif est de créer une **application web tout-en-un**, ergonomique, sécurisée, et facile à maintenir.

---

## 🎯 Objectifs fonctionnels

L'application devra permettre :

- 🧑‍🤝‍🧑 **La gestion des membres** : inscriptions, cotisations, profils, rôles (membre, bénévole, admin)
- 📅 **L’organisation d’événements** : calendrier, inscriptions, présence
- 📦 **La gestion comptable** : dépenses, recettes, reçus fiscaux, clôture annuelle
- 📝 **La gestion documentaire** : statuts de l’association, rapports PDF
- 🛡️ **La conformité RGPD** : consentement, droits d’accès et suppression
- 🧪 **Le suivi des formations** : parcours, certificats PDF, validation
- 📊 **Les tableaux de bord** : synthèse visuelle pour le bureau
- 🖼️ **La gestion des profils avec photos** (bénévoles et membres)
- 🖨️ **L’édition automatique de documents** : certificats, reçus, convocations

---

## 🛠️ Contraintes techniques

Le développement doit respecter les contraintes suivantes :

### 🔹 Technologies

| Domaine            | Choix                     |
|--------------------|---------------------------|
| Backend            | Python 3.12, Django 5     |
| Base de données    | PostgreSQL                |
| Tests              | `pytest`, TDD obligatoire |
| Authentification   | `django-allauth`          |
| Interface Frontend | Django + Tailwind CSS     |
| Images             | Pillow                    |
| Génération PDF     | ReportLab                 |
| API                | Django REST Framework     |
| Graphiques         | Matplotlib                |
| Traitement données | Pandas, NumPy             |

### 🔹 Outils et environnement

| Outil / Méthode        | Utilisation prévue                                      |
|------------------------|----------------------------------------------------------|
| **Git & GitHub**       | Versionnement, hébergement, pull requests                |
| **GitHub Flow**        | Stratégie de branchement                                |
| **GitHub Projects**    | Suivi agile des user stories et tâches                   |
| **GitHub Actions**     | Intégration continue, tests automatisés, déploiement     |
| **Docker**             | Conteneurisation (PostgreSQL, Django, Nginx, etc.)       |
| **Ubuntu**             | Système d’exploitation cible pour le déploiement         |
| **Coolify**            | Déploiement sur VPS, via containers Docker               |

---

## 🔐 Sécurité

L'application devra :

- Implémenter un système d’authentification robuste (mot de passe sécurisé, allauth)
- Gérer les rôles et permissions (admin, membre, bénévole)
- Protéger les données personnelles (RGPD)
- Fournir un panneau d’administration sécurisé

---

## 💡 Fonctionnalités prioritaires (MVP)

Voici les fonctionnalités à implémenter dans la première version (Minimum Viable Product) :

1. Création d’un espace membre (connexion, inscription, modification)
2. Interface d’administration
3. Gestion des rôles
4. Tableau de bord avec les adhésions
5. Reçus fiscaux PDF
6. Événements avec calendrier
7. Gestion comptable de base
8. Upload de photos de profil
9. Génération automatique de statuts
10. Déploiement sur VPS avec Coolify

---

## 🧪 Approche pédagogique

Pour chaque fonctionnalité :

- 📌 Une **user story** claire sera présentée
- 🧩 Les **tâches techniques** seront détaillées
- 🧪 Les **tests TDD** seront écrits **avant** le code
- 💻 Le **code fonctionnel** sera commenté avec **docstrings**
- 🗂️ Un **message de commit** clair sera fourni

---

## 🧠 Public visé

Ce projet est conçu pour les :

- Développeurs Python/Django en montée en compétence
- Étudiants suivant une formation Dev / Data
- Responsables associatifs souhaitant se former au numérique

---

## 🖼️ Illustrations UML

Voici un exemple de diagramme de cas d’usage utilisé pour illustrer les fonctionnalités du projet :

![Diagramme UML des cas d’usage](/images/uml_cas_utilisation.png)

---

## 🚀 Prochaine étape

👉 Dans le prochain chapitre, nous allons **mettre en place notre environnement de développement** sous Ubuntu, avec GitHub et Docker. On démarre le projet !

---