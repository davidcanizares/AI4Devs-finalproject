> Detalla en esta sección los prompts principales utilizados durante la creación del proyecto, que justifiquen el uso de asistentes de código en todas las fases del ciclo de vida del desarrollo. Esperamos un máximo de 3 por sección, principalmente los de creación inicial o  los de corrección o adición de funcionalidades que consideres más relevantes.
Puedes añadir adicionalmente la conversación completa como link o archivo adjunto si así lo consideras


## Índice

1. [Descripción general del producto](#1-descripción-general-del-producto)
2. [Arquitectura del sistema](#2-arquitectura-del-sistema)
3. [Modelo de datos](#3-modelo-de-datos)
4. [Especificación de la API](#4-especificación-de-la-api)
5. [Historias de usuario](#5-historias-de-usuario)
6. [Tickets de trabajo](#6-tickets-de-trabajo)
7. [Pull requests](#7-pull-requests)

---

## 1. Descripción general del producto

**Prompt 1:**
LLM utilizado: ChatGPT

Eres un experto Product Owner y Business Analyst, necesito es tu visión general e inicial del proyecto para adaptar este boceto inicial, estructurarlo y completarlo:
Codec-PMS Gavilán es un Property Management System orientado a la gestión de complejos rurales y basado en el uso interno de la aplicación, potenciando el control y la gestión de alojamientos rurales para empresas, autónomos o partículares que necesitan optimizar su tiempo de gestión al no tratarse de su core de negocio.

La idea surge tras la adquisición de un complejo rural por la empresa Grupo Codec Technology y la necesidad de realizar la mejor gestión en el menor tiempo posible, automizando y adaptando todos los procesos posibles de manera que mantenga la calidad de servicio con el menor coste tanto temporal como económico.

Características principales:
-	Página web corporativa con información de los alojamientos, visualización de calendarios, formulario de contacto y acceso al backend.
-	Posibilidad de reserva por parte de los usuarios que deberán crear su cuenta antes de reservar.
-	Posibilidad de generar reservas a nivel interno con un rol de gestor de reservas
-	Gestión de calendario de reservas, podemos utilizar un módulo contribuido como BAT (Booking and Availability Management Tools)
-	Sincronización del calendario con plataformas externas: Booking, Airbnb, Escapada Rural.
-	Posibilidad de incluir notas internas en las reservas para indicaciones de montar las habitaciones.
-	Posibilidad de incluir notas internas a los alojados y bloquear futuras reservas para los conflictivos.
-	Envío de check-in automático a los usuarios
-	Sincronización con la web del ministerio del interior para el registro de reservas y estancias de alojamientos, con la web: https://hospedajes.ses.mir.es/hospedajes-sede
-	Generación de facturas.
-	Gestión de stock de elementos del complejo como sábanas, mantas, productos de limpieza, etc.
-	Informes de rentabilidad.
-	Dentro del complejo definimos como unidad el elemento que se alquila.
-	El fuerte de la aplicación es la gestión interna, debe funcionar más como un programa de gestión hotelera como PMS (Property Management System) ejemplo OfiRural (OfiHotel20) o AvaiBook pero orientado a una casa rural.
-	Desde la aplicación debe poder imprimirse el contrato de reserva para los cllientes.
-	El proyecto debe ser modular para poder realizar ampliaciones en el futuro como:
  -	Sistema de fichaje de empleados
  -	Añadir reservas complementarias de actividades:
    -	Pintball
    -	Canoas
    -	Alquiler de bicicleta
    -	Etc.


**Prompt 2:**
LLM utilizado: ChatGPT

Eres un experto Product Owner y Business Analyst, según la información generada del proyecto extráeme: - Objetivo - Características y funcionalidades principales
General la información en formato markdown.

**Prompt 3:**
LLM utilizado: ChatGPT

Eres un experto Product Manager y experto en aplicaciones PMS como la que estamos desarrollando, trabajas con un equipo colaborativo de:
- Product Owner
- UX Designer
- Tech Lead
- Stakeholders de negocio

Genera, en base a la información que hemos generado, tu experiencia y la aportación de tu equipo colaborativo el PRD de nuestra aplicación.

General la información en formato markdown.

---

## 2. Arquitectura del Sistema

### **2.1. Diagrama de arquitectura:**

**Prompt 1:**
LLM utilizado: ChatGPT

Actúa como Tech Lead senior con experiencia en PMS (Property Management System), cuentas con la colaboración de un Software Engineer experto en Drupal y un Product Owner experto en validación funcional.  

A partir de la información generada y del PRD genera el ARQ Backend. Adjunto documentación

**Prompt 2:**
LLM utilizado: ChatGPT

Actúa como Tech Lead senior con experiencia en PMS (Property Management System), cuentas con la colaboración de un UX Designer experto y un Product Owner experto. 

Decisión a documentar

Comparativa:

| Opción             | Pros                                   | Contras                              |
|--------------------|----------------------------------------|--------------------------------------|
| Drupal (Twig)      | Integración directa, menor complejidad | UX limitada                          |
| React (decoupled)  | UX avanzada, escalable                 | Mayor complejidad, APIs necesarias   |

Resultado esperado
-	Decisión argumentada (no ambigua) 
-	Arquitectura elegida: 
  -	Monolítica (Drupal) 
  -	Headless (Drupal + React) 

**Prompt 3:**
LLM utilizado: ChatGPT

Como experto Tech Lead y Arquitecto de software en proyectos PMS (Property Management System) y Drupal para Front y Backend crea a partir de la información generada y herramientas como Mermaid o Draw.io el Documento de Arquitectura con la información y diagramas necesarios.

El documento debe incluir:
- Frontend 
- Backend (Drupal) 
- Base de datos 
- Integraciones externas: 
  - SES.MIR 
  - Plataformas (Booking, etc.)
 
Genera la salida en formato markdown

### **2.2. Descripción de componentes principales:**

**Prompt 1:**
LLM utilizado: ChatGTP

Como experto Tech Lead y Arquitecto de software en proyectos PMS (Property Management System) y Drupal para Front y Backend crea a partir de la información generada un documento anexo al de ARQ en formato markdown con la descripción detallada de los componentes principales.

Adjunto documento ARQ

**Prompt 2:**
LLM utilizado: ChatGTP

Como experto Tech Lead y Arquitecto de software en proyectos PMS (Property Management System) y Drupal para Front y Backend genera el documento ampliando y documentando más el punto 3. Backend (Drupal Core + Custom Modules)

**Prompt 3:**

LLM utilizado: ChatGTP

Como experto Tech Lead y Arquitecto de software en proyectos PMS (Property Management System) y Drupal para Front y Backend genera el documento ampliando y documentando más el punto 4. Módulos PMS (detalle técnico)

Genera un markdown descargable.

### **2.3. Descripción de alto nivel del proyecto y estructura de ficheros**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.4. Infraestructura y despliegue**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.5. Seguridad**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.6. Tests**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 3. Modelo de Datos

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 4. Especificación de la API

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 5. Historias de Usuario

**Prompt 1:**
LLM utilizado: ChatGPT
Actúa como un Product Owner senior con experiencia en metodologías ágiles y PMS (Property Management System)

A partir de la información generada y del PRD, genera todas las User Stories para la fase inicial que cumplan los criterios INVEST. Para cada una incluye:
- Título descriptivo
- Historia en formato "Como [rol], quiero [acción], para [beneficio]"
- 3 criterios de aceptación en formato BDD (Dado que/Cuando/Entonces)
- Estimación de complejidad (S/M/L)
- Evaluación breve contra INVEST
Genera la salida en formato markdown.

Después de generar las historias, sugiere un orden de priorización
para el MVP y justifica tu decisión.
Genera la salida en formato markdown.

**Prompt 2:**
LLM utilizado: ChatGPT
Has omitido el rol de usuario de la tienda, es decir aquel usuario que debe registrarse para poder comprar, ya que para realizar la compra el registro se ha determinado como obligatorio.
Indícame dónde debo añadirlo en el documento y dame la respuesta en formato markdown.
 
**Prompt 3:**
LLM utilizado: ChatGPT
Actúa como un Product Owner senior con experiencia en metodologías ágiles y PMS (Property Management System)
A partir de la información generada, el PRD y las User histories sugiere un orden de priorización para el MVP y justifica tu decisión.
Genera la salida en formato markdown.

---

### 6. Tickets de Trabajo

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 7. Pull Requests

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**
