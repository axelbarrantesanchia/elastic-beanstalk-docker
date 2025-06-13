# Proyecto Docker - Introducción a Contenedores y Dockerfile

## Paso 1: Instalar Docker

💡 **¿Por qué instalamos Docker primero?**  
Docker es el elemento central en nuestro diagrama. Aunque técnicamente podríamos empezar a trabajar en el código fuente, será mucho más fácil entenderlo si instalamos y usamos Docker primero.  

### Instalando Docker Desktop  
1. Ve a la página oficial de Docker.  
2. Descarga Docker Desktop y selecciona la versión que coincida con el sistema operativo de tu computadora.  

💡 **¿Cómo sé qué versión debo descargar?**  
- **Mac:** Haz clic en el icono de Apple > Acerca de esta Mac, y revisa si el chip dice Apple o Intel.  
- **Windows:** Busca Información del Sistema y revisa si es x64-based o ARM-based.  
- **Linux:** Abre la terminal y ejecuta `uname -m`, revisa si es x86_64 o aarch64/arm64.  

Descargar Docker Desktop puede tomar varios minutos. Mientras esperas...  

💡 **¿Qué es Docker Desktop?**  
Es una aplicación que facilita el uso de Docker, que es una herramienta para crear y gestionar contenedores. Los desarrolladores usan Docker Desktop para construir, probar y desplegar apps desde sus computadoras de forma sencilla.  

💡 **¿Qué son los contenedores? ¿Por qué existen?**  
Los contenedores resuelven el problema del “funciona en mi máquina” que sucede cuando un código corre bien en una computadora pero falla en otra. Cada máquina tiene su sistema operativo, versiones de software, recursos, etc.  
Los contenedores:  
- Empaquetan tu app y todo lo que necesita para correr (dependencias) en un solo archivo. Así otros desarrolladores pueden ejecutar ese paquete igual que tú.  
- Permiten ejecutar aplicaciones de otros desarrolladores rápido porque traen todo listo para funcionar.  
Se usan mucho en desarrollo para garantizar que todo el equipo trabaje en el mismo entorno, aunque estén en máquinas distintas. Por eso son tan populares en DevOps, que busca hacer más eficiente el desarrollo y despliegue de software.  

💡 **¿Qué hace Docker?**  
Docker te ayuda a crear, administrar y desplegar contenedores eficientemente. Puedes imaginarlo como una herramienta para crear el “cargamento” y cargarlo en barcos (contenedores).  

💡 **¿Qué puedo hacer en Docker Desktop?**  
Puedes crear, modificar y monitorear contenedores, así como administrar imágenes, datos y extensiones.  

![Paso 1](docker-pasos/paso1.png)  
![Paso 1](docker-pasos/paso1a.png)  
![Paso 1](docker-pasos/paso1b.png)  
![Paso 1](docker-pasos/paso1c.png)  
![Paso 1](docker-pasos/paso1d.png)  

Aquí podemos ver que Docker Desktop abrió su dashboard, ¡EXCELENTE!  
![Paso 1](docker-pasos/dockerinstalado.png)  

### Verificar que Docker se instaló correctamente  
💡 **¿Por qué verificar la instalación? ¿No basta con ver Docker Desktop?**  
Docker es la herramienta para contenedores, mientras que Docker Desktop es la app que facilita usarla. Tener Docker Desktop no garantiza que Docker esté instalado. Mejor verificarlo con el terminal.  

Abre la terminal (Terminal en Mac/Linux o Command Prompt en Windows).  
![Paso 1](docker-pasos/paso1e.png)  

💡 **Partes importantes de Docker Desktop:**  
- Containers: donde gestionas contenedores (iniciar, parar, borrar).  
- Images: templates para crear contenedores (lo veremos en el siguiente paso).  
- Volumes: datos guardados en contenedores, que persisten aunque reinicies.  
- Builds: imágenes personalizadas creadas o cargadas.  
- Docker Scout: analiza imágenes por temas de seguridad.  
- Extensions: integra herramientas adicionales para monitoreo, seguridad, etc.  

![Paso 1](docker-pasos/opcionesendocker.png)  

💡 **¿Qué es el Docker daemon?**  
El Docker daemon es el motor que ejecuta las órdenes de Docker, como crear contenedores. Es un proceso en segundo plano que recibe comandos del cliente Docker (terminal o Docker Desktop) y realiza las tareas pesadas.  

🙋‍♀️ **Si no ves el icono del Docker daemon (🐳) en Mac:**  
Intenta mover los iconos en la barra de menú manteniendo presionada la tecla Command, a veces se oculta por otros iconos o la cámara.  
![Paso 1](docker-pasos/dockerdaemon.png)  


---

## Paso 2: Ejecutar una Imagen de Contenedor Preconstruida  
¡Wooohoo, ahora que hemos instalado Docker, vamos a usarlo para crear un nuevo contenedor a partir de una imagen de contenedor existente!  
NOTA: Aún no estamos construyendo nuestra propia aplicación (eso sucederá en el siguiente paso), así que piensa en este paso como tu campo de entrenamiento para aprender cómo funcionan las imágenes de contenedores antes de crear la tuya propia.

💡 ¿Qué es una imagen de contenedor?  
Una imagen de contenedor es un plano o plantilla para contenedores. Le da a Docker instrucciones sobre qué incluir en un contenedor, como código de aplicación, librerías, dependencias y archivos necesarios.  
Puedes crear múltiples contenedores idénticos a partir de la misma imagen, y todos esos contenedores se comportarán igual sin importar dónde se desplieguen (siempre que haya una plataforma de contenedores, por ejemplo Docker, para ejecutarlos).  
Esto es genial para desarrolladores que trabajan en equipo, porque significa que todos tienen la misma experiencia con una aplicación que están ejecutando en sus computadoras individuales. Hay menos probabilidad de que una aplicación funcione solo para algunos miembros del equipo y no para otros. También es mucho más rápido para los nuevos miembros del equipo ponerse al día ejecutando las aplicaciones que necesitan para que su proyecto funcione.

Vuelve a tu terminal y ejecuta el siguiente comando:  
docker run -d -p 80:80 nginx
![Paso 2](docker-pasos/terminal.png)

💡 ¿Qué hacen estos comandos?  
`docker run` inicia un nuevo contenedor. Estamos usando una imagen de contenedor preexistente llamada nginx y arrancando este contenedor en modo separado (`-d`) para que se ejecute en segundo plano. Luego, `-p 80:80` mapea el puerto 80 de tu máquina host al puerto 80 dentro del contenedor, lo que significa que podrás acceder a la página web que Nginx está ejecutando desde el navegador de tu computadora.

💡 ¿Qué es Nginx?  
Nginx (se pronuncia "engine-x") es un servidor web, lo que significa que es un programa que sirve páginas web a personas en internet. Los ingenieros usan Nginx porque puede manejar mucho tráfico web de forma fluida y eficiente. A veces, escucharás que Nginx se llama 'proxy server', lo que significa que también puede usarse para reenviar solicitudes de internet a otros servidores, ayudando a balancear la carga o manejar más usuarios.

Deberías obtener esta respuesta en tu terminal:  
![Paso 2](docker-pasos/paso2.png)

💡 Extra para expertos: Si te preguntas de dónde viene la imagen de Nginx, puedes encontrar nginx en Docker Hub haciendo clic aquí.  
💡 Extra para expertos: ¿Qué es Docker Hub?  
Docker Hub es un registro de contenedores, lo que significa que es una biblioteca en línea donde las personas pueden compartir y encontrar imágenes Docker.  
Psst... AWS también tiene su propio registro de contenedores, llamado Amazon ECR (Elastic Container Registry).

Abre tu navegador web y navega a http://localhost. Deberías ver la página de bienvenida predeterminada de Nginx.  
![Paso 2](docker-pasos/paso2a.png)

💡 ¡Wow! ¿Cómo es que terminé viendo esta página de bienvenida de Nginx?  
Escribir localhost en tu navegador significa que quieres conectarte al software servidor que está corriendo en tu propia máquina local.  
Como mapeaste el puerto 80 de tu máquina al puerto 80 en el contenedor que está corriendo (esto pasó cuando ejecutaste `-p 80:80 nginx` anteriormente en este paso), el software servidor al que se conecta localhost es el servidor Nginx dentro del contenedor.  
¡Por eso ves la página web predeterminada de Nginx!

💡 ¿Cómo sabe localhost que use el puerto 80?  
Los navegadores web asumen automáticamente que te refieres al puerto 80 cuando no especificas un número de puerto. Así que cuando escribes localhost en tu navegador, es básicamente lo mismo que escribir localhost:80.

Fíjate cómo pudimos ejecutar un servidor Nginx y abrir una página web en segundos usando contenedores. Hacer esto con una máquina virtual (como EC2) tomaría mucho más tiempo: crear la instancia EC2 significa que necesitaríamos instalar un sistema operativo completo y otro software para crear el servidor web. En general, los contenedores permiten cargar y desplegar aplicaciones más rápido que usando máquinas virtuales.

---

## Paso 3: Crear tu Propia Imagen Personalizada

### 1. Crea una carpeta en tu Escritorio llamada `Compute`

```bash
cd ~/Desktop
mkdir Compute
```

📷  
![Crear carpeta](docker-pasos/paso3.png)

### 2. Crea un archivo llamado `Dockerfile` (sin extensión)

```bash
cd Compute
# En Windows
type nul > Dockerfile.txt
# Luego, cambia el nombre quitando ".txt" o hazlo directamente desde tu editor
```

📷  
![Verificar archivo](docker-pasos/paso3a.png)  
![Carpeta en escritorio](docker-pasos/paso3b.png)

### 3. Agrega el siguiente contenido al Dockerfile

Abre `Dockerfile` con tu editor favorito (como VSCode o Notepad++) y copia lo siguiente:

```Dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/
EXPOSE 80
```

📷  
![Contenido Dockerfile](docker-pasos/paso3c.png)

💡 **Explicación del Dockerfile:**

- `FROM nginx:latest`: Usamos la imagen base de Nginx.
- `COPY index.html /usr/share/nginx/html/`: Reemplazamos la página por defecto con una personalizada.
- `EXPOSE 80`: Indicamos que nuestra app usará el puerto 80.

Guarda el archivo con `Ctrl + S` o `Cmd + S`.

---

### Crear la página web para tu contenedor

Ahora que tenemos listo tu Dockerfile, ¿qué página web debería servir tu contenedor Nginx? Vamos a crear un archivo HTML simple para este proyecto.

Ejecuta estos comandos en tu terminal para crear un nuevo archivo llamado `index.html`. Este archivo debe estar en el mismo directorio que tu Dockerfile.

```bash
type nul > index.html
```
(Asegúrate de estar en el escritorio dentro de la carpeta `Compute`)

📷  
![Paso 3](docker-pasos/paso3d.png)

💡 **¿Qué es un archivo HTML?**  
El archivo HTML determina cómo se verá tu página web. Es un documento que define la estructura, texto, imágenes y enlaces de tu página. Cuando Nginx abre tu archivo HTML, leerá el código y lo mostrará en el navegador del usuario.

Abre tu archivo `index.html` (recomiendo usar VSCode) y agrega este contenido de ejemplo:

> Nota: si al hacer doble clic se abre automáticamente en el navegador, asegúrate de hacer clic derecho sobre `index.html` y abrirlo con un editor de texto.

```html
<!doctype html>
<html>
  <head>
    <title>My Web App</title>
  </head>
  <body>
    <h1>Hello from YOURNAME's custom Docker image!</h1>
  </body>
</html>
```

📷  
![Paso 3](docker-pasos/paso3e.png)

💡 **¿Qué hace este `index.html`?**  
Este archivo mostrará a los visitantes un encabezado que dice:  
*"Hello from YOURNAME's custom Docker image!"*  
Lo verás funcionando pronto 👀

Revisa que tu `index.html` no tenga errores. En la carpeta `Compute`, haz clic derecho sobre `index.html` y selecciona *Abrir con* → tu navegador (ej. Google Chrome) para comprobar que se muestra correctamente.

---

### Construir la Imagen

Ahora, ¡vamos a construir la imagen!

Vuelve a la terminal local, asegúrate de estar dentro de la carpeta `Compute` y ejecuta:

```bash
docker build -t my-web-app .
```

📷  
![Paso 3](docker-pasos/paso3f.png)

En caso de error, usa este comando para renombrar el archivo Dockerfile si se creó con extensión `.txt`:

```bash
rename Dockerfile.txt Dockerfile
```

💡 **¿Qué significa construir una imagen?**  
Construir una imagen significa crear una imagen Docker usando las instrucciones dentro del Dockerfile. Docker usará esta imagen construida como plantilla para crear contenedores que ejecuten tu aplicación en cualquier lugar.

💡 **¿Qué hacen estos comandos?**  
- `-t my-web-app` le pone el nombre `my-web-app` a tu imagen.  
- El punto `.` le dice a Docker que busque el Dockerfile en el directorio actual, es decir, la carpeta `Compute`.

💡 **¿Qué significa la respuesta del terminal?**  
La respuesta en la terminal muestra los pasos que Docker ejecutó para construir tu imagen a partir del Dockerfile:  

- *Loading build definition:* Docker está cargando las instrucciones del Dockerfile para saber cómo construir la imagen.  
- *[1/2] FROM docker.io...:* Docker procesa la primera línea del Dockerfile (la imagen base nginx).  
- *[2/2] COPY index.html...:* Docker procesa la segunda línea, copiando el archivo `index.html` al sistema de archivos del contenedor.  
- *Exporting to image:* Docker combina todas las instrucciones aplicadas y prepara la imagen lista para correr contenedores.

---
```

## Paso 4: Ejecutar un contenedor con tu imagen personalizada

Para ejecutar una imagen, usa este comando:

```bash
docker run -d -p 80:80 my-web-app
```

📷  
![Paso 4](docker-pasos/paso4.png)

💡 **¿Qué hace este comando?**  
Similar al comando que usamos antes, le estamos pidiendo a Docker que ejecute nuestra imagen `my-web-app` como un contenedor en segundo plano (`-d`), haciéndola accesible a través del puerto 80 en tu máquina local (`-p 80:80`).

---

### ¿Tuviste un error?

```
Error response from daemon: driver failed to remove network docker_default: Error
```

💡 **¿Por qué apareció este error?**  
Este error aparece cuando ya hay un contenedor usando el puerto 80, por lo que el nuevo contenedor que intentas crear no puede acceder a ese puerto.

Vamos a descubrir quién está usando el puerto 80 ahora mismo 🔎

---

### Forma 1: Usar Docker Desktop

Puedes encontrar el contenedor que está usando el puerto 80 volviendo a abrir Docker Desktop. El icono del contenedor debería ser verde si está en ejecución.

Ese es el contenedor Nginx que creaste cuando ejecutaste por primera vez:

```bash
docker run -d -p 80:80 nginx
```

¡Ya encontramos al culpable! 🧙‍♂️

📷  
![Paso 4](docker-pasos/paso4a.png)

Puedes detener ese contenedor seleccionando el icono cuadrado de “stop”. El icono del contenedor debería volverse gris.

📷  
![Paso 4](docker-pasos/paso4b.png)

---

### Forma 2: Usar la terminal

Otra forma de encontrar el contenedor que está usando el puerto 80 es ejecutando:

```bash
docker ps --filter "publish=80"
```

Tu terminal te mostrará el ID del contenedor bajo la columna `CONTAINER ID`.

📷  
![Paso 4](docker-pasos/paso4c.png)

Luego, detén el contenedor con:

```bash
docker stop {container_id}
```

Reemplaza `{container_id}` con el ID real del contenedor.

📷  
![Paso 4](docker-pasos/paso4d.png)

---

### Intenta ejecutar la imagen nuevamente:

```bash
docker run -d -p 80:80 my-web-app
```

📷  
![Paso 4](docker-pasos/paso4e.png)

¡Genial! Esta vez no hubo errores.

Abre tu navegador web y navega a [http://localhost](http://localhost) nuevamente. Si hicimos todo correctamente, deberías ver el contenido de nuestro archivo `index.html`.

📷  
![Paso 4](docker-pasos/paso4f.png)


## Paso 5: Inicia sesión en AWS con tu usuario IAM

📷  
![Paso 5](docker-pasos/paso5.png)

## Paso 6: Despliega tu imagen personalizada en Elastic Beanstalk

Dirígete a la Consola de administración de AWS e inicia sesión con tu usuario IAM.  
Busca Elastic Beanstalk y haz clic en el servicio.  
![Paso 6](docker-pasos/paso6.png)

💡 **¿Qué es Elastic Beanstalk?**  
AWS Elastic Beanstalk es un servicio que facilita el despliegue de aplicaciones en la nube sin preocuparte por la infraestructura subyacente. Solo subes tu código y Elastic Beanstalk se encarga de todo lo necesario para ejecutarlo, como configurar servidores y gestionar escalabilidad. Así puedes enfocarte en tu código sin manejar infraestructura directamente.

En términos técnicos, Elastic Beanstalk maneja:  
- Aprovisionamiento de capacidad  
- Balanceo de carga  
- Autoescalado  
- Monitoreo de salud de la aplicación  

💡 **¿Cómo se relaciona Elastic Beanstalk con contenedores y Docker?**  
Elastic Beanstalk puede ejecutar aplicaciones empaquetadas como contenedores Docker. Esto te permite desarrollar localmente, crear una imagen Docker con todo lo necesario para correr tu app y luego desplegarla fácilmente en Elastic Beanstalk.

---

Haz clic en **Create Application** en la página principal de Elastic Beanstalk.  
![Paso 6](docker-pasos/paso6a.png)

💡 **¿Qué es una aplicación en Elastic Beanstalk?**  
Una aplicación es como una carpeta que contiene todas las versiones de un proyecto desplegado y la configuración usada.

---

En la página de configuración:  
- Deja el **Environment tier** por defecto.  

💡 **¿Qué es un entorno (environment) en Elastic Beanstalk?**  
Es la configuración para las máquinas virtuales (EC2) que ejecutarán tu aplicación: tipo de instancia, escalado, redes, etc.

- Pon **Dockerdemoapp** como nombre de aplicación.  
- Deja la sección Environment information con valores por defecto.  
![Paso 6](docker-pasos/paso6b.png)

---

En la sección **Platform**, selecciona **Docker** como plataforma.  
La rama y versión de la plataforma se seleccionan automáticamente.  
![Paso 6](docker-pasos/paso6c.png)

💡 **¿Qué significa plataforma?**  
Es la tecnología que ejecuta tu aplicación. Elegimos Docker porque es la mejor opción para imágenes Docker.

---

En la sección **Application code**, selecciona **Upload your code**.  
![Paso 6](docker-pasos/paso6d.png)

Antes de subir cualquier código, regresa a la carpeta Compute en tu escritorio y abre el archivo index.html con tu editor de texto.  
Encuentra la línea que dice <h1>Hello from YOURNAME's custom Docker image!</h1>  
Actualiza index.html agregando una nueva línea justo debajo de la línea que encontraste. Por ejemplo:

<!doctype html>
<html>
  <head>
    <title>Mi Aplicación Web</title>
  </head>
  <body>
    <h1>Hello from YOURNAME's custom Docker image!</h1>
    <h1>
      Si puedo ver esto, significa que Elastic Beanstalk ha desplegado una imagen con
      mi trabajo.
    </h1>
  </body>
</html>

![Paso 6](docker-pasos/paso6e.png)

Elastic Beanstalk necesita que tu código fuente esté en un archivo ZIP. Crea un archivo ZIP que contenga Dockerfile e index.html.  
Tus archivos deben estar en el nivel raíz del archivo ZIP, no dentro de una subcarpeta.  
Para crear tu archivo ZIP, en la carpeta Compute, selecciona ambos archivos Dockerfile e index.html y comprímelos juntos.

![Paso 6](docker-pasos/paso6f.png)

Regresa a la página de configuración de Elastic Beanstalk, ingresa **Version One** como etiqueta de versión.  
Selecciona **Archivo local (Local file)**.  
En **Upload application**, selecciona **Choose file**.  
Carga el archivo ZIP que creaste anteriormente. Esto sube el código de tu aplicación a Elastic Beanstalk.

![Paso 6](docker-pasos/paso6g.png)  
![Paso 6](docker-pasos/paso6h.png)

En la sección Presets, elige **Single instance (Free tier eligible)**.  

💡 **Extra para expertos: ¿Qué son los Presets?**  
Al seleccionar un preset, eliges una forma predefinida recomendada por AWS para configurar Elastic Beanstalk.  
El preset Single instance crea una única instancia EC2, ideal para pruebas y elegible para el Free Tier.  
Otros presets se adaptan a diferentes escenarios y necesidades. Por ejemplo, alta disponibilidad ofrece herramientas para manejar rápidamente cambios en el volumen de tráfico, ideal para aplicaciones en producción y uso público.  

Selecciona **Next**.

![Paso 6](docker-pasos/paso6i.png)

In the Configure service access page:  
Hay que crear 2 roles para nuestros servicios  
Presiona Create Role  
![Paso 6](docker-pasos/paso6j.png)  
Sigue los pasos de las imagenes siguientes:  
![Paso 6](docker-pasos/paso6k.png)  
Permisos que Beanstalk tendra por defecto al seleccionar Create Role  
AWSElasticBeanstalkEnhancedHealth  
AWSElasticBeanstalkManagedUpdatesCustomerRolePolicy  
Cuando creas un Environment de tipo "Single Instance" en Elastic Beanstalk, y estás seleccionando o creando un EC2 instance profile (rol de instancia EC2), Elastic Beanstalk te sugiere al menos estas dos políticas:  
1. AWSElasticBeanstalkEnhancedHealth  
🔍 Permite a la instancia reportar información detallada de salud a Elastic Beanstalk.  
📈 Es necesaria para el monitoreo de salud mejorado.  
2. AWSElasticBeanstalkManagedUpdatesCustomerRolePolicy  
🔄 Permite a Beanstalk aplicar actualizaciones administradas en tu entorno.  
🛡️ Asegura que EB pueda verificar si es seguro aplicar parches o nuevas versiones.  
dale next  
![Paso 6](docker-pasos/paso6l.png)  
Aqui solo dale Create Role y deja todo por defecto  
![Paso 6](docker-pasos/paso6m.png)  
Primer rol creado, ahora vamos con el otro...  
![Paso 6](docker-pasos/paso6n.png)  
Vuelve a Beanstalk y toca Create Rol para el perfil de la instancia  
![Paso 6](docker-pasos/paso6o.png)  
Sigue las siguientes imagenes...  
![Paso 6](docker-pasos/paso6p.png)

Añadiremos AWSElasticBeanstalkWebTier  
y el rol AmazonEC2ContainerServiceRole  
Permite a la instancia EC2 interactuar con otros servicios como S3, CloudWatch, etc.

Es parte del uso común de aplicaciones web desplegadas en Beanstalk.  
![Paso 6](docker-pasos/paso6q.png)  
![Paso 6](docker-pasos/ecsrole.png)  
Ahora avanza hasta crear el rol con éxito  
![Paso 6](docker-pasos/paso6r.png)  
Ahora ya verás los 2 roles listos, no necesitaremos pares de claves en esta demo  

💡 ¿Qué es un service role?  
Un service role es un rol IAM de AWS que permite a Elastic Beanstalk llamar a otros servicios de AWS en tu nombre.

💡 ¿Por qué Elastic Beanstalk necesita un nuevo service role?  
Uno de los beneficios de Elastic Beanstalk es que puede manejar la infraestructura en la nube de tu aplicación por ti, y solo puede hacerlo si tiene permiso para usar tus recursos AWS automáticamente, por ejemplo, creando una nueva instancia EC2. También ayuda a automatizar tareas como el escalado y el monitoreo de salud.

💡 ¿Qué es un instance profile?  
Un instance profile es otro rol IAM (similar a los service roles), pero está diseñado para dar a las instancias EC2 permiso para acceder a otros servicios AWS que tu aplicación pueda necesitar para funcionar.

💡 Extra para expertos: ¿Qué hace ecsInstanceRole?  
El ecsInstanceRole otorga a las instancias EC2 permiso para gestionar contenedores usando AWS Elastic Container Service (ECS).  
Mientras Docker construye y ejecuta contenedores, piensa en ECS como un administrador que ayuda a Elastic Beanstalk a decidir cuántos contenedores iniciar y detener, basado en la cantidad de tráfico hacia tu aplicación.  
![Paso 6](docker-pasos/paso6s.png)  

En la página de configuración de red, base de datos y etiquetas (Set up networking, database, and tags):  
Ignora la sección Virtual Private Cloud – la VPC por defecto es adecuada para este proyecto.  
En Configuración de instancia (Instance settings), marca Activada (Activated) para la opción Dirección IP pública (Public IP address).  

💡 ¿Qué hace activar una dirección IP pública?  
Esto hace que tus instancias EC2 y tu aplicación sean accesibles desde Internet – ¡emocionante!  

Sáltate el resto de la página, no necesitamos configurar una base de datos para nuestra página web.  
Selecciona Next.  
![Paso 6](docker-pasos/paso6t.png)

Para la página Configure instance traffic and scaling:  
En la sección Instances, para Root volume type selecciona General Purpose 3 (SSD).  
Para Size selecciona 10 GB.  

💡 Extra para expertos: ¿Qué significa root volume type?  
El root volume type es el espacio de almacenamiento de tu instancia EC2, como el disco duro de tu computadora local donde se guarda el sistema operativo y archivos.  
General Purpose 3 (SSD) es elegible para Free Tier y es adecuado para la mayoría de las aplicaciones.  
Otros tipos son para casos especiales, como Provisioned IOPS SSD (io1/io2) para bases de datos de alto rendimiento, o Cold HDD (sc1) para almacenamiento a largo plazo.  

En Instance metadata service (IMDS), asegúrate que IMDSv1 esté Desactivado (mantén la casilla Deactivated marcada).  

💡 Extra para expertos: ¿Qué es Instance metadata service (IMDS)?  
IMDS es un servicio que otorga credenciales temporales a tus aplicaciones en las instancias EC2. Por ejemplo, para permitir acceso a S3 desde tu app.  
![Paso 6](docker-pasos/paso6u.png)  

Como nuestra app no necesitará acceso a otros servicios AWS, no necesitamos IMDS.  
No es necesario configurar nada más. Salta las secciones Security groups y Capacity.  

💡 Extra para expertos: ¿Qué hacen estas configuraciones?  
Los security groups controlan el tráfico, mientras que Capacity controla la capacidad de cómputo del entorno y la configuración de autoescalado para optimizar el número de instancias usadas.  

Selecciona Next.  

![Paso 6](docker-pasos/paso6v.png)  

En la página Configure updates, monitoring, and logging:  
En la sección Monitoring, selecciona Basic para tu System.  
🚨 Asegúrate de seleccionar Basic para mantener el proyecto gratis. 🚨  

💡 Extra para expertos: ¿Qué son monitoring y health reporting?  
Son herramientas que te dan actualizaciones de rendimiento y estado de tu aplicación Elastic Beanstalk para detectar problemas antes que afecten a los usuarios.  
![Paso 6](docker-pasos/paso6w.png)  

Desplázate a la sección Managed platform updates.  
Asegúrate de desmarcar la casilla Activated para la opción Managed updates.  

💡 Extra para expertos: ¿Qué hacen los managed updates?  
Actualizan automáticamente el software que corre tu aplicación en Elastic Beanstalk, por ejemplo Docker, para mantenerla segura y estable sin actualizaciones manuales.  
![Paso 6](docker-pasos/paso6x.png)  

Ahora en Rolling updates and deployments, acepta la política predeterminada All at once deployment.  

💡 Extra para expertos: ¿Qué son los application deployments?  
Son los procesos para mover una nueva versión de software a producción en Elastic Beanstalk: subir código, configurar opciones, y reemplazar la versión antigua por la nueva que ven los usuarios.  
Hay dos tipos principales de deployment policies:  
- All at once: actualiza todas las instancias al mismo tiempo, generando un breve downtime.  
- Rolling updates: actualiza instancias gradualmente, minimizando downtime.  
![Paso 6](docker-pasos/paso6y.png)  

Deja todas las demás opciones, incluyendo Platform software, con sus valores por defecto.  

💡 Extra para expertos: ¿Qué es platform software?  
Es el software que corre en las instancias de Elastic Beanstalk. Por ejemplo, Elastic Beanstalk configura Nginx como servidor proxy por defecto para manejar el tráfico entrante y pasarlo a las instancias EC2 que corren tu app, y luego enviar las respuestas al usuario.  

Selecciona Next.  
![Paso 6](docker-pasos/paso6z.png)  

Para el paso final, solo queda revisar la configuración de Elastic Beanstalk. Aquí se resumen tus elecciones en las últimas cinco páginas.  

Hagamos un checklist rápido:  
- ¿Application name es NextWork App?  
- ¿Application code es un archivo zip?  
- ¿EC2 instance profile está en ecsInstanceRole?  
- ¿Public IP address está en true?  
- ¿Root volume type es gp3?  
- ¿Environment type es Single instance?  
- ¿System está en basic?  
- ¿Managed updates está desactivado?  
- ¿Deployment policy es AllAtOnce?  

Haz clic en Submit. Esto inicia el proceso de creación del entorno y despliegue de la aplicación. Este proceso puede tardar varios minutos...  

![Paso 6](docker-pasos/pasofinalconexito.png)  
![Paso 6](docker-pasos/desplieguefinal.png)  
