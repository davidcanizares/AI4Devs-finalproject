# User Stories — Fase Inicial (MVP) — Codec-PMS Gavilán

---

## US-01 — Gestión de unidades (alojamientos)

**Historia**  
Como administrador, quiero crear y gestionar unidades de alojamiento, para poder definir qué se puede reservar.

**Criterios de aceptación (BDD)**  
- Dado que accedo al panel de administración, cuando creo una unidad con datos válidos, entonces se guarda correctamente  
- Dado que existe una unidad, cuando la edito, entonces los cambios se actualizan  
- Dado que existe una unidad, cuando la desactivo, entonces no aparece disponible para reservas  

**Estimación**: M  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí (campos ampliables)  
- Valuable: Alta  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-02 — Creación de reservas internas

**Historia**  
Como gestor de reservas, quiero crear reservas manualmente, para gestionar clientes sin uso de la web.

**Criterios de aceptación**  
- Dado un calendario, cuando selecciono fechas libres, entonces puedo crear una reserva  
- Dado una reserva creada, cuando la guardo, entonces queda asociada a una unidad  
- Dado una reserva existente, cuando hay conflicto de fechas, entonces el sistema lo impide  

**Estimación**: L  

**INVEST**  
- Independent: Parcial (depende de unidades)  
- Negotiable: Sí  
- Valuable: Crítica  
- Estimable: Sí  
- Small: No (pero asumible MVP)  
- Testable: Sí  

---

## US-03 — Visualización de calendario

**Historia**  
Como gestor, quiero ver un calendario de disponibilidad, para gestionar reservas eficientemente.

**Criterios de aceptación**  
- Dado el calendario, cuando accedo, entonces veo todas las unidades  
- Dado reservas existentes, cuando visualizo calendario, entonces aparecen reflejadas  
- Dado una fecha ocupada, cuando intento reservar, entonces se indica como no disponible  

**Estimación**: M  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí (vista simplificada inicial)  
- Valuable: Alta  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-04 — Gestión de clientes

**Historia**  
Como gestor, quiero registrar clientes, para asociarlos a reservas.

**Criterios de aceptación**  
- Dado el formulario, cuando introduzco datos válidos, entonces se guarda el cliente  
- Dado un cliente existente, cuando lo selecciono, entonces puedo asociarlo a una reserva  
- Dado un cliente, cuando accedo a su ficha, entonces veo su información básica  

**Estimación**: M  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí  
- Valuable: Alta  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-05 — Notas internas en reservas

**Historia**  
Como gestor, quiero añadir notas a reservas, para facilitar la operativa interna.

**Criterios de aceptación**  
- Dado una reserva, cuando añado una nota, entonces se guarda correctamente  
- Dado una reserva con notas, cuando accedo, entonces puedo visualizarlas  
- Dado múltiples notas, cuando se listan, entonces aparecen ordenadas  

**Estimación**: S  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí  
- Valuable: Media  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-06 — Bloqueo de fechas

**Historia**  
Como gestor, quiero bloquear fechas en el calendario, para evitar reservas en periodos no disponibles.

**Criterios de aceptación**  
- Dado una unidad, cuando selecciono fechas, entonces puedo bloquearlas  
- Dado fechas bloqueadas, cuando intento reservar, entonces no es posible  
- Dado un bloqueo, cuando lo elimino, entonces la fecha vuelve a estar disponible  

**Estimación**: M  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí  
- Valuable: Alta  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-07 — Generación de contrato en PDF

**Historia**  
Como gestor, quiero generar un contrato en PDF, para formalizar la reserva.

**Criterios de aceptación**  
- Dado una reserva, cuando solicito contrato, entonces se genera PDF  
- Dado el PDF, cuando lo descargo, entonces contiene los datos correctos  
- Dado una reserva modificada, cuando regenero el contrato, entonces se actualiza  

**Estimación**: M  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí  
- Valuable: Alta  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-08 — Registro de usuarios (cliente)

**Historia**  
Como cliente, quiero registrarme, para poder realizar reservas.

**Criterios de aceptación**  
- Dado el formulario, cuando introduzco datos válidos, entonces se crea la cuenta  
- Dado un email existente, cuando intento registrarme, entonces se muestra error  
- Dado un usuario registrado, cuando inicia sesión, entonces accede  

**Estimación**: M  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí  
- Valuable: Media  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

## US-09 — Envío automático de check-in

**Historia**  
Como sistema, quiero enviar automáticamente el check-in, para recoger datos antes de la llegada.

**Criterios de aceptación**  
- Dado una reserva confirmada, cuando se acerca la fecha, entonces se envía email  
- Dado el enlace, cuando el cliente accede, entonces puede completar datos  
- Dado datos completados, cuando se guardan, entonces quedan asociados a la reserva  

**Estimación**: L  

**INVEST**  
- Independent: No (depende de reservas)  
- Negotiable: Sí  
- Valuable: Muy alta  
- Estimable: Sí  
- Small: No  
- Testable: Sí  

---

## US-10 — Marcado de clientes conflictivos

**Historia**  
Como gestor, quiero marcar clientes conflictivos, para evitar futuras reservas.

**Criterios de aceptación**  
- Dado un cliente, cuando lo marco como conflictivo, entonces queda registrado  
- Dado un cliente conflictivo, cuando intento reservar, entonces se bloquea  
- Dado un cliente desbloqueado, cuando se actualiza, entonces puede reservar  

**Estimación**: S  

**INVEST**  
- Independent: Sí  
- Negotiable: Sí  
- Valuable: Media  
- Estimable: Sí  
- Small: Sí  
- Testable: Sí  

---

# Priorización MVP

## Orden propuesto

1. US-01 — Gestión de unidades  
2. US-04 — Gestión de clientes  
3. US-02 — Creación de reservas internas  
4. US-03 — Calendario  
5. US-06 — Bloqueo de fechas  
6. US-05 — Notas internas  
7. US-07 — Contrato PDF  
8. US-10 — Clientes conflictivos  
9. US-09 — Check-in automático  
10. US-08 — Registro usuarios  

---

## Justificación

### 1. Núcleo operativo primero
Sin:
- unidades  
- reservas  
- clientes  

👉 el sistema no existe

---

### 2. Control de disponibilidad
Calendario + bloqueos evitan:
- overbooking
- errores críticos

---

### 3. Operativa interna
Notas + contratos:
- aportan valor inmediato al negocio

---

### 4. Automatización (fase posterior)
Check-in:
- alto valor
- pero no bloqueante para operar

---

### 5. Frontend cliente al final
Registro:
- no necesario en MVP interno
- se puede operar manualmente

---

## Conclusión

El MVP está correctamente orientado a:

- **operativa interna primero**
- **automatización después**
- **canal cliente en última fase**

Esto reduce riesgo y acelera validación real del producto.
