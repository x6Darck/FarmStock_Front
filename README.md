# FarmStock - Frontend (Aplicación de escritorio)

![Electron](https://img.shields.io/badge/Electron-47848F?style=flat&logo=electron&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Offline](https://img.shields.io/badge/Funciona-sin%20conexi%C3%B3n-2EA44F?style=flat)
![Estado](https://img.shields.io/badge/Estado-%F0%9F%94%A7%20COMPLETAR-lightgrey?style=flat)

**FarmStock** es un sistema de inventario para la gestión de **herramientas y demás elementos de la finca del SENA ubicada en El Zulia (Cúcuta), Norte de Santander**.

Este repositorio contiene la **aplicación de escritorio** de FarmStock, desarrollada con **Electron**, que ofrece la interfaz para registrar, consultar y controlar el inventario. Se comunica con el backend de FarmStock, desarrollado con Spring Boot.

El sistema fue diseñado para **funcionar sin una conexión estable a internet**, una condición habitual en entornos rurales como el de la finca.

> 🔧 **COMPLETAR:** indica si fue un proyecto desarrollado de forma individual o en equipo, y en qué contexto (por ejemplo, proyecto formativo del SENA).

---

## 📑 Tabla de contenido

- [Características principales](#-características-principales)
- [Funcionamiento sin conexión](#-funcionamiento-sin-conexión)
- [Arquitectura](#️-arquitectura)
- [Stack tecnológico](#-stack-tecnológico)
- [Integración con el backend](#-integración-con-el-backend)
- [Requisitos](#-requisitos)
- [Instalación y ejecución local](#️-instalación-y-ejecución-local)
- [Generación del instalador](#-generación-del-instalador)
- [Estructura del proyecto](#️-estructura-del-proyecto)
- [Ecosistema FarmStock](#-ecosistema-farmstock)
- [Estado del proyecto](#-estado-del-proyecto)
- [Desarrollo](#-desarrollo)
- [Propiedad y uso](#-propiedad-y-uso)
- [Autor](#-autor)

---

## 🚀 Características principales

- Gestión del inventario de herramientas y elementos de la finca
- Aplicación de escritorio instalable en equipos de la institución
- Diseñada para operar sin conexión estable a internet
- Comunicación con un backend propio mediante API REST

> 🔧 **COMPLETAR:** reemplaza o amplía esta lista con las funciones reales de la aplicación. Por ejemplo: registro y edición de herramientas, categorías, control de entradas y salidas, préstamos, estado o ubicación de cada elemento, búsqueda y filtros, reportes, usuarios y roles. Deja solo lo que realmente existe en el código.

---

## 📡 Funcionamiento sin conexión

La finca no siempre cuenta con internet estable, por lo que FarmStock se planteó desde el inicio para **no depender de una conexión permanente**. Por eso se eligió una aplicación de escritorio con Electron, que se ejecuta en el propio equipo, en lugar de una aplicación web alojada en un servidor remoto.

> 🔧 **COMPLETAR:** explica en dos o tres frases cómo se logra esto realmente. Por ejemplo: dónde se ejecuta el backend (en el mismo equipo o en un computador de la red local), qué base de datos se usa y dónde se guardan los datos, y si hay algún mecanismo de respaldo o sincronización.

---

## 🏗️ Arquitectura

La aplicación de escritorio actúa como cliente del backend de FarmStock.

```text
Usuario
   │
   ▼
Aplicación de escritorio (Electron)
   │
   ▼
Comunicación con la API REST
   │
   ▼
FarmStock Backend (Spring Boot)
   │
   ▼
Base de datos
```

> 🔧 **COMPLETAR:** confirma este flujo y ajústalo si es distinto (por ejemplo, si Electron inicia el backend automáticamente al abrir la aplicación).

---

## 🧰 Stack tecnológico

| Tecnología | Uso |
|---|---|
| Electron | Aplicación de escritorio multiplataforma |
| Node.js / npm | Entorno de ejecución y gestión de dependencias |

> 🔧 **COMPLETAR:** agrega el resto de tecnologías que uses en la interfaz, según tu `package.json` (por ejemplo, el framework o la librería de UI, el cliente HTTP, el empaquetador).

---

## 🔗 Integración con el backend

La aplicación se comunica con **FarmStock Backend** mediante una API REST.

> 🔧 **COMPLETAR:** indica cómo se configura la dirección del backend (archivo de configuración, variable de entorno o valor fijo) y cuál es la URL por defecto en desarrollo. No incluyas direcciones ni claves privadas.

---

## 📋 Requisitos

Para ejecutar el proyecto localmente se requiere:

- Node.js
- npm
- Git
- Backend de FarmStock en ejecución

> 🔧 **COMPLETAR:** indica la versión mínima de Node.js que usaste.

---

## ⚙️ Instalación y ejecución local

### 1. Clonar el repositorio

```bash
git clone https://github.com/x6Darck/FarmStock_Front.git
cd FarmStock_Front
```

### 2. Instalar dependencias

```bash
npm install
```

### 3. Ejecutar la aplicación en modo desarrollo

```bash
npm start
```

> 🔧 **COMPLETAR:** verifica en la sección `scripts` de tu `package.json` que el comando para iniciar sea `npm start`, y corrígelo si es otro (por ejemplo, `npm run dev`).

---

## 📦 Generación del instalador

> 🔧 **COMPLETAR:** si el proyecto genera un instalador (por ejemplo con `electron-builder` o `electron-forge`), escribe aquí el comando y dónde queda el archivo resultante. Si no lo hace, elimina esta sección y su enlace en la tabla de contenido.

---

## 🗂️ Estructura del proyecto

```text
FarmStock_Front/
│
└── (COMPLETAR: pega aquí la estructura real de carpetas)
```

> 🔧 **COMPLETAR:** en Windows puedes obtenerla con `tree /F` dentro de la carpeta del proyecto. Deja solo las carpetas y los archivos principales, y agrega una breve descripción a cada uno.

---

## 🔄 Ecosistema FarmStock

FarmStock está compuesto por dos aplicaciones.

### ⚙️ FarmStock Backend

API REST desarrollada con **Spring Boot**, encargada de la lógica de negocio y de la persistencia de los datos del inventario.

**Repositorio:** [github.com/x6Darck/FarmStock_Backend](https://github.com/x6Darck/FarmStock_Backend)

### 🖥️ FarmStock Frontend

Aplicación de escritorio desarrollada con **Electron** (este repositorio).

**Repositorio:** [github.com/x6Darck/FarmStock_Front](https://github.com/x6Darck/FarmStock_Front)

---

## 📌 Estado del proyecto

**Estado:** 🔧 COMPLETAR (por ejemplo: Completado / En uso / En desarrollo)

FarmStock fue desarrollado para cubrir una necesidad real de control de inventario en la finca del SENA ubicada en El Zulia (Cúcuta), con la condición de funcionar sin conexión estable a internet.

---

## 👨‍💻 Desarrollo

> 🔧 **COMPLETAR:** lista lo que hiciste tú en esta parte del proyecto, con frases cortas. Por ejemplo: diseño de la interfaz, integración con la API, empaquetado con Electron, validación de formularios. Incluye solo lo que sea cierto.

---

## 📄 Propiedad y uso

FarmStock fue desarrollado para la finca del SENA ubicada en El Zulia (Cúcuta).

Este repositorio se presenta con fines demostrativos y de **portafolio profesional**. Su publicación no implica la transferencia de derechos de propiedad intelectual ni autorización para copiar, modificar, distribuir o utilizar el software con fines comerciales.

> 🔧 **COMPLETAR:** confirma que puedes publicar el proyecto y que este texto es compatible con los acuerdos o las normas de propiedad intelectual bajo los que se desarrolló.

El repositorio no incluye:

- Credenciales
- Contraseñas
- Datos personales
- Información sensible
- Configuraciones privadas

---

## 👤 Autor

**Jean Pier Gómez**

---

<p align="center">
  <strong>FarmStock — Sistema de inventario para la finca del SENA</strong><br>
  Desarrollado con Spring Boot y Electron.
</p>
