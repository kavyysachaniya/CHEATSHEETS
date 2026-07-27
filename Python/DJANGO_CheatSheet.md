# CHEATSHEET FOR DJANGO

> **Universal Django Template**
> Covers:
> - Project Setup
> - CRUD
> - ModelForm
> - Authentication (Login / Signup / Logout)
> - Django REST Framework
> - Serializer
> - ViewSet
> - Permission
> - Router

---

# 1. CREATE DJANGO PROJECT

```bash
pip install django

django-admin startproject project_name

cd project_name

python manage.py startapp app_name
```

---

# 2. PROJECT SETTINGS

## Register App (Necessary)

```python
INSTALLED_APPS = [
    ...
    'app_name',
]
```

---

## Templates Folder (Optional)

```python
TEMPLATES = [
    {
        ...
        'DIRS': [BASE_DIR / 'templates'],
    },
]
```

---

# 3. CREATE MODEL

```python
from django.db import models

class Student(models.Model):

    name = models.CharField(max_length=100)
    roll = models.IntegerField()
    city = models.CharField(max_length=100)

    def __str__(self):
        return self.name
```

---

# 4. REGISTER MODEL (admin.py)

```python
from .models import Student

admin.site.register(Student)
```

---

# 5. DATABASE MIGRATIONS

```bash
python manage.py makemigrations

python manage.py migrate
```

---

# 6. CREATE MODELFORM

```python
from django import forms
from .models import Student

class StudentForm(forms.ModelForm):

    class Meta:

        model = Student

        fields = [
            'name',
            'roll',
            'city'
        ]
```

---

# 7. CRUD (Function Based Views)

## Imports

```python
from django.shortcuts import render, redirect, get_object_or_404
```

---

## Read

```python
objects = Student.objects.all()
```

---

## Create

```python
form = StudentForm(request.POST)

if form.is_valid():

    form.save()
```

---

## Update

```python
form = StudentForm(
    request.POST,
    instance=student
)
```

---

## Delete

```python
student.delete()
```

---

# 8. URL CONFIGURATION

## Project urls.py

```python
path('', include('students.urls'))
```

---

## App urls.py

```python
path('', views.student_list),
path('create/', views.student_create),
path('update/<int:pk>/', views.student_update),
path('delete/<int:pk>/', views.student_delete),
```

---

# 9. TEMPLATES

## student_list.html

```html
Display all students
```

---

## student_form.html

```html
{{ form.as_p }}
```

---

## student_confirm_delete.html

```html
Delete Confirmation
```

---

# 10. LOGIN / SIGNUP / LOGOUT

## Imports

```python
from django.contrib.auth import authenticate, login, logout
from django.contrib.auth.models import User
from django.contrib.auth.forms import UserCreationForm
```

---

## Signup

```python
User.objects.create_user(...)
```

OR

```python
form = UserCreationForm(request.POST)

form.save()
```

---

## Login

```python
user = authenticate(...)

login(request, user)
```

---

## Logout

```python
logout(request)
```

---

# 11. SERIALIZER

```python
from rest_framework import serializers

class StudentSerializer(serializers.ModelSerializer):

    class Meta:

        model = Student

        fields = "__all__"
```

---

# 12. VIEWSET

```python
from rest_framework import viewsets

class StudentViewSet(viewsets.ModelViewSet):

    queryset = Student.objects.all()

    serializer_class = StudentSerializer

    permission_classes = [
        IsAuthenticated,
        IsAdminOrReadOnly
    ]
```

---

# 13. PERMISSIONS

```python
from rest_framework.permissions import BasePermission

class IsAdminOrReadOnly(BasePermission):

    def has_permission(self, request, view):

        if request.method in SAFE_METHODS:
            return True

        return request.user.is_staff
```

---

# 14. ROUTER

```python
from rest_framework.routers import DefaultRouter

router = DefaultRouter()

router.register(
    'students',
    StudentViewSet,
    basename='students'
)

urlpatterns = [
    path('api/', include(router.urls))
]
```

---

# 15. RUN SERVER

```bash
python manage.py runserver
```

---

# QUICK COMMANDS

| Task | Command |
|------|---------|
| Create Project | `django-admin startproject` |
| Create App | `python manage.py startapp` |
| Migrations | `python manage.py makemigrations` |
| Apply Migrations | `python manage.py migrate` |
| Run Server | `python manage.py runserver` |

---

# COMMON FILES

| File | Purpose |
|------|---------|
| models.py | Database Models |
| views.py | Business Logic |
| forms.py | Model Forms |
| serializers.py | API Serializer |
| permissions.py | Custom Permissions |
| urls.py | URL Routing |
| admin.py | Register Models |
| templates/ | HTML Pages |

---

# COMMON METHODS

### Model
- `objects.all()`
- `objects.create()`
- `save()`
- `delete()`

### Forms
- `is_valid()`
- `save()`

### Authentication
- `authenticate()`
- `login()`
- `logout()`

### REST Framework
- `ModelSerializer`
- `ModelViewSet`
- `DefaultRouter`
- `BasePermission`
