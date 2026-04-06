## TL;DR

LTI es una plataforma SaaS de gestión de candidatos (ATS) diseñada para startups que necesitan contratar de forma rápida sin contar con procesos de recruiting estructurados.

El producto elimina dos cuellos de botella críticos del proceso de selección: el análisis manual de candidatos y la generación de feedback tras entrevistas. A través de asistencia inteligente y automatización, LTI reduce significativamente el tiempo operativo y mejora la calidad de las decisiones.

El objetivo es reducir el time-to-hire en un 30–50% y permitir a equipos pequeños operar procesos de contratación eficientes sin necesidad de experiencia previa en recruiting.

---

## 1. Problema

Las startups necesitan contratar rápido, pero no cuentan con procesos definidos ni recursos dedicados al recruiting.

### Principales problemas:

- Evaluación manual de CVs (5–10 minutos por candidato)
- Alto volumen de candidatos sin priorización clara
- Feedback de entrevistas inexistente o inconsistente
- Información fragmentada entre herramientas (email, Slack, hojas de cálculo)
- Decisiones lentas o basadas en información incompleta

### Impacto:

- Time-to-hire promedio en startups: 40–60 días
- Retrasos en contratación impactan directamente en productividad (~$500–$1,500/día por vacante abierta)
- Bajo ratio de feedback (<50% en 24h), bloqueando decisiones

---

## 2. Objetivos

### 2.1 Business Goals

- Reducir time-to-hire en un 30–50%
- Aumentar activación y uso recurrente del producto
- Posicionar LTI como ATS “AI-first” con impacto operativo real

---

### 2.2 User Goals

**Hiring Manager**

- Evaluar candidatos rápidamente
- Reducir tiempo dedicado a tareas manuales
- Tomar decisiones con información clara

**Interviewer**

- Dar feedback sin fricción
- Minimizar esfuerzo y tiempo invertido

---

### 2.3 Non-Goals

- Reporting avanzado en V1
- Configuración compleja de workflows
- Integraciones extensivas
- Casos enterprise

---

## 3. Usuario objetivo

### Primary Persona — Hiring Manager en startup

- Responsable de contratación sin ser experto en recruiting
- Tiempo limitado
- Necesidad de tomar decisiones rápidas

**Pain points:**

- No quiere leer decenas de CVs
- No recibe feedback consistente
- No tiene visibilidad clara del proceso

**Job to be done:**

“Evaluar candidatos y tomar decisiones rápidamente sin gestionar un proceso complejo”

---

## 4. Propuesta de valor

LTI permite a startups contratar de forma eficiente sin necesidad de diseñar procesos complejos.

El sistema automatiza tareas repetitivas y guía a los usuarios en los momentos clave del proceso, proporcionando información estructurada y recomendaciones accionables que facilitan la toma de decisiones.

---

## 5. Decisiones de producto

- Pipeline con etapas predefinidas (no configurable en V1)
- Interfaz simplificada orientada a velocidad
- IA como sistema de apoyo a decisiones, no solo asistente
- Minimización de input manual

---

## 6. Funcionalidades principales (MVP)

### Incluido

- Creación de vacantes
- Gestión de candidatos
- Pipeline simple (movimiento entre etapas)
- Screening asistido por IA
- Feedback asistido

### Excluido

- Reporting avanzado
- Automatizaciones complejas
- Integraciones externas extensivas
- Funcionalidades enterprise

---

## 7. Experiencia de usuario

### 7.1 Creación de vacante

El usuario introduce información básica (título, descripción breve).

El sistema sugiere contenido adicional automáticamente.

Tiempo objetivo: <2 minutos

---

### 7.2 Screening de candidatos

Vista tipo lista donde cada candidato incluye:

- Resumen estructurado
- Experiencia relevante
- Señales clave
- Recomendación de acción

El usuario puede tomar decisiones sin abrir el CV completo.

Tiempo objetivo: <30 segundos por candidato

---

### 7.3 Evaluación y feedback

Tras una entrevista:

- El sistema presenta contexto del candidato
- Genera un borrador de feedback estructurado
- El usuario edita y envía

Tiempo objetivo: <2 minutos

---

### 7.4 Pipeline

Pipeline con etapas estándar:

- Applied
- Screening
- Interview
- Decision

Movimiento simple entre etapas con visibilidad completa del estado.

---

### 7.5 Automatización

- Recordatorios de feedback
- Alertas de candidatos sin actividad
- Restricción de avance sin evaluación

---

## 8. Narrative

Los procesos de contratación en startups suelen ser lentos y desorganizados debido a la falta de estructura y recursos.

Los equipos invierten tiempo significativo en tareas manuales como revisar CVs y recopilar feedback, lo que ralentiza las decisiones y reduce la calidad de las contrataciones.

LTI introduce un sistema estructurado que automatiza estas tareas y proporciona información clara en cada etapa del proceso.

Desde el screening inicial hasta la decisión final, el sistema reduce la carga operativa y mejora la consistencia, permitiendo a los equipos contratar de forma más rápida y fiable.

---

## 9. Success Metrics

### Core

- Tiempo medio de screening por candidato (<1 minuto)
- % candidatos evaluados con asistencia IA
- % entrevistas con feedback completo (>80%)
- Tiempo entrevista → feedback (<24h)

---

### Impacto

- Reducción de time-to-hire
- Conversión entre etapas
- Engagement de usuarios

---

## 10. Consideraciones técnicas

### IA

- Generación de resúmenes de CV
- Generación de feedback
- Necesidad de explicabilidad en outputs

---

### Backend

- Extensión del modelo de datos (AI summary, feedback generado)
- Procesamiento asíncrono de CVs

---

### Riesgos técnicos

- Calidad inconsistente de outputs IA
- Coste por uso
- Latencia

---

## 11. Riesgos

### Producto

- Baja confianza en IA
- Resistencia al cambio

---

### UX

- Sobrecarga de información
- Falta de claridad en recomendaciones

---

### Negocio

- Diferenciación insuficiente si no se ejecuta correctamente

---

## 12. Milestones & Sequencing

### Fase 1

- Core ATS (vacantes, candidatos, pipeline)

---

### Fase 2

- AI screening

---

### Fase 3

- Feedback asistido

---

### Fase 4

- Automatización