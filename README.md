# 🏗️ Torre Interactiva 3D: Experiencia Interactiva Web & TouchDesigner

Una experiencia de juego interactiva en tiempo real donde los usuarios participan desde una interfaz web para construir una torre en 3D, acompañada de un sistema de renderizado dinámico y audio generativo en TouchDesigner.

## 🌐 Arquitectura del Sistema
El proyecto se comunica en tiempo real a través de tres capas:
- **Frontend Web:** Recibe las interacciones del usuario.
- **Puente WebSockets / OSC:** Transmite variables (`nivel`, `velocidad`, `ancho`) al puerto 3333.
- **TouchDesigner:** Procesa los datos para la geometría 3D, la cámara y el audio procedural.

## 🛠️ Requisitos Previos
- Node.js (versión 16 o superior).
- TouchDesigner (versión Non-Commercial o superior).
- Editor de código (Visual Studio Code).

## 🚀 Guía de Reproducción Paso a Paso

### Paso 1: Clonar y configurar el Servidor Web
1. Clona el repositorio:
   ```bash
   git clone <url-de-tu-repositorio>
   cd <nombre-de-carpeta>
   ```
2. Instala las dependencias y arranca el servidor:
   ```bash
   npm install
   node server.js
   ```
3. Entra a `http://localhost:3000` en tu navegador. <br>

### Paso Extra: Conexión en Red Local (Para múltiples usuarios)
Para que la experiencia funcione y otras personas (o tú desde tu celular) puedan interactuar con la torre:
1. **Conexión Wi-Fi compartida:** Tanto tu computadora como los dispositivos del público deben estar conectados a la **misma red Wi-Fi** (si no dispones de una red local estable, puedes crear un punto de acceso/compartir datos móviles desde tu celular y conectar el PC allí).
2. **Obtener tu dirección IP local:** 
   - Abre la terminal (Símbolo del sistema) en tu PC.
   - Escribe el comando:
     ```bash
     ipconfig
     ```
   - Busca la línea que dice **Dirección IPv4** (por ejemplo, `192.168.1.X`). Ese número será tu "localhost" de red.
3. **Conexión de los clientes:** En lugar de entrar a `localhost:3000` en los celulares, los usuarios deberán ingresar la dirección IP IPv4 seguida del puerto, por ejemplo: `http://192.168.1.X:3000`.

### Paso 2: Configurar TouchDesigner
1. Abre tu archivo `.toe`.
2. Verifica que el nodo OSC In esté escuchando en el puerto `3333`.

### Paso 3: Ejecutar la Experiencia
1. Presiona la tecla `R` en TouchDesigner para reiniciar la torre.
2. Juega desde la web para ver la torre crecer, la cámara seguir el movimiento y el audio procedural activarse.

## 🎹 Características Técnicas Destacadas
- **Renderizado en GPU:** Instanciamiento de geometrías optimizado y post-procesamiento con Level TOP.
- **Audio Procedural:** Cadena CHOP con oscilador senoidal, envolvente LFO suave y limitador dinámico integrado para evitar saturación.
- **Cámara Dinámica:** Movimiento adaptativo vinculado a la altura de la torre mediante expresiones de Python.
