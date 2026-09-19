# DriveSync PRO 🚀

> **Sincronización y transferencia masiva de Google Drive para Windows.**

DriveSync PRO es una herramienta premium para gestionar y sincronizar grandes volúmenes de contenido de Google Drive desde una **interfaz TUI moderna, interactiva y orientada al rendimiento**.

Permite seleccionar unidades de Google Drive, explorar estructuras de carpetas, elegir destinos locales o de Google Drive y ejecutar sincronizaciones masivas con un panel de progreso en tiempo real.

Desarrollado por **JeanDev** bajo **Streamify+**.

---

## ✨ Características

### ☁️ Gestión de Google Drive

- Detección automática de las **unidades de Google Drive disponibles**.
- Visualización del espacio libre de cada unidad detectada.
- Selección interactiva de la unidad de origen.
- Navegación por la estructura de directorios.
- Visualización del tamaño de carpetas en **MB / GB**.
- Selección de carpetas mediante teclado.
- Preparación de sincronizaciones masivas.

### 🔄 Sincronización

DriveSync PRO permite sincronizar contenido seleccionado desde Google Drive hacia:

- 💻 **PC / Disco externo**
- ☁️ **Google Drive**

El flujo está diseñado para seleccionar primero la unidad de origen, después el destino y finalmente el contenido que se desea sincronizar.

### ⚡ Transferencias de alto rendimiento

El panel de sincronización muestra información en tiempo real, incluyendo:

- Progreso global.
- Archivos procesados.
- Archivo actualmente transferido.
- Velocidad de transferencia.
- Tiempo transcurrido.
- ETA (tiempo estimado restante).
- Archivos copiados.
- Archivos omitidos.
- Errores.
- Registro de actividad.

### 📂 Explorador de directorios

El explorador integrado permite navegar visualmente por las carpetas antes de iniciar una sincronización.

Muestra:

```text
Estructura de directorios

📁 Carpeta principal
 ├─ 📁 Subcarpeta
 ├─ 📁 Subcarpeta
 └─ 📁 Subcarpeta
```

Cada carpeta puede mostrar su tamaño para facilitar la selección del contenido que se desea transferir.

La primera vez que se calculan determinados tamaños, DriveSync PRO puede utilizar una caché para acelerar posteriores consultas.

---

## 🖥️ Interfaz TUI

DriveSync PRO está diseñado alrededor de una **Terminal User Interface (TUI)**.

La interfaz permite realizar las operaciones utilizando principalmente el teclado, manteniendo la información importante visible en pantalla.

### Navegación

```text
↑ ↓       Navegar
Enter     Confirmar
Esc       Volver
Espacio   Seleccionar
← →       Cambiar entre carpetas / vistas
Ctrl+C    Cancelar de forma segura
```

Las opciones y controles disponibles pueden variar según la pantalla actual.

---

## 🔎 Flujo de trabajo

El proceso de sincronización está organizado en pasos claros:

### 1. Seleccionar la sincronización

Desde el menú principal se inicia una nueva sincronización.

```text
DRIVESYNC PRO · v4.3.1 · LISTO

Inicio

  > Iniciar sincronización
    Salir
```

### 2. Seleccionar la unidad de Google Drive

DriveSync PRO detecta las unidades disponibles y muestra información sobre el espacio libre.

```text
Unidades Google Drive Detectadas

  > [G:] streamifyplus@gmail.com     Google Drive · 127.5 GB Libres
    [H:] otra_cuenta@gmail.com       Google Drive · 3.4 GB Libres
```

### 3. Elegir el destino

Puedes seleccionar dónde se copiará el contenido:

```text
Destino De La Copia

  > PC / Disco externo
    Google Drive
```

### 4. Explorar y seleccionar carpetas

Utiliza el explorador de directorios para navegar por la estructura y seleccionar las carpetas necesarias.

### 5. Ejecutar la sincronización

Una vez confirmado el contenido, DriveSync PRO inicia la operación y muestra el progreso en tiempo real.

---

## 📊 Panel de sincronización

Durante una operación, el programa muestra un resumen global y detalles del archivo actual.

Ejemplo:

```text
SINCRONIZACIÓN GLOBAL                         25.3%

8 / 45 archivos                         126.98 MB / 502.80 MB

ARCHIVO ACTUAL    Video (17).mp4

16.59 MB / 16.59 MB     100.0%

⚡ 116.88 MB/s    ⏱ 00:00:01    ETA 00:00:03
```

También se muestra un resumen de archivos:

```text
ARCHIVOS

TOTAL          45
PROCESADOS      8
COPIADOS        8
OMITIDOS        0
ERRORES         0
```

Y un registro de actividad:

```text
ACTIVIDAD

✓ OK       Nuevo plan de sincronización guardado.
ℹ INFO     Copiado: Video (44).mp4
ℹ INFO     Copiado: Video (19).mp4
ℹ INFO     Copiado: Video (6).mp4
```

> Los valores de velocidad, progreso, ETA y cantidad de archivos dependen de cada operación.

---

## 🛡️ Cancelación segura

Las sincronizaciones pueden cancelarse de forma controlada utilizando:

```text
Ctrl+C
```

El programa está diseñado para gestionar la cancelación de la operación de forma segura.

---

## 🔐 Sistema de licencia y HWID

DriveSync PRO es software premium y utiliza un sistema de activación asociado a un **HWID (Hardware ID)**.

La activación permite vincular una licencia con el dispositivo autorizado.

### Primer inicio

Durante el primer inicio, DriveSync PRO muestra automáticamente el **HWID del dispositivo** cuando corresponde al proceso de activación.

Utiliza ese identificador para solicitar y activar tu licencia.

> **La licencia es personal, no transferible y está vinculada al dispositivo autorizado.**

---

## 💻 Compatibilidad

### Windows x64

La versión oficial está preparada para sistemas:

- Windows x64.
- Equipos con conexión a Internet.
- Acceso a las cuentas de Google Drive que se utilizarán.

### Distribución

DriveSync PRO se distribuye como un **paquete ZIP con sus componentes**, no como un único ejecutable independiente.

Esta distribución permite mantener separados los componentes de la aplicación y está orientada a:

- Un inicio más consistente.
- Una distribución más estable.
- Evitar empaquetar todos los componentes dentro de un único ejecutable.
- Reducir determinados falsos positivos de antivirus que pueden aparecer con ejecutables altamente empaquetados.

> **Extrae completamente el ZIP antes de ejecutar el programa.**

---

## 📥 Descargar DriveSync PRO v4.3.1

### Versión estable

**DriveSync PRO v4.3.1 — Stable Release**

Archivo para Windows x64:

```text
DriveSync-PRO-v4.3.1-Windows-x64.zip
```

La descarga oficial se encuentra en la sección **Releases** de este repositorio.

### Instalación

1. Descarga el ZIP de la versión correspondiente.
2. Extrae todo su contenido en una carpeta.
3. Ejecuta:

```text
DRIVESYNC PRO.exe
```

4. Sigue el proceso de activación si es necesario.
5. Selecciona la unidad de Google Drive.
6. Selecciona el destino.
7. Explora y selecciona las carpetas.
8. Confirma la sincronización.

> **No ejecutes el programa directamente desde el interior del ZIP.**

---

## 📋 Requisitos

Para utilizar DriveSync PRO necesitas:

- Windows x64.
- Drive para escritorio: [Descarga aquí](https://dl.google.com/drive-file-stream/GoogleDriveSetup.exe)
- Conexión a Internet.
- Una cuenta de Google Drive con acceso al contenido que deseas gestionar.
- Una licencia válida para las funciones protegidas.

El rendimiento de las transferencias puede variar según:

- Velocidad y estabilidad de Internet.
- Tamaño y cantidad de archivos.
- Latencia de red.
- Rendimiento del almacenamiento local.
- Condiciones y límites de Google Drive.

---

## ❓ FAQ

### ¿Qué puedo hacer con DriveSync PRO?

Puedes detectar tus unidades de Google Drive, navegar por sus directorios, seleccionar carpetas y sincronizar el contenido hacia un PC, disco externo o una ubicación de Google Drive.

### ¿Puedo seleccionar carpetas completas?

Sí. El explorador permite navegar por la estructura de directorios y seleccionar las carpetas que deseas procesar.

### ¿Puedo ver el tamaño de las carpetas?

Sí. El explorador muestra tamaños de carpetas en MB o GB cuando la información está disponible.

### ¿Puedo ver la velocidad de transferencia?

Sí. Durante la sincronización se muestra la velocidad actual de transferencia junto con el progreso y el ETA.

### ¿Puedo ver cuántos archivos se han copiado?

Sí. El panel de sincronización muestra el total, procesados, copiados, omitidos y errores.

### ¿Necesito una licencia?

Sí. DriveSync PRO es software premium y requiere una licencia válida para las funciones protegidas.

### ¿La licencia funciona en otro equipo?

La licencia está vinculada al **HWID del dispositivo autorizado** y no está diseñada para transferirse libremente entre equipos.

### ¿Por qué se distribuye como ZIP y no como un único EXE?

Porque DriveSync PRO utiliza varios componentes y una distribución por carpeta permite mantenerlos separados. Además, ayuda a evitar algunos falsos positivos que pueden producirse con ejecutables altamente empaquetados.

---

## 📌 Información de la versión

| Información | Detalle |
|---|---|
| Producto | **DriveSync PRO** |
| Versión | **4.3.1** |
| Estado | **Stable** |
| Plataforma | **Windows x64** |
| Distribución | **ZIP** |
| Interfaz | **TUI** |
| Activación | **HWID** |
| Licencia | **Lifetime** |

---

## ⚠️ Aviso importante

DriveSync PRO es **software comercial**.

El uso, distribución, modificación, ingeniería inversa, redistribución no autorizada o intento de eludir el sistema de activación puede estar restringido por los términos de la licencia correspondiente.

Las funciones relacionadas con Google Drive están sujetas a las condiciones, políticas, límites y disponibilidad de los servicios de Google.

---

## 👨‍💻 Desarrollador

**JeanDev**

Desarrollado bajo **Streamify+**.

### Contacto

- **🌐 ForoBeta** — [Perfil de JeanDev](https://forobeta.com/members/jeandev.362650/)
- **💬 WhatsApp** — [Contactar directamente](https://wa.me/51925030997)

---

## ⭐ DriveSync PRO v4.3.1

**Manage. Transfer. Sync.**

Una herramienta enfocada en **sincronización masiva, navegación intuitiva, monitoreo en tiempo real y rendimiento** para trabajar con Google Drive desde Windows.
