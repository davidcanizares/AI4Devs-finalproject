# Codec-PMS Gavilán

## 1. Definición del producto

**Codec-PMS Gavilán** es un Property Management System (PMS) orientado a la gestión de complejos rurales, con foco en la operativa interna y la optimización del tiempo de gestión.

Está diseñado para empresas, autónomos o particulares que gestionan alojamientos rurales como actividad secundaria, y necesitan:

- Reducir carga operativa  
- Automatizar procesos  
- Mantener calidad de servicio con bajo coste  

No es un “channel manager con web”, sino un **ERP ligero verticalizado para turismo rural**, donde el núcleo es la gestión interna.

---

## 2. Origen del proyecto

La solución surge tras la adquisición de un complejo rural por **Grupo Codec Technology**, con el objetivo de:

- Gestionar eficientemente el complejo  
- Minimizar el tiempo de operación  
- Automatizar procesos repetitivos  
- Reducir costes operativos y errores  

---

## 3. Problema que resuelve

Situación actual:

- Gestión manual o semi-manual (Excel, WhatsApp, llamadas)  
- Duplicidad de reservas entre canales  
- Cumplimiento legal manual (SES.MIR)  
- Falta de control económico real  
- Alta carga operativa diaria  

El sistema debe reducir:

- Tiempo de gestión  
- Errores humanos  
- Overbooking  
- Riesgos legales  

---

## 4. Usuarios y roles

### Roles internos

- **Admin (propietario)**  
  - Configuración global, informes, facturación  

- **Gestor de reservas**  
  - Alta/modificación de reservas  
  - Gestión del calendario  

- **Personal de limpieza/mantenimiento**  
  - Acceso a tareas y notas operativas  

- **Contabilidad (opcional)**  
  - Facturación, ingresos  

### Usuarios externos

- **Cliente**  
  - Registro  
  - Reserva  
  - Consulta  

---

## 5. Módulos funcionales

### 5.1. Módulo Web (cara pública)

- Página web corporativa  
- Catálogo de alojamientos (unidades)  
- Calendario de disponibilidad (lectura)  
- Formulario de contacto  
- Registro/login  
- Motor de reservas  

⚠️ Decisión clave:  
Motor propio vs integración con channel manager

---

### 5.2. Módulo PMS (core interno)

#### Reservas

- CRUD completo  
- Estados:
  - pendiente  
  - confirmada  
  - cancelada  
  - no-show  
- Notas internas por reserva  
- Historial  

#### Calendario

- Vista global por unidades  
- Drag & drop  
- Bloqueos manuales  

#### Clientes

- Ficha única  
- Histórico de reservas  
- Flags:
  - conflictivo (bloqueo)  
  - observaciones  

---

### 5.3. Integraciones externas

#### Channel Manager

- Booking  
- Airbnb  
- Escapada Rural  

Opciones técnicas:

1. APIs directas  
2. Intermediario (ej: AvaiBook)  
3. iCal  

---

#### Ministerio del Interior (SES.MIR)

- Envío automático de partes de viajeros  
- Gestión de errores  

Requisito legal crítico.

---

### 5.4. Facturación

- Generación automática desde reserva  
- Numeración legal  
- Exportación (PDF, contabilidad)  

---

### 5.5. Operativa interna

#### Limpieza

- Notas por reserva  
- Estado de unidad:
  - limpia  
  - pendiente  
  - en proceso  

#### Stock

- Inventario básico:
  - sábanas  
  - mantas  
  - limpieza  
- Movimientos simples  

---

### 5.6. Informes

- Ocupación (%)  
- Ingresos por unidad  
- Ingresos por canal  
- Rentabilidad  

---

### 5.7. Documentos

- Contrato de reserva (PDF imprimible)  
- Check-in digital  
- Posible firma (futuro)  

---

## 6. Funcionalidad clave: Check-in automático

### Descripción

Sistema de envío automático de comunicaciones para que el cliente complete el check-in antes de su llegada.

---

### Objetivos

- Reducir carga en recepción  
- Automatizar recogida de datos  
- Cumplir normativa (SES.MIR)  
- Mejorar experiencia del cliente  

---

### Flujo funcional

1. Reserva pasa a estado **confirmada**  
2. Se programa envío automático  
3. Cliente recibe comunicación  
4. Accede a enlace único seguro  
5. Completa:
   - Datos personales  
   - Acompañantes  
6. Información queda asociada a la reserva  
7. Opcional: envío a SES.MIR  

---

### Reglas de negocio

- Envío configurable (24–48h antes)  
- Reintentos automáticos  
- Enlace único con token  

Estados:

- Pendiente  
- Completado  
- Expirado  

---

### Consideraciones técnicas

- Asociación directa a reserva  
- Tokens únicos  
- Almacenamiento estructurado  
- Registro de timestamps  

---

### Consideraciones legales

- Cumplimiento GDPR  
- Integración con SES.MIR  
- Trazabilidad de datos  

---

## 7. Modelo conceptual

### Entidades

- Unidad (alojamiento)  
- Reserva  
- Cliente  
- Factura  
- Nota interna  
- Bloqueo  
- Canal  
- Inventario  

### Relaciones

- Reserva → Unidad (1:N)  
- Reserva → Cliente (N:1)  
- Reserva → Factura (1:1 o 1:N)  

---

## 8. Decisiones técnicas

- Drupal como:
  - backend (entidades, permisos)  
  - CMS público  

- Uso de BAT:
  - válido para calendario  
  - requiere adaptación  
  - no cubre PMS completo  

Riesgo: alta complejidad si no se acota

---

## 9. Roadmap

### Fase 1 (MVP)

- Unidades  
- Reservas internas  
- Calendario básico  
- Clientes  
- Notas internas  
- Bloqueos  
- Contrato PDF  

### Fase 2

- Web pública  
- Reservas online  
- iCal  
- Facturación básica  
- SES.MIR  

### Fase 3

- Integraciones API  
- Informes avanzados  
- Stock  

### Fase 4

- Actividades  
- Fichaje empleados  
- Optimización operativa  

---

## 10. Extensibilidad

Sistema modular para futuras ampliaciones:

- Fichaje de empleados  
- Actividades:
  - Paintball  
  - Canoas  
  - Bicicletas  
  - Otros servicios  

👉 Tratar actividades como “servicios asociados a reserva”

---

## 11. Riesgos

1. Integraciones externas (APIs, certificaciones)  
2. Sobrealcance (convertirse en ERP completo)  
3. UX interna deficiente  
4. Requisitos legales (facturación, SES.MIR)  

---

## 12. Principios del sistema

- Prioridad en operativa interna  
- Arquitectura modular y escalable  
- Integraciones abiertas  
- Optimizado para usuarios no técnicos  

---

## 13. Decisión estratégica pendiente

👉 ¿Producto interno o SaaS?

Impacta en:

- Arquitectura  
- Multi-tenant  
- Seguridad  
- Roadmap  
