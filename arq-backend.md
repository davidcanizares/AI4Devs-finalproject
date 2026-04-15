# ARQ Backend — Codec-PMS Gavilán

## 1. Contexto

Este documento define la arquitectura backend del sistema Codec-PMS Gavilán, basada en Drupal 10/11 como decisión técnica impuesta.

El sistema debe cubrir:
- Gestión operativa interna (core PMS)
- Automatización de procesos (check-in, comunicaciones)
- Cumplimiento legal (SES.MIR)
- Escalabilidad modular

Basado en:
- Definición funcional :contentReference[oaicite:0]{index=0}  
- PRD :contentReference[oaicite:1]{index=1}  
- User Stories :contentReference[oaicite:2]{index=2}  

---

## 2. Decisión arquitectónica

### 2.1 Enfoque general

Arquitectura **modular basada en Drupal como framework de dominio**, no solo como CMS.

Patrón aplicado:
- **Domain-Oriented Architecture sobre Drupal**
- Separación por módulos de negocio
- API-first (preparado para desacoplar frontend)

---

### 2.2 Principios

- Core del sistema en backend (no frontend)
- Entidades como fuente de verdad
- Bajo acoplamiento entre módulos
- Preparado para integraciones externas
- Extensible (módulos plug-in)

---

## 3. Stack tecnológico

### Backend
- Drupal 10/11
- PHP 8.4+

### Base de datos
- MySQL / MariaDB

### APIs
- JSON:API (Drupal core)
- Custom REST endpoints (cuando aplique)

### Otros
- Queue API (procesos async)
- Cron (automatizaciones)
- Symfony components (interno Drupal)

---

## 4. Arquitectura lógica

### 4.1 Capas
[ Presentation Layer ]
Drupal (Forms, Controllers, JSON:API)

[ Application Layer ]
Custom Modules (lógica de negocio)

[ Domain Layer ]
Entidades (Reserva, Cliente, Unidad, etc.)

[ Infrastructure Layer ]
DB, APIs externas, SES.MIR, Email

---

## 5. Módulos Drupal (diseño)

### 5.1 Módulos core del dominio

#### pms_unit
- Gestión de unidades (alojamientos)

#### pms_reservation
- Reservas
- Estados
- Validación de disponibilidad

#### pms_customer
- Clientes
- Flags (conflictivo)

#### pms_calendar
- Lógica de disponibilidad
- Bloqueos

---

### 5.2 Módulos funcionales

#### pms_checkin
- Generación de tokens
- Formularios externos
- Estados de check-in

#### pms_document
- Generación de contratos PDF

#### pms_invoice
- Facturación básica

#### pms_notes
- Notas internas

---

### 5.3 Integraciones

#### pms_channel
- iCal sync (fase inicial)
- Preparado para APIs

#### pms_sesmir
- Integración con SES.MIR
- Envío de partes
- Gestión de errores

#### pms_notifications
- Emails
- Sistema de colas

---

## 6. Modelo de datos (Drupal Entities)

### 6.1 Entidades principales

#### Unidad
- id
- nombre
- capacidad
- estado

#### Reserva
- id
- unidad_id
- cliente_id
- fecha_inicio
- fecha_fin
- estado
- precio

#### Cliente
- id
- nombre
- email
- teléfono
- conflictivo (bool)

#### Check-in
- id
- reserva_id
- token
- estado
- fecha_completado

#### Factura
- id
- reserva_id
- importe
- fecha

#### Bloqueo
- unidad_id
- fecha_inicio
- fecha_fin

---

### 6.2 Relaciones clave

- Reserva → Unidad (N:1)
- Reserva → Cliente (N:1)
- Reserva → Check-in (1:1)
- Reserva → Factura (1:N)

---

## 7. Gestión de disponibilidad (clave PMS)

### Estrategia

NO depender completamente de BAT.

Implementación:
- Validación en capa aplicación
- Queries optimizadas por fechas
- Índices DB en:
  - unidad_id
  - fecha_inicio / fecha_fin

Regla crítica:
- No permitir solapamientos

---

## 8. Check-in automatizado

### Arquitectura

- Trigger: cambio de estado reserva
- Cron + Queue Worker:
  - Envío emails
- Endpoint público:
  - /checkin/{token}

### Seguridad
- Token único
- Expiración configurable

---

## 9. Integración SES.MIR

### Flujo

1. Check-in completado
2. Transformación de datos
3. Envío API / fichero
4. Registro de estado

### Consideraciones
- Reintentos automáticos
- Logging obligatorio
- Trazabilidad

---

## 10. API

### Estrategia

- JSON:API para entidades básicas
- Endpoints custom para:
  - Check-in público
  - Acciones específicas (bloqueos, validaciones)

---

## 11. Seguridad

### Acceso
- Roles Drupal:
  - admin
  - gestor
  - operativo

### Protección
- Tokens en check-in
- Validación input
- Sanitización

### Legal
- GDPR:
  - minimización datos
  - trazabilidad

---

## 12. Procesos asíncronos

Uso de:
- Queue API

Casos:
- Envío check-in
- SES.MIR
- Emails

---

## 13. Infraestructura (visión backend)

- Entorno local: DDEV
- Contenedores (Colima)
- CI/CD (pendiente definir)
- Cron activo

---

## 14. Testing

### Tipos

- Unit tests (lógica)
- Kernel tests (Drupal)
- Functional tests

### Cobertura mínima
- Reservas
- Validación disponibilidad
- Check-in

---

## 15. Riesgos técnicos

1. BAT sobrecarga arquitectura
2. Integraciones externas inestables
3. Complejidad en disponibilidad
4. Modelo de datos mal definido

---

## 16. Decisiones clave tomadas

- Drupal como core backend (no solo CMS)
- Arquitectura modular por dominio
- API-first preparado para desacoplar frontend
- Lógica crítica en backend (no JS)

---

## 17. Decisiones pendientes

- Uso real de BAT vs custom completo
- Canal de notificaciones (email vs multicanal)
- Integración channel manager (iCal vs API)
- Multi-tenant (si evoluciona a SaaS)

---

## 18. Conclusión técnica

La arquitectura propuesta:

- Es coherente con un PMS real
- Minimiza dependencias externas
- Prioriza operativa interna (correcto según PRD)
- Permite evolucionar a sistema más complejo sin rehacer base

Riesgo principal:
👉 No acotar el alcance y convertirlo en ERP completo
