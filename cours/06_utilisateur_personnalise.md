# Chapitre 9 — Utilisateur personnalisé avec relations OneToOne

## User Story

> En tant que développeur de l'application associative,  
> je veux créer un modèle utilisateur personnalisé,  
> afin de pouvoir associer facilement un rôle spécifique à chaque utilisateur (admin, membre, bénévole)  
> tout en gardant un système centralisé d'authentification.

---

## Tâches

1. Créer un modèle `CustomUser` basé sur `AbstractUser`.
2. Créer les modèles `AdminProfile`, `MembreProfile` et `BenevoleProfile`.
3. Ajouter des relations OneToOne vers `CustomUser`.
4. Enregistrer le `CustomUser` dans `settings.AUTH_USER_MODEL`.
5. Créer les formulaires et vues associées.
6. Ajouter une administration dédiée dans Django admin.
7. Écrire les tests unitaires pour chaque modèle.

---

## Test (TDD)

```python
# tests/test_models.py

import pytest
from django.contrib.auth import get_user_model
from core.models import AdminProfile, MembreProfile, BenevoleProfile

User = get_user_model()

@pytest.mark.django_db
def test_create_user_with_role_profiles():
    """
    Vérifie que chaque type de profil (Admin, Membre, Bénévole)
    peut être lié à un utilisateur via une relation OneToOne.
    """
    user = User.objects.create_user(username='testuser', password='testpass')

    admin = AdminProfile.objects.create(user=user, fonction='Trésorier')
    assert admin.user.username == 'testuser'

    membre = MembreProfile.objects.create(user=user, cotisation_payee=True)
    assert membre.user.username == 'testuser'

    benevole = BenevoleProfile.objects.create(user=user, zone='Ouest')
    assert benevole.user.username == 'testuser'
```

```python
# core/models.py

from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    """
    Utilisateur personnalisé pour l'association.
    Ce modèle remplace celui de base de Django.
    """
    pass

class AdminProfile(models.Model):
    """
    Profil de l'administrateur
    """
    user = models.OneToOneField(CustomUser, on_delete=models.CASCADE)
    fonction = models.CharField(max_length=100)


class MembreProfile(models.Model):
    """
    Profil des membres adhérents.
    """
    user = models.OneToOneField(CustomUser, on_delete=models.CASCADE)
    cotisation_payee = models.BooleanField(default=False)


class BenevoleProfile(models.Model):
    """
    Profil des bénévoles avec des informations spécifiques.
    """
    user = models.OneToOneField(CustomUser, on_delete=models.CASCADE)
    zone = models.CharField(max_length=50)
```

```python
# core/admin.py

from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import CustomUser, AdminProfile, MembreProfile, BenevoleProfile

admin.site.register(CustomUser, UserAdmin)
admin.site.register(AdminProfile)
admin.site.register(MembreProfile)
admin.site.register(BenevoleProfile)
```

```python
# settings.py
AUTH_USER_MODEL = 'core.CustomUser'
```
## Message de commit
```bash
feat(user): création du modèle utilisateur personnalisé avec profils admin, membre et bénévole liés en OneToOne
```