# Transparencia técnica, privacidad y seguridad — DriveSync PRO v2026.2.2

**Última revisión documental:** 26 de noviembre de 2026  
**Distribución descrita:** Windows x64, ZIP ligero de la release  
**Alcance:** revisión estática de los archivos de código fuente disponibles en `JeanDev09/DRIVESYNC-PRO`, rama `master`, y de la documentación pública de la release.

Este documento describe el comportamiento que se puede verificar en el código fuente revisado. No sustituye una auditoría independiente del ejecutable ni garantiza que cada archivo binario de una release corresponda a un commit concreto mientras no se publique una relación verificable entre ambos.

## 1. Cookies y perfiles de navegador

DriveSync PRO **sí puede utilizar cookies de navegador** durante la extracción de perfiles de TikTok. Por tanto, no sería correcto afirmar que el programa nunca accede a cookies.

En el flujo de extracción de TikTok, el código:

1. Comprueba si existen directorios de perfiles de Chrome, Microsoft Edge, Brave, Vivaldi, Opera o Firefox en las ubicaciones habituales de Windows.
2. En la consulta del catálogo de un perfil, si detecta al menos uno de esos perfiles y la URL no utiliza el formato interno `tiktokuser:`, añade a la ejecución de `yt-dlp` el argumento `--cookies-from-browser` con el primer navegador detectado.
3. En el flujo de descubrimiento autenticado, puede intentar los navegadores detectados uno por uno si el flujo solicita esa modalidad.

La lectura y el manejo de las cookies los realiza `yt-dlp` a petición de DriveSync PRO. Se utilizan para realizar solicitudes autenticadas a TikTok y facilitar la consulta de perfiles que requieren una sesión iniciada.

**Qué significa para el usuario:**

- La detección se basa en la existencia de carpetas de perfiles; no confirma por sí sola que haya una sesión activa.
- En el código revisado, el uso de cookies forma parte del flujo de extracción de perfiles de TikTok; no es una función general de lectura de credenciales para otras tareas.
- Las cookies se usan como credenciales de sesión frente a TikTok. Por su naturaleza, pueden acompañar las solicitudes autenticadas dirigidas a TikTok.
- En los módulos de licencias y cuotas revisados no se encontró código que incorpore cookies, contraseñas del navegador o bases de datos de cookies en los datos enviados a la API de DriveSync PRO.
- El código revisado no muestra un selector de consentimiento por navegador antes de añadir el argumento de cookies al escaneo del catálogo. La presencia de un perfil compatible puede activar ese comportamiento automáticamente en ese flujo.

Si el usuario no desea que se utilice su sesión del navegador, debe evitar ejecutar la extracción de perfiles de TikTok mientras exista ese comportamiento automático. Esta versión no documenta un interruptor de desactivación porque no se verificó uno en el código examinado.

## 2. Conexiones externas

DriveSync PRO realiza conexiones a servicios externos para las funciones que dependen de licencias, cuotas, extracción de TikTok y preparación de dependencias.

| Servicio / destino | Finalidad identificada en el código |
|---|---|
| `drivesync-api.streamifyplus.dev` | Validación de licencias DriveSync PRO y TikTok, consulta de suscripciones y sincronización de cuotas. |
| `www.tiktok.com` | Consulta de perfiles, descubrimiento de vídeos y solicitudes de extracción; puede utilizar cookies del navegador en el flujo descrito arriba. |
| `api.github.com` | Consulta de la última release de yt-dlp. |
| `github.com` | Descarga del ejecutable de yt-dlp desde sus releases oficiales y acceso a actualizaciones/repositorios cuando corresponda. |
| `www.python.org` | Descarga del paquete embebible de CPython 3.14.8 durante la preparación inicial del runtime. |
| `bootstrap.pypa.io` | Descarga de `get-pip.py` para instalar pip en el runtime. |
| PyPI | Instalación de los paquetes declarados en `requirements.txt`. |
| `www.gyan.dev` | Descarga del paquete ZIP de FFmpeg para Windows cuando se necesita y no hay una instalación utilizable. |

La tabla recoge los destinos identificados en los módulos revisados; no debe interpretarse como una lista exhaustiva de todo el tráfico que puedan generar Windows, Google Drive para escritorio, bibliotecas de terceros u otros componentes del equipo.

### Google Drive

Las funciones que trabajan con Google Drive requieren Google Drive para escritorio, según los requisitos publicados. El tráfico propio del cliente de Google Drive debe distinguirse de las conexiones de licencias y cuotas de DriveSync PRO. Este documento no atribuye a la API de DriveSync PRO el contenido sincronizado por el cliente de Google.

## 3. Datos enviados al servicio de DriveSync PRO

Los módulos de licenciamiento y cuotas revisados muestran los siguientes datos de aplicación:

### Validación de licencia DriveSync PRO

La solicitud de validación online incluye:

- Clave de licencia, normalizada a mayúsculas y sin espacios exteriores.
- HWID normalizado del equipo.

Las licencias históricas con formato V3 pueden validarse localmente mediante firma ECC, sin esa consulta online para la validación V3.

### Licencias de TikTok

Las operaciones de validación o activación de licencias TikTok incluyen:

- Clave de licencia TikTok.
- HWID normalizado.

La consulta de recuperación de una licencia asociada al equipo puede enviar únicamente el HWID.

### Sincronización de cuotas

La solicitud de sincronización incluye:

- HWID.
- Incremento de bytes contabilizados (`add_bytes`).
- Incremento de operaciones/descargas TikTok (`add_tiktok`).
- Incremento de operaciones FFmpeg (`add_ffmpeg`).

Estos contadores permiten mantener las cuotas gratuitas sincronizadas con el servicio remoto. El código también conserva información de uso en un archivo JSON local.

**Importante:** no sería preciso afirmar que DriveSync PRO no transmite ningún dato operativo. La sincronización de cuotas transmite los contadores anteriores junto con el HWID. En los payloads de esos módulos no se observaron nombres de archivos, rutas locales, vídeos ni el contenido de carpetas.

La ausencia de esos campos en los módulos revisados no constituye una garantía sobre todos los componentes externos o sobre el tráfico de Google Drive/TikTok.

## 4. Runtime y dependencias

La distribución ligera no incorpora el entorno Python completo. Durante la preparación inicial, `install_runtime.ps1`:

1. Descarga CPython embebible **3.14.8** desde python.org.
2. Descarga `get-pip.py` desde bootstrap.pypa.io.
3. Instala pip y los paquetes declarados en `requirements.txt`.
4. Prepara el entorno en `%LOCALAPPDATA%\DriveSyncPro\Python`.

El archivo `requirements.txt` revisado declara:

- `rich>=13.0,<15`
- `pywin32>=300` (solo Windows)
- `cryptography>=42.0`
- `packaging>=23.0`

Los rangos permiten que pip resuelva versiones compatibles disponibles al instalar; por tanto, la resolución de dependencias puede variar entre instalaciones.

### Componentes descargados bajo demanda

- **yt-dlp:** consulta GitHub Releases y descarga el ejecutable oficial cuando hace falta. El código comprueba que el archivo sea un ejecutable Windows y que su versión coincida con la release consultada.
- **FFmpeg para Windows:** descarga el ZIP `ffmpeg-release-essentials.zip` desde `gyan.dev` cuando no encuentra una instalación utilizable.

La preparación del runtime y los descargadores revisados no fijan ni comparan un SHA-256 esperado para el archivo de CPython, `get-pip.py` o el ZIP de FFmpeg. No debe afirmarse que esos archivos tienen verificación criptográfica de hash si no se incorpora y publica esa comprobación.

## 5. Procesamiento local y archivos

El procesamiento multimedia se realiza mediante componentes locales y dependencias ejecutadas en el equipo. En los módulos de validación de licencias y sincronización de cuotas revisados, los datos enviados son los campos descritos en la sección 3; no se observó que esos payloads adjunten archivos personales.

Esto no equivale a afirmar que ningún dato sale nunca del equipo: la extracción de TikTok realiza solicitudes a TikTok y las funciones de Google Drive utilizan el servicio/cliente correspondiente.

## 6. Distribución ligera y alcance de esta revisión

La release pública ofrece un ZIP ligero. El runtime Python y algunas dependencias se preparan o descargan durante el primer uso o cuando una función los necesita. Por ello, un análisis antivirus del ZIP inicial no representa por sí solo un análisis de todos los componentes que pueden descargarse posteriormente.

La revisión documental se realizó sobre los archivos disponibles en la rama `master` del repositorio de código fuente y la documentación pública de la release v2026.2.2. Mientras no se publique un identificador de commit y un manifiesto que vinculen la compilación con el ZIP distribuido, no se debe presentar esta revisión estática como prueba de que el ejecutable publicado es reproducible o idéntico a ese código fuente.

## 7. Resumen para compradores

- DriveSync PRO puede utilizar cookies de Chrome, Edge, Brave, Vivaldi, Opera o Firefox para autenticarse ante TikTok durante la extracción de perfiles.
- Las cookies son manejadas por yt-dlp para solicitudes a TikTok; no se encontró que los módulos de licencias o cuotas las envíen a la API de DriveSync PRO.
- La API de DriveSync PRO recibe datos de licencia (clave y HWID) y datos de cuotas (HWID y contadores de uso).
- El ZIP ligero no contiene todo el runtime; algunos componentes se descargan desde los proveedores indicados cuando son necesarios.
- El procesamiento multimedia se realiza localmente, pero las funciones online se comunican con sus respectivos servicios.
- Esta página documenta el código fuente revisado y no sustituye una auditoría independiente del binario de la release.

## Archivos de referencia revisados

Repositorio de código fuente: [JeanDev09/DRIVESYNC-PRO](https://github.com/JeanDev09/DRIVESYNC-PRO)

- `sync/tiktok.py` — detección de perfiles y uso de `--cookies-from-browser`.
- `licensing/validator.py` — validación online de licencias DriveSync PRO.
- `licensing/tiktok_license.py` — validación y recuperación de licencias TikTok.
- `quota/daily_tracker.py` — sincronización de contadores de cuotas.
- `install_runtime.ps1` — preparación de CPython y pip.
- `requirements.txt` — dependencias Python.
- `utils/ytdlp_installer.py` — descarga y validación de yt-dlp.
- `utils/ffmpeg_installer.py` — descarga de FFmpeg.
