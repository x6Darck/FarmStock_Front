# FarmStock - Aplicación de escritorio

![Electron](https://img.shields.io/badge/Electron-28-47848F?style=flat&logo=electron&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Offline](https://img.shields.io/badge/Funciona-sin%20conexi%C3%B3n-2EA44F?style=flat)
![Estado](https://img.shields.io/badge/Estado-Completado-2EA44F?style=flat)

**FarmStock** es un sistema de inventario para la gestión de **herramientas y equipos de la finca del SENA ubicada en El Zulia (Cúcuta), Norte de Santander**.

Este repositorio contiene la **aplicación de escritorio**, desarrollada con **Electron**, que ofrece la interfaz para registrar, consultar y controlar el inventario. Se comunica con el backend de FarmStock, una API REST desarrollada con Spring Boot que vive en su propio repositorio.

FarmStock fue pensado para **funcionar sin una conexión estable a internet**: la aplicación, el backend y la base de datos se ejecutan en el propio equipo, sin depender de servicios en la nube.

El sistema fue **diseñado y desarrollado de forma individual**.

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

- **Inventario de herramientas:** registro, consulta, edición y eliminación, con el detalle de cada unidad.
- **Registro de aprendices y personas:** alta y búsqueda por documento o por ficha.
- **Equipos de cómputo:** registro y consulta por código o por cédula, con sus movimientos de entrada y salida.
- **Registro de salidas** de herramientas.
- **Inicio de sesión y perfil** de usuario según el cargo.
- **Estadísticas** con actualización periódica y **exportación de informes en PDF**.
- **Notificaciones** por correo desde la interfaz.
- **Modo oscuro** y ventana sin bordes con controles propios.
- **Página institucional** "Quiénes somos" con la misión y la visión.

---

## 📡 Funcionamiento sin conexión

La finca no siempre cuenta con internet estable, por lo que la aplicación se diseñó para no depender de él:

- **Todo corre en el equipo.** La aplicación de escritorio, el backend de Spring Boot y la base de datos MySQL se ejecutan localmente. No se usan servicios alojados en la nube.
- **Respaldo local.** Si el backend no responde, el cliente (`FSApiClient.js`) guarda y consulta los datos de herramientas y aprendices en el almacenamiento local de la aplicación (`localStorage`), para no interrumpir el trabajo.

Solo el envío de notificaciones por correo requiere conexión a internet.

---

## 🏗️ Arquitectura

```text
  Aplicación de escritorio (Electron)
  HTML · CSS · JavaScript
              │
              │  FSApiClient.js · REST API
              ▼
  FarmStock Backend (Spring Boot)
              │
              ▼
        MySQL (local)


  Sin respuesta del backend → respaldo en localStorage
```

El proceso principal (`main.js`) crea la ventana y gestiona la navegación, el control de la ventana y la generación de PDF. El archivo `preload.js` expone a la interfaz solo las funciones necesarias, con `contextIsolation` activado y `nodeIntegration` desactivado.

---

## 🧰 Stack tecnológico

| Tecnología | Uso |
|---|---|
| Electron 28 | Aplicación de escritorio |
| electron-builder | Empaquetado e instalador |
| HTML, CSS y JavaScript | Interfaz de usuario |
| Fetch API | Comunicación con la API REST |
| localStorage | Respaldo local sin conexión |
| Node.js / npm | Entorno de desarrollo |

---

## 🔗 Integración con el backend

La aplicación consume la API de **FarmStock Backend** (Spring Boot). El backend debe estar en ejecución antes de abrir la aplicación.

La dirección del backend se define en la constante `API_BASE` del archivo `app/FSApiClient.js` (y en los demás archivos del directorio `app/` que consumen la API) y debe apuntar al puerto donde corre el backend. Por defecto, Spring Boot usa el puerto `8080`.

Repositorio del backend: [github.com/x6Darck/FarmStock_Backend](https://github.com/x6Darck/FarmStock_Backend)

---

## 📋 Requisitos

- Node.js y npm
- Git
- [FarmStock Backend](https://github.com/x6Darck/FarmStock_Backend) en ejecución (requiere Java 21 y MySQL)

---

## ⚙️ Instalación y ejecución local

### 1. Iniciar el backend

Sigue las instrucciones del repositorio [FarmStock_Backend](https://github.com/x6Darck/FarmStock_Backend).

### 2. Clonar este repositorio

```bash
git clone https://github.com/x6Darck/FarmStock_Front.git
cd FarmStock_Front
```

### 3. Instalar dependencias

```bash
npm install
```

### 4. Ejecutar la aplicación

```bash
npm start
```

---

## 📦 Generación del instalador

```bash
npm run dist
```

El resultado se genera con **electron-builder** en la carpeta `dist/`.

---

## 🗂️ Estructura del proyecto

```text
FarmStock_Front/
│
├── main.js                  # Proceso principal de Electron
├── preload.js               # Puente seguro entre Electron y la interfaz
├── package.json
│
└── app/                     # Interfaz de usuario
    ├── HTML/                # Pantallas (login, inventario, estadísticas, equipos…)
    ├── CSS/                 # Estilos
    ├── imagenes/            # Recursos gráficos
    ├── FSApiClient.js       # Cliente de la API con respaldo local
    └── *.js                 # Lógica de cada pantalla
```

---

## 🔄 Ecosistema FarmStock

FarmStock se compone de dos repositorios.

### 🖥️ FarmStock Frontend

Aplicación de escritorio desarrollada con **Electron** (este repositorio).

**Repositorio:** [github.com/x6Darck/FarmStock_Front](https://github.com/x6Darck/FarmStock_Front)

### ⚙️ FarmStock Backend

API REST desarrollada con **Java y Spring Boot**. Gestiona herramientas, préstamos, mantenimientos, aprendices, usuarios y equipos de cómputo, y genera códigos QR y notificaciones por correo.

**Repositorio:** [github.com/x6Darck/FarmStock_Backend](https://github.com/x6Darck/FarmStock_Backend)

---

## 📌 Estado del proyecto

**Estado:** Completado

FarmStock fue desarrollado para cubrir una necesidad real de control de inventario en la finca del SENA ubicada en El Zulia (Cúcuta), con la condición de funcionar sin conexión estable a internet.

---

## 👨‍💻 Desarrollo

FarmStock fue **diseñado, estructurado y desarrollado de forma individual**. En la aplicación de escritorio se realizó:

- Diseño de la interfaz y de las pantallas
- Aplicación de escritorio con Electron y comunicación segura entre procesos
- Cliente de la API con respaldo local para trabajar sin conexión
- Inicio de sesión y gestión de la sesión del usuario
- Módulos de herramientas, aprendices y equipos de cómputo
- Estadísticas y exportación de informes en PDF
- Modo oscuro y navegación entre pantallas
- Empaquetado de la aplicación con electron-builder
- Integración con el backend de Spring Boot

---

## 📄 Propiedad y uso

FarmStock fue desarrollado para la finca del SENA ubicada en El Zulia (Cúcuta).

Este repositorio se publica **únicamente con fines demostrativos y de portafolio profesional**. Su publicación no implica la transferencia de derechos de propiedad intelectual ni autorización para copiar, modificar, distribuir o utilizar el software con fines comerciales.

El repositorio no incluye credenciales, contraseñas, datos personales ni configuraciones privadas.

---

## 👤 Autor

**Jean Pier Gómez**

Desarrollo individual de FarmStock.

---

<p align="center">
  <strong>FarmStock — Sistema de inventario para la finca del SENA</strong><br>
  Desarrollado con Electron y Spring Boot.
</p>
