# Django Project Setup Tutorial

## Steps to Set Up and Run a Django Project

1. **Install Django**
   ```bash
   pip install django
   ```

2. **Create a Django Project**
   ```bash
   python -m django startproject mynewproject
   ```

3. **Navigate to the Project Directory**
   ```bash
   cd mynewproject
   ```

4. **Apply Database Migrations**
   ```bash
   python manage.py migrate
   ```

5. **Create a Superuser (Admin)**
   ```bash
   python manage.py createsuperuser
   ```

6. **Run the Development Server**
   ```bash
   python manage.py runserver
   ```

7. **Create a Django App**
   ```bash
   python manage.py startapp myapp
   ```

8. **Register the App**
   - Add `'myapp'` to `INSTALLED_APPS` in `mynewproject/settings.py`.

9. **Create a View**
   - Add a view in `myapp/views.py`:
     ```python
     from django.http import HttpResponse

     def home(request):
         return HttpResponse("Hello, world!")
     ```

10. **Configure URLs**
    - Create `myapp/urls.py`:
      ```python
      from django.urls import path
      from . import views

      urlpatterns = [
          path('', views.home, name='home'),
      ]
      ```
    - Include app URLs in `mynewproject/urls.py`:
      ```python
      from django.urls import include, path

      urlpatterns = [
          path('', include('myapp.urls')),
      ]
      ```

11. **Test Your App**
    - Visit `http://127.0.0.1:8000/` in your browser.

12. **Optional: Create Models**
    - Define models in `myapp/models.py`.
    - Create and apply migrations:
      ```bash
      python manage.py makemigrations
      python manage.py migrate
      ```

13. **Optional: Use Templates**
    - Create a `templates` folder in `myapp`.
    - Render templates in views:
      ```python
      from django.shortcuts import render

      def home(request):
          return render(request, 'home.html')
      ```

14. **Optional: Add Static Files**
    - Create a `static` folder in `myapp`.
    - Link static files in templates:
      ```html
      {% load static %}
      <link rel="stylesheet" href="{% static 'styles.css' %}">
      ```
 