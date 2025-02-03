# Bharatfd_internship

https://github.com/DongaHarikaSri/Bharatfd_internship

# Overview
A Django-based REST API for managing Frequently Asked Questions (FAQs) with automatic translation support for Hindi and Bengali languages.

# Features
REST API for FAQ management
Automatic translation using Google Translate
Support for multiple languages (English, Hindi, Bengali)
Rich text editing with CKEditor
Admin interface for content management
Redis caching integration
# Prerequisites
Python 3.x
Django 5.0+
Redis Server
pip
# Installation
Clone the repository:

git clone <repository-url>
cd faq_project
Create and activate a virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
Install dependencies:

pip install django djangorestframework django-ckeditor django-redis googletrans
Apply database migrations:

python manage.py migrate
Create a superuser:

python manage.py createsuperuser
# Usage
Start the development server:

python manage.py runserver
Access the endpoints:

Admin interface: http://localhost:8000/admin/
API endpoints:
List FAQs: GET /api/faqs/
Get FAQ by ID: GET /api/faqs/{id}/
Create FAQ: POST /api/faqs/
Update FAQ: PUT /api/faqs/{id}/
Delete FAQ: DELETE /api/faqs/{id}/
# Language Support
To get FAQs in a specific language, use the lang query parameter: sh GET /api/faqs/?lang=hi  # For Hindi GET /api/faqs/?lang=bn  # For Bengali GET /api/faqs/?lang=en  # For English (default) 

# Testing
Run the test suite: sh python manage.py test 

# Configuration
Key settings in settings.py: ```python INSTALLED_APPS = [ ... 'rest_framework', 'faq', 'ckeditor', 'django_redis', ]

REST_FRAMEWORK = {
    'DEFAULT_PERMISSION_CLASSES': [
        'rest_framework.permissions.IsAuthenticatedOrReadOnly',
    ]
}

CACHES = {
    'default': {
        'BACKEND': 'django_redis.cache.RedisCache',
        'LOCATION': 'redis://127.0.0.1:6379/1',
        'OPTIONS': {
            'CLIENT_CLASS': 'django_redis.client.DefaultClient',
        }
    }
}

# Models
The FAQ model includes:

Question and answer fields
Translated versions for Hindi and Bengali
Automatic translation on save
Methods for retrieving translated content

