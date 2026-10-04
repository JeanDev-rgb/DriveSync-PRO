# 🚀 DriveSync PRO

> **Gestión, procesamiento y optimización masiva de contenido en Google Drive y entornos locales.**

<p align="center">
  <a href="https://github.com/JeanDev-rgb/DriveSync-PRO/releases/tag/v2026.1">
    <img src="https://img.shields.io/github/v/release/JeanDev-rgb/DriveSync-PRO?display_name=tag&style=for-the-badge&logo=github&label=Release" alt="Latest Release">
  </a>
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Windows-x64-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Windows x64">
  <img src="https://img.shields.io/badge/FFmpeg-Automatic-007808?style=for-the-badge&logo=ffmpeg&logoColor=white" alt="FFmpeg">
  <img src="https://img.shields.io/badge/Google%20Drive-Supported-4285F4?style=for-the-badge&logo=googledrive&logoColor=white" alt="Google Drive">
</p>

<p align="center">
  <strong>DriveSync PRO v2026.1</strong><br>
  Nueva arquitectura · ECC V3 · Procesamiento local · Anti-Duplicados · Auto-actualizador
</p>

---

## ✨ ¿Qué es DriveSync PRO?

**DriveSync PRO** es una plataforma orientada a la **gestión, clonación masiva, procesamiento y optimización de contenido** desde Google Drive y directorios locales.

La versión **v2026.1** introduce una nueva arquitectura interna, un flujo independiente de **procesamiento local**, un sistema **Anti-Duplicados**, seguridad criptográfica **ECC V3**, instalación automática de **FFmpeg**, una TUI multifase y un comprobador integrado de actualizaciones mediante GitHub Releases.

> **Desarrollado por JeanDev bajo Streamify+.**

---

## 🆕 Novedades de v2026.1

### 🎬 Modo Anti-Duplicados

Nuevo flujo independiente para procesar contenido directamente desde el almacenamiento local, **sin necesidad de utilizar Google Drive**.

Permite:

- 📂 Seleccionar directorios de entrada y salida.
- 🎞️ Procesar colecciones de vídeo de forma recursiva.
- 🎥 Trabajar con `.mp4`, `.mov`, `.mkv` y otros formatos compatibles.
- 🏷️ Insertar marcas de agua únicas para trazabilidad.
- 🧹 Depurar y optimizar metadatos.
- 📱 Preparar contenido para TikTok, Reels y Shorts.
- 🔄 Procesar grandes cantidades de archivos mediante un flujo automatizado.

---

### 📂 Procesamiento local

DriveSync PRO ya no depende exclusivamente de contenido almacenado en Google Drive.

El procesamiento local permite trabajar directamente con archivos existentes en el equipo y resulta especialmente útil para:

- 🎞️ Grandes colecciones de vídeos.
- 📦 Procesamiento por lotes.
- 📱 Preparación de contenido para redes sociales.
- 🧹 Optimización de metadatos.
- 🏷️ Aplicación de marcas de agua.
- 📴 Flujos de trabajo offline.
- ⚙️ Automatización de procesamiento multimedia.

---

### 🔐 Seguridad avanzada — ECC V3

La versión `v2026.1` incorpora un nuevo sistema criptográfico basado en:

- **ECDSA**
- **NIST P-256**
- **SHA-256**

### Compatibilidad de licencias

| Versión | Tecnología | Estado |
|---|---|---|
| **ECC V3** | ECDSA / NIST P-256 + SHA-256 | ✅ Actual |
| **RSA V2** | RSA 2048 bits | ✅ Legacy |
| **Legacy V1** | RSA 512 bits | ✅ Legacy |

El sistema mantiene compatibilidad con licencias existentes mediante una transición escalonada.

---

### ⚙️ Instalación automática de FFmpeg

La configuración de FFmpeg está automatizada.

DriveSync PRO:

1. 🔍 Comprueba si FFmpeg está disponible en el `PATH`.
2. 📥 Si no está disponible, descarga automáticamente una build estática.
3. 📦 Descomprime los binarios localmente.
4. 🔗 Configura automáticamente el entorno de ejecución.
5. ▶️ Continúa la ejecución sin requerir una instalación manual.

Los binarios se almacenan dentro de:

```text
APP_DATA_DIR/bin
```

Esto permite utilizar las funciones de procesamiento multimedia sin obligar al usuario a instalar y configurar FFmpeg manualmente.

---

### 📊 TUI Multifase

La **Terminal User Interface (TUI)** ha sido mejorada para proporcionar información más precisa durante operaciones de larga duración.

Incluye diferentes fases de procesamiento:

- 📥 Progreso de descarga de binarios.
- ☁️ Descarga previa de vídeos temporales desde la nube.
- 🎞️ Progreso del procesamiento multimedia.
- ⏱️ Progreso de FFmpeg calculado según la duración real del archivo.
- 📈 Métricas actualizadas en tiempo real.
- 🔄 Estados independientes para cada fase.

Esto permite identificar claramente qué está realizando DriveSync PRO durante cada etapa del proceso.

---

### 🔄 Comprobador de actualizaciones

DriveSync PRO incorpora un sistema integrado de comprobación de actualizaciones basado en **GitHub Releases**.

Desde el menú principal es posible:

- 🔍 Comprobar si existe una nueva versión.
- 📋 Consultar las notas de la versión.
- 📦 Visualizar los assets disponibles.
- ⬇️ Descargar directamente una nueva versión.
- 🌐 Abrir la página de la release en el navegador.

Las actualizaciones pueden gestionarse directamente desde la aplicación.

---

### 🧱 Arquitectura desacoplada

El núcleo de DriveSync PRO ha sido reorganizado para separar la **lógica de negocio** de la **interfaz de usuario**.

La comunicación de eventos se ha estandarizado mediante:

`ProgressReporter`

Esta arquitectura permite que el motor funcione independientemente de la interfaz de terminal utilizada actualmente y facilita la incorporación de nuevas interfaces.

La versión `v2026.1` incorpora además la estructura inicial:

`gui/app.py`

Esto prepara el proyecto para futuras interfaces gráficas nativas sin necesidad de reconstruir el núcleo de la aplicación.

---

## ☁️ Google Drive

DriveSync PRO mantiene sus capacidades orientadas a la gestión y procesamiento de contenido en **Google Drive**.

La arquitectura permite combinar operaciones en la nube con procesamiento local, facilitando flujos de trabajo donde los archivos pueden ser descargados temporalmente, procesados y posteriormente utilizados dentro del flujo correspondiente.

---

## 🔑 Activación y licencia

> ⚠️ **DriveSync PRO requiere una licencia válida para funcionar.**

El sistema utiliza una activación vinculada al equipo.

Al iniciar la aplicación, DriveSync PRO detecta y muestra automáticamente el:

```text
Hardware ID (HWID)
```

Este identificador se utiliza para generar la clave de activación correspondiente.

Las licencias pueden utilizar:

- 🔐 ECC V3
- 🔑 RSA V2
- 🗝️ Legacy V1

dependiendo de la versión de licencia emitida.

---

## 🎁 Licencia vitalicia

La licencia vitalicia de DriveSync PRO proporciona acceso indefinido a las funciones disponibles del software.

Incluye:

- ✅ Funciones completas de DriveSync PRO.
- 🔄 Actualizaciones y parches de estabilidad.
- 🛠️ Mejoras futuras del software.
- 🔐 Sistema de activación vinculado al equipo.
- 🧩 Compatibilidad con nuevas versiones publicadas.

---

## 💻 Compatibilidad

<p align="center">
  <img src="https://img.shields.io/badge/Windows-x64-0078D6?style=flat-square&logo=windows&logoColor=white" alt="Windows x64">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python 3.x">
  <img src="https://img.shields.io/badge/FFmpeg-Automatic-007808?style=flat-square&logo=ffmpeg&logoColor=white" alt="FFmpeg">
</p>

La distribución oficial de `v2026.1` está preparada para:

- 🪟 **Windows x64**
- 🐍 **Python**
- 🌐 Equipos con conexión a Internet cuando se utilizan funciones que requieren servicios en línea.
- ☁️ Acceso a las cuentas de Google Drive correspondientes.

### 📦 Distribución

DriveSync PRO se distribuye como un **paquete ZIP con sus componentes**.

Esto permite mantener separados los componentes de la aplicación y facilita:

- ⚙️ Un inicio más consistente.
- 📦 Una distribución más estable.
- 🧩 Separación de componentes.
- 🛡️ Reducción de determinados falsos positivos de antivirus que pueden aparecer con ejecutables altamente empaquetados.

> **Extrae completamente el ZIP antes de ejecutar el programa.**

---

## 📥 Descargar

### 🚀 DriveSync PRO v2026.1

**Versión estable actual**

[![Download](https://img.shields.io/badge/Download-Windows%20x64-0078D6?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/JeanDev-rgb/DriveSync-PRO/releases/download/v2026.1/DriveSync-PRO-v2026.1-Windows-x64.zip)

**Archivo:**

```text
DriveSync-PRO-v2026.1-Windows-x64.zip
```

[📦 Ver release v2026.1](https://github.com/JeanDev-rgb/DriveSync-PRO/releases/tag/v2026.1)

---

## 📦 Instalación

1. 📥 Descarga `DriveSync-PRO-v2026.1-Windows-x64.zip`.
2. 📂 Extrae **todo** su contenido en una carpeta.
3. ▶️ Ejecuta la aplicación.
4. 🔐 Completa el proceso de activación si es necesario.
5. ⚙️ Si FFmpeg no está disponible, DriveSync PRO gestionará automáticamente su instalación.
6. 🚀 Utiliza la aplicación.

> ⚠️ **No ejecutes el programa directamente desde el interior del ZIP.**

---

## 🧩 Flujo general

```text
┌───────────────────────────────┐
│       🚀 DriveSync PRO        │
└───────────────┬───────────────┘
                │
       ┌────────▼────────┐
       │ Detectar entorno│
       └────────┬────────┘
                │
       ┌────────▼────────┐
       │ Configurar      │
       │ dependencias    │
       └────────┬────────┘
                │
       ┌────────▼────────┐
       │ Seleccionar     │
       │ origen/destino  │
       └────────┬────────┘
                │
       ┌────────▼────────┐
       │ Procesar        │
       │ contenido       │
       └────────┬────────┘
                │
       ┌────────▼────────┐
       │ 📊 TUI /        │
       │ ProgressReporter│
       └─────────────────┘
```

---

## 📋 Resumen de v2026.1

| Componente | Estado |
|---|---|
| 🎬 Modo Anti-Duplicados | ✅ |
| 📂 Procesamiento local | ✅ |
| 🎞️ Procesamiento recursivo de vídeo | ✅ |
| 🏷️ Marcas de agua de trazabilidad | ✅ |
| 🧹 Optimización de metadatos | ✅ |
| 🔐 ECC V3 / NIST P-256 | ✅ |
| 🔑 RSA V2 / Legacy V1 | ✅ |
| ⚙️ Instalación automática de FFmpeg | ✅ |
| 📊 TUI multifase | ✅ |
| 📈 Métricas en tiempo real | ✅ |
| 🔄 Comprobador de actualizaciones | ✅ |
| 🧱 `ProgressReporter` | ✅ |
| 🖥️ Arquitectura preparada para GUI | ✅ |
| 📅 Versionado `vYYYY.Release` | ✅ |

---

## 📝 Changelog

### v2026.1 — Nueva arquitectura

#### ✨ Añadido

- 🎬 Modo Anti-Duplicados para carpetas locales.
- 📂 Procesamiento local de vídeos.
- 🎞️ Procesamiento recursivo.
- 🏷️ Marcas de agua de trazabilidad.
- 🧹 Optimización y limpieza de metadatos.
- 🔐 ECC V3 basado en ECDSA NIST P-256 + SHA-256.
- 🔑 Compatibilidad con RSA V2 y Legacy V1.
- ⚙️ Instalación automática de FFmpeg.
- 📊 TUI multifase.
- 📈 Métricas de procesamiento en tiempo real.
- 🔄 Comprobador de actualizaciones mediante GitHub Releases.
- 🧱 Sistema `ProgressReporter`.
- 🖥️ Estructura inicial para futura GUI.
- 📅 Nuevo esquema de versionado `vYYYY.Release`.

#### 🚀 Mejorado

- 🏗️ Arquitectura interna.
- 🔌 Separación entre núcleo e interfaz.
- 📦 Gestión de dependencias multimedia.
- 📊 Visualización del progreso.
- 🎞️ Flujo de procesamiento de vídeo.
- 🔄 Gestión de actualizaciones.

#### 🔐 Seguridad

- ECC V3 establecido como sistema criptográfico actual.
- Compatibilidad mantenida con sistemas de licencias anteriores.

---

## 🔍 Comparación de versiones

Consulta los cambios realizados desde **v4.3.1**:

[![Compare](https://img.shields.io/badge/Compare-v4.3.1%20→%20v2026.1-6f42c1?style=for-the-badge&logo=github)](https://github.com/JeanDev-rgb/DriveSync-PRO/compare/4.3.1...v2026.1)

---

## 📩 Soporte y contacto

Para información sobre licencias, activación o soporte, puedes contactar directamente con el desarrollador.

### 🌐 ForoBeta

**JeanDev**

[Visitar perfil de JeanDev](https://forobeta.com/members/jeandev.362650/)

### 💬 WhatsApp

[Contactar por WhatsApp (+51 925030997)](https://wa.me/51925030997)

---

## 📜 Licencia

DriveSync PRO utiliza un sistema de **licenciamiento comercial**.

El software requiere una licencia válida para su utilización.

Consulta las condiciones de licencia correspondientes antes de distribuir, modificar o utilizar el software.

---

## 🚀 DriveSync PRO v2026.1

> **Una nueva generación de DriveSync PRO.**

**Más automatización.**

**Más seguridad.**

**Más control.**

**Una arquitectura preparada para el futuro.**

---

<p align="center">
  <strong>© DriveSync PRO — v2026.1</strong><br>
  <sub>Desarrollado por JeanDev · Streamify+</sub>
</p>
