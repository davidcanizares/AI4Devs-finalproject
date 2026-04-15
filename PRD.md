# PRD — Codec-PMS Gavilán

## 1. Resumen del producto

Codec-PMS Gavilán es un sistema PMS (Property Management System) especializado en la gestión de alojamientos rurales, enfocado en optimizar la operativa interna, automatizar procesos clave y garantizar el cumplimiento normativo, reduciendo la carga manual y los errores operativos.

El producto prioriza la eficiencia operativa frente a la capa pública, orientado a usuarios no expertos en gestión hotelera.

---

## 2. Objetivos del producto

### Objetivo principal
Centralizar y automatizar la gestión de un complejo rural, reduciendo el tiempo operativo, minimizando errores y garantizando cumplimiento legal.

### Objetivos específicos
- Reducir gestión manual de reservas
- Evitar overbooking
- Automatizar comunicaciones con clientes
- Cumplir normativa del Ministerio del Interior
- Mejorar control de rentabilidad
- Facilitar operativa diaria (limpieza, preparación, incidencias)

---

## 3. Stakeholders

- Propietario del complejo (negocio)
- Equipo de operaciones (gestores de reservas)
- Personal de limpieza/mantenimiento
- Equipo técnico (desarrollo)
- Clientes finales

---

## 4. Usuarios y roles

### Internos
- **Administrador**
  - Configuración global
  - Acceso total
  - Informes y facturación

- **Gestor de reservas**
  - Gestión de reservas
  - Calendario
  - Clientes

- **Personal operativo**
  - Visualización de tareas
  - Notas internas

### Externos
- **Cliente**
  - Registro
  - Reserva
  - Check-in

---

## 5. Alcance del producto

### Incluido (In Scope)
- Gestión de alojamientos
- Gestión de reservas
- Calendario
- Clientes
- Check-in automatizado
- Facturación básica
- Integración con Ministerio del Interior
- Sincronización básica con plataformas externas
- Web pública con motor de reservas

### No incluido (Out of Scope - fase inicial)
- ERP completo
- Contabilidad avanzada
- Revenue management avanzado
- Integraciones API complejas (fase posterior)

---

## 6. Funcionalidades principales

### 6.1 Gestión de alojamientos y reservas
- CRUD de unidades
- Creación de reservas (frontend y backend)
- Estados de reserva
- Bloqueo de fechas
- Notas internas

### 6.2 Calendario
- Vista global por unidades
- Gestión de disponibilidad
- Edición rápida

### 6.3 Clientes
- Registro y autenticación
- Historial de reservas
- Marcado de clientes conflictivos

### 6.4 Web pública
- Catálogo de alojamientos
- Disponibilidad
- Motor de reservas
- Contacto

### 6.5 Integraciones externas
- Sincronización con plataformas externas (iCal inicialmente)
- Integración con Ministerio del Interior (SES.MIR)

### 6.6 Operativa interna
- Notas operativas
- Preparación de unidades
- Contrato imprimible

### 6.7 Check-in automatizado
- Envío automático previo a la llegada
- Formulario digital de huéspedes
- Asociación a reserva
- Estados de check-in
- Posible envío automático al Ministerio

### 6.8 Facturación
- Generación automática desde reserva
- Exportación PDF

### 6.9 Inventario
- Control básico de stock
- Seguimiento de consumibles

### 6.10 Informes
- Ocupación
- Ingresos
- Rentabilidad

---

## 7. Requisitos funcionales

### RF-01
El sistema debe permitir crear, editar y cancelar reservas.

### RF-02
El sistema debe mostrar un calendario de disponibilidad por unidad.

### RF-03
El sistema debe permitir registro y autenticación de usuarios.

### RF-04
El sistema debe enviar automáticamente comunicaciones de check-in.

### RF-05
El sistema debe permitir la introducción de datos de huéspedes.

### RF-06
El sistema debe integrarse con el Ministerio del Interior.

### RF-07
El sistema debe generar facturas asociadas a reservas.

### RF-08
El sistema debe permitir notas internas en reservas y clientes.

### RF-09
El sistema debe sincronizar disponibilidad con plataformas externas.

---

## 8. Requisitos no funcionales

### Rendimiento
- Respuesta < 2s en operaciones críticas

### Seguridad
- Control de accesos por roles
- Tokens seguros en check-in
- Cumplimiento GDPR

### Disponibilidad
- Alta disponibilidad en gestión interna

### Escalabilidad
- Arquitectura modular

### Usabilidad
- Interfaz optimizada para usuarios no técnicos

---

## 9. Flujos clave

### Flujo de reserva
1. Usuario selecciona alojamiento
2. Consulta disponibilidad
3. Realiza reserva
4. Sistema confirma
5. Reserva registrada en calendario

### Flujo de check-in
1. Reserva confirmada
2. Sistema envía enlace automático
3. Cliente introduce datos
4. Sistema valida y almacena
5. Datos disponibles para envío legal

### Flujo operativo interno
1. Nueva reserva
2. Generación de tareas internas
3. Preparación de unidad
4. Check-in completado

---

## 10. Métricas de éxito (KPIs)

- Reducción de tiempo de gestión (>30%)
- Reducción de errores en reservas
- % de check-ins completados antes de llegada
- Ocupación media
- Tiempo medio de gestión por reserva

---

## 11. Roadmap

### Fase 1 (MVP)
- Reservas internas
- Calendario
- Clientes
- Notas
- Contrato PDF

### Fase 2
- Web pública
- Check-in automatizado
- Facturación básica
- Integración Ministerio

### Fase 3
- Sincronización con plataformas
- Informes avanzados

### Fase 4
- Actividades
- Fichaje empleados
- Optimización operativa

---

## 12. Riesgos

- Complejidad en integraciones externas
- Cumplimiento legal incorrecto
- Sobrecarga funcional
- Baja adopción por mala UX

---

## 13. Decisiones abiertas

- Integración directa vs intermediario (channel manager)
- Nivel de complejidad de facturación
- Canal de envío de check-in (email vs multicanal)
- Arquitectura multi-tenant (producto vs uso interno)

---

## 14. Consideraciones técnicas

- Backend basado en Drupal (entidades, roles, permisos)
- Uso potencial de módulo BAT para disponibilidad
- Desarrollo de módulos custom para:
  - Check-in
  - Integraciones
  - Facturación
- API-first para futuras integraciones

---
