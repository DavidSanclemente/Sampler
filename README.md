# Sampler

## Descripción
Este proyecto es una réplica de la plataforma de streaming de música **SoundCloud**. Permite a los usuarios registrarse, subir pistas de audio, escuchar música, comentar en pistas, dar likes, seguir a otros usuarios, crear playlists, y gestionar su perfil.

## Tabla de Contenidos
- [Requisitos de Información](#requisitos-de-información)
- [Reglas de Negocio](#reglas-de-negocio)
- [Requisitos Funcionales](#requisitos-funcionales)
- [Requisitos No Funcionales](#requisitos-no-funcionales)
- [Casos de Uso](#casos-de-uso)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Instalación](#instalación)
- [Contribución](#contribución)
- [Licencia](#licencia)

## Requisitos de Información
### Información de Usuarios:
- **Nombre de usuario**
- **Correo electrónico**
- **Contraseña cifrada**
- **Fecha de registro**
- **Foto de perfil**
- **Biografía o descripción**

### Información de Pistas:
- **Título**
- **Archivo de audio** (MP3, WAV, etc.)
- **Portada o imagen**
- **Género**
- **Descripción**
- **Fecha de subida**
- **Número de reproducciones**
- **Número de likes**
- **Número de comentarios**

### Información de Comentarios:
- **Usuario que comenta**
- **Pista comentada**
- **Texto del comentario**
- **Timestamp** (en el tiempo de reproducción)
- **Fecha y hora**

### Información de Seguidores:
- **Usuario seguido**
- **Usuario que sigue**
- **Fecha de seguimiento**

### Información de Playlists:
- **Nombre de la playlist**
- **Usuario propietario**
- **Lista de pistas**
- **Imagen de portada** (opcional)
- **Fecha de creación**

## Reglas de Negocio
- Un usuario solo puede subir archivos de audio con un peso máximo de **100MB** (cuenta gratuita).
- Solo los usuarios registrados pueden dar **like** o **comentar** pistas.
- Un usuario no puede comentar más de una vez en el mismo segundo de una canción.
- Un usuario solo puede seguir a otro una vez.
- No se permite subir pistas duplicadas (título + archivo idéntico).
- Las **playlists** deben contener al menos una pista.
- No se puede editar ni eliminar una pista que haya sido escuchada más de **100 veces**.
- La duración máxima de una pista es de **10 minutos** para cuentas gratuitas.

## Requisitos Funcionales
- Registro y autenticación de usuarios (registro, login, logout).
- Subida de pistas de audio con formulario (título, archivo, portada, descripción, género).
- Visualización de un feed de pistas más recientes y populares.
- Reproductor de audio integrado con controles: play, pause, avance, volumen.
- Buscador de pistas, usuarios y playlists con autocompletado.
- Comentarios sincronizados con el tiempo de reproducción.
- Likes en pistas.
- Seguimiento de usuarios (seguir/dejar de seguir).
- Creación, edición y eliminación de playlists.
- Añadir pistas a playlists.
- Perfil público de usuario con sus pistas, seguidores, y a quién sigue.
- Panel de usuario con estadísticas básicas: nº de pistas, reproducciones totales, seguidores, etc.
- Reproducción automática del siguiente tema (auto play).
- Modo oscuro y claro.

## Requisitos No Funcionales
- El sistema debe soportar al menos **500 usuarios simultáneos** sin pérdida de rendimiento.
- Las pistas deben comenzar a reproducirse en menos de **3 segundos** desde que se hace clic en "play".
- El sistema debe ser accesible desde navegadores web modernos (Chrome, Firefox, Edge, Safari).
- La aplicación debe estar disponible en **inglés y español**.
- Todas las contraseñas deben estar cifradas con **bcrypt**.
- La base de datos debe realizar **backups diarios automáticos**.
- El sistema debe ser compatible con dispositivos móviles (**responsive design**).
- Se debe utilizar **HTTPS** para todas las comunicaciones.
- El reproductor no debe reiniciarse si el usuario navega por la app (uso de **SPA** o persistencia de estado).
- El tiempo máximo de inactividad antes de cerrar sesión automáticamente será de **30 minutos**.

## Casos de Uso
### Caso de Uso 1: Subir una pista
**Actor:** Usuario registrado

**Escenario principal:**
1. El usuario hace clic en “Subir pista”.
2. Se muestra un formulario donde selecciona el archivo de audio, portada y completa los datos.
3. El usuario pulsa “Subir”.
4. El sistema valida los datos y guarda la pista en el servidor.
5. Se redirige al usuario a su perfil con la nueva pista visible.

**Excepciones:**
- Si el archivo pesa más de 100MB → mensaje de error.
- Si falta algún dato obligatorio → mensaje de advertencia.

### Caso de Uso 2: Escuchar una pista
**Actor:** Usuario visitante o registrado

**Escenario principal:**
1. El usuario accede al perfil de otro usuario o al feed principal.
2. Hace clic en “Play” en una pista.
3. El reproductor se activa y comienza la reproducción.
4. El número de reproducciones se incrementa.

**Extensiones:**
- El usuario puede comentar en un punto específico de la pista si está logueado.

### Caso de Uso 3: Comentar una pista
**Actor:** Usuario registrado

**Escenario principal:**
1. El usuario escucha una pista.
2. En un punto de reproducción, hace clic en “Agregar comentario”.
3. Escribe el texto y envía el comentario.
4. El comentario se guarda vinculado al segundo exacto de reproducción.

**Excepciones:**
- Si el usuario intenta comentar sin iniciar sesión → redirección a login.

### Caso de Uso 4: Crear una playlist
**Actor:** Usuario registrado

**Escenario principal:**
1. El usuario va a su perfil y pulsa “Crear playlist”.
2. Ingresa nombre y portada.
3. Agrega pistas desde su biblioteca o desde otras públicas.
4. Guarda la playlist.

## Tecnologías Utilizadas
- **Frontend:** HTML, CSS, JavaScript (React.js)
- **Backend:** Node.js, Express
- **Base de Datos:** MongoDB (o MySQL)
- **Autenticación:** JWT, bcrypt
- **Reproductor de Audio:** Web Audio API
- **Estilos:** Bootstrap o Material UI
- **Desarrollo móvil:** Responsive Design, Media Queries
- **Otros:** Docker, Git

## Instalación
1. Clona este repositorio.
   git clone https://github.com/usuario/repo-soundcloud-clone.git

2. Instala las dependencias del frontend:
cd frontend
npm install

3. Instala las dependencias del backend:
cd backend
npm install

4. Configura las variables de entorno (por ejemplo, en .env).

5. Inicia los servidores:
npm start

## Contribución
¡Las contribuciones son bienvenidas! Si tienes ideas para mejorar el proyecto, puedes abrir un "issue" o enviar un "pull request".

## Licencia
Este proyecto está licenciado bajo la Licencia MIT - consulta el archivo LICENSE para más detalles.

Este `README.md` cubre la estructura básica y la descripción del proyecto, los requisitos, los casos de uso, las tecnologías, y cómo instalar y contribuir. Puedes personalizarlo según sea necesario.



