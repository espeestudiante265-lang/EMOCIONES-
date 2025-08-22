<h1 align="center"> # EmocionesDSS :performing_arts: </h1>

Sistema de detección de emociones en tiempo real usando Django (API), Next.js (Frontend) y un modelo MLP preentrenado.

:construction: Proyecto en construcción :construction:



## :clipboard: Requisitos previos

- Python 3.12.x **---- IMPORTANTE**
- Git
- Bun (para frontend)

- **OJO: Se debe clonar el repositorio en el disco C para que la ruta sea corta y no hayan problemas posteriormente.**


## Clonar el repositorio
```
https://github.com/ssaloudd/EmocionesDSS.git
```

### :rocket: **Backend (Django)**

###     1. Crear y ejecutar un entorno virtual
```
cd EmocionesDSS/emotion-backend
python -m venv venv
venv\Scripts\activate
```

###     2. Instalar dependencias
Con el entorno virtual activo se ejecuta:
```
pip install -r requirements.txt
```

###     3. Aplicar migraciones
```
cd EmocionesDSS/emotion-backend
venv\Scripts\activate

cd EmocionesDSS/emotion-backend/emotion_api
python manage.py makemigrations api
python manage.py migrate
```

###     4. Crear super-usuario
Aún dentro del directorio `EmocionesDSS/emotion-backend/emotion_api` se puede crear el usuario administrador:
```
python manage.py createsuperuser
```
Llenar con los datos pedidos en consola (para desarrollo solo poner como `Username: admin`, `Email address: admin@admin.com` y `Password: admin`).
Posteriormente, se procede a ejecutar:
```
cd EmocionesDSS\emotion-backend\emotion_api
python manage.py shell
from api.models import Usuario
admin_user = Usuario.objects.get(username='admin') 
admin_user.rol = 'admin'
admin_user.save()

print(f"Usuario {admin_user.username} actualizado. Nuevo rol: {admin_user.rol}")
exit()
```

###     5. Entorno local
En la carpeta `emotion-frontend` se debe crear un archivo `.env.local` en la cual debe hallarse la siguiente información:
```
NEXT_PUBLIC_API_BASE_URL=http://127.0.0.1:8000
```

###     6. Ejecutar servidor
Con el entorno virtual activo y en la ruta `EmocionesDSS/emotion-backend/emotion_api`:
```
python manage.py runserver
```


### :sunrise: **Frontend (Next.js + Bun)**
Al mismo tiempo, en una nueva terminal (sin ningún entorno virtual):
```
cd EmocionesDSS/emotion-frontend
bun install
bun dev
```


### :star2: **Ejecución**
- Para acceder al panel de administrador, se ingresa en el navegador a http://localhost:3000/login con las credenciales que se asignaron a `admin`


- Para probar el modelo de detección de emociones: http://localhost:3000/detection
