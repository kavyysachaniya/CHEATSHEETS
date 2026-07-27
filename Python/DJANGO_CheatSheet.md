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
        fields = ['name','roll','city']
```

---
# 7. CRUD (Function Based Views)

## Imports

```python
from django.shortcuts import render, redirect, get_object_or_404
from .models import Student
from .forms import StudentForm
```

---

## Read (Display All Records)

```python
def student_list(request):
    students = Student.objects.all()
    return render(request,'students/student_list.html',{'students': students})
```

---

## Create (Insert Record)

```python
def student_create(request):
    if request.method == 'POST':
        form = StudentForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('student_list')
    else:
        form = StudentForm()
    return render(request,'students/student_form.html',{'form': form})
```

---

## Update (Modify Record)

```python
def student_update(request, pk):
    student = get_object_or_404(Student, pk=pk)
    if request.method == 'POST':
        form = StudentForm(request.POST, instance=student)
        if form.is_valid():
            form.save()
            return redirect('student_list')
    else:
        form = StudentForm(instance=student)
    return render(request,'students/student_form.html',{'form': form})
```

---

## Delete (Remove Record)

```python
def student_delete(request, pk):
    student = get_object_or_404(Student, pk=pk)
    if request.method == 'POST':
        student.delete()
        return redirect('student_list')
    return render(request,'students/student_confirm_delete.html',{'student': student})
```
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
# 9. HTML TEMPLATES

## List Template (list.html)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <h1>Heading</h1>
    <a href="{% url 'create_name' %}">Add New</a>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Field 1</th>
            <th>Field 2</th>
            <th>Field 3</th>
            <th>Actions</th>
        </tr>
        {% for object in objects %}
        <tr>
            <td>{{ object.id }}</td>
            <td>{{ object.field1 }}</td>
            <td>{{ object.field2 }}</td>
            <td>{{ object.field3 }}</td>
            <td>
                <a href="{% url 'update_name' object.id %}">Edit</a> |
                <a href="{% url 'delete_name' object.id %}">Delete</a>
            </td>
        </tr>
        {% endfor %}
    </table>
</body>
</html>
```

---

## Form Template (form.html)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <h1>Form</h1>
    <form method="POST">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit">Save</button>
    </form>
    <a href="{% url 'list_name' %}">Back to List</a>
</body>
</html>
```

---

## Delete Template (confirm_delete.html)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Delete</title>
</head>
<body>
    <h1>Are you sure you want to delete "{{ object.field1 }}"?</h1>
    <form method="POST">
        {% csrf_token %}
        <button type="submit">Yes, Delete</button>
    </form>
    <a href="{% url 'list_name' %}">Cancel</a>
</body>
</html>
```
---

# 10. LOGIN / SIGNUP / LOGOUT

## Imports

```python
from django.shortcuts import render, redirect
from django.contrib.auth.models import User
from django.contrib.auth import authenticate, login, logout
```

---

## Home

```python
def home(request):
    return render(request,'home.html')
```

---

## Signup

```python
def signup(request):
    if request.method == 'POST':
        username = request.POST['username']
        email = request.POST['email']
        password = request.POST['password']
        User.objects.create_user(
            username=username,
            email=email,
            password=password
        )
        return redirect('login')
    return render(request,'signup.html')
```

---

## Login

```python
def login_view(request):
    if request.method == 'POST':
        username = request.POST['username']
        password = request.POST['password']
        user = authenticate(
            username=username,
            password=password
        )
        if user:
            login(request,user)
            return redirect('home')
    return render(request,'login.html')
```

---

## Logout

```python
def logout_view(request):
    logout(request)
    return redirect('login')
```
---

## signup.html

```html
<form method="POST">
    {% csrf_token %}
    <input type="text" name="username">
    <input type="email" name="email">
    <input type="password" name="password">
    <button>Signup</button>
</form>
```

---

## login.html

```html
<form method="POST">
    {% csrf_token %}
    <input type="text" name="username">
    <input type="password" name="password">
    <button>Login</button>
</form>
```

---

## home.html

```html
{% if user.is_authenticated %}
Welcome {{ user.username }}
<a href="/logout/">Logout</a>
{% else %}
<a href="/login/">Login</a>
{% endif %}
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
router.register('students', StudentViewSet, basename='students')

urlpatterns = [path('api/', include(router.urls))]
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
