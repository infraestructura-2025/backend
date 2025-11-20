# backend
Servicio backend para gestión de usuarios con Django

1. Título y Descripción
El proyecto es un backend Django llamado user_registration que proporciona una API REST para gestión de usuarios. settings.py:9

2. Características Principales
API REST para crear y listar usuarios
Integración con servicio de notificaciones externo (notification-service:5000)
Sistema de notificaciones por email (actualmente en modo simulación)
Configuración CORS para frontend
Base de datos PostgreSQL views.py:41-67 email_service.py:5-21

3. Requisitos Previos

- Python 3.10+  
- PostgreSQL 12+  
- pip (gestor de paquetes)  
settings.py:80-89

4. Dependencias
Las dependencias principales incluyen:
Django 5.2.7
django-cors-headers 4.9.0
psycopg2-binary 2.9.9
requests 2.32.5

5. Instalación

# Clonar repositorio  
git clone https://github.com/infraestructura-2025/backend.git  
cd backend  
  
# Crear entorno virtual  
python3 -m venv venv  
source venv/bin/activate  # En Windows: venv\Scripts\activate  
  
# Instalar dependencias  
pip install -r requirements.txt  
  
# Configurar base de datos PostgreSQL  
# (Ver sección de configuración)  
  
# Ejecutar migraciones  
python manage.py migrate  
  
# Iniciar servidor  
python manage.py runserver
manage.py:7-18

6. Configuración
La aplicación usa variables de entorno con valores por defecto:
DB_NAME: user_registration
DB_USER: admin
DB_PASSWORD: MyPassword123!
DB_HOST: postgres
DB_PORT: 5432
ALLOWED_HOSTS: localhost,127.0.0.1 settings.py:80-89

7. Endpoints API

POST /api/users/     - Crear nuevo usuario  
GET  /api/users/list/ - Listar todos los usuarios  
GET  /admin/         - Panel de administración Django  

urls.py:4-7

8. Integraciones Externas
Servicio de Notificaciones: Envía notificaciones POST a http://notification-service:5000/notify cuando se crea un usuario
Email: Sistema de notificaciones por email (actualmente en modo simulación para desarrollo) views.py:51-58 email_service.py:12-21

9. CORS
Orígenes permitidos configurados para desarrollo y producción:
http://localhost:3000
http://127.0.0.1:3000
http://localhost:8001
http://127.0.0.1:8001
AWS ELB (producción) settings.py:134-140
