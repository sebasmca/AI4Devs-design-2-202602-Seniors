# LTI-ESM - Prompt Log 

## Module 5 - Part 2

The prompts below were used on ChatPRD for this exercise.

### PRD Generation

```md
# ROLE
Actúa como un Senior Product Manager con experiencia en productos SaaS B2B.

# OBJECTIVE
A partir del siguiente design document, genera un Product Requirements Document (PRD) estructurado y listo para ser utilizado por un equipo de producto y desarrollo.

# REQUIREMENTS
Incluir un resumen ejecutivo claro y orientado a impacto
Definir el problema de forma concreta, incluyendo contexto y consecuencias
Identificar claramente el usuario objetivo y sus principales necesidades
Establecer objetivos de negocio y de usuario
Incluir propuesta de valor diferenciada
Describir la experiencia de usuario de forma detallada (flujos clave)
Definir funcionalidades principales priorizadas (enfocadas a MVP)
Incluir métricas de éxito claras y medibles
Identificar riesgos y consideraciones técnicas relevantes
Proponer un plan de milestones y secuenciación

# INSTRUCTIONS
Prioriza claridad y foco sobre exhaustividad
Evita scope innecesario o funcionalidades no críticas
Asegura coherencia entre problema, solución y métricas
Escribe en tono profesional, como documento dirigido a stakeholders
```

> Adicionalmente le adjunte mi documento de diseño inicial de la parte 1 del ejercicio [LTI-ESM.md]


### User Stories Generation

```md
# ROLE
Actúa como un Product Owner senior con experiencia en productos SaaS.

# OBJECTIVE
A partir del siguiente Product Requirements Document (PRD), genera un conjunto de User Stories para un MVP funcional.

# REQUIREMENTS
- Organiza las historias en épicas (máximo 3–5)
- Cada historia debe incluir:
  - ID
  - Título
  - "Como [rol], quiero [acción], para [beneficio]"
  - 3 criterios Given/When/Then
  - Dependencias si existen

- Las historias deben ser:
  - Atómicas
  - Implementables en 1–2 días
  - Coherentes con el flujo del producto

- Prioriza primero la base funcional antes de añadir IA
```

> Adicionalmente le adjunte mi documento PRD que obtuve como output y refiné en el paso previo [PRD.md]

### Backlog Generation

PROMPT 1 (Básico)

```md
A partir de las siguientes user stories, ordénalas por prioridad para un MVP.

Justifica brevemente el orden.
```

> Resultado observado:
>  - Priorización poco clara
>  - Sin criterio definido
>  - Justificaciones superficiales


PROMPT 2 (Usando MoSCoW)
```md
# ROLE
Actúa como un Product Owner senior.

# OBJECTIVE
A partir de las siguientes user stories, genera un Product Backlog priorizado usando la metodología MoSCoW.

# REQUIREMENTS
Para cada historia incluye:
- Prioridad (Must / Should / Could)
- Justificación basada en valor y dependencias

# OUTPUT
1. Backlog por épicas
2. Backlog global priorizado
3. Explicación de la lógica de priorización
```

> Resultado observado:
>  - Priorización clara y estructurada
>  - Uso de criterio explícito (MoSCoW)
>  - Mejor justificación de decisiones
>  - Backlog más profesional



PROMPT 3 (Usando User Story Mapping)
```md
# ROLE
Actúa como un Product Owner senior.

# OBJECTIVE
A partir de las siguientes user stories, genera un Product Backlog priorizado usando la técnica User Story Mapping

# REQUIREMENTS
- Para el User Story Mapping no traces ninguna subdivisión horizontal, ya que todas las stories ya forman parte del MVP

# OUTPUT
1. Backlog por épicas
2. Backlog global priorizado y gráfico en Mermaid
3. Explicación de la lógica de priorización
```

> Resultado observado:
>  - Priorización clara y estructurada
>  - Uso de técnica explícita (User Story Mapping)
>  - Mejor justificación de decisiones
>  - Backlog más profesional
>  - Incluye un diagrama en mermaid, lo que lo hace más visual


> CONCLUSIÓN:
> En miopinión el prompt #2 arrojó los mejores resultados en el sentido de que fueron más prácticos y concisos, la estructura de Must, Should y Could tenía más sentido para mi en un contexto tan cambiante como puede ser el de un MVP y estaba realmente claro lo que era crítico para el MPV. 
> El prompt #3 está bien porque obliga a profundizar más en las tareas que irá realizando el usuario. Si bien inicialment eno lo consideré y tuve que iterar el diagrama. También tuve problemas para que el diagrama en mermaid tomase forma real de User Story Mapping, acabé teniendo que adaptarlo a mano. Lo consideraría como una buena opción para una fase posterior al MVP.


### Tickets Generation

```md
# ROLE
Actúa como un Product Owner senior trabajando con un equipo de desarrollo en una reunión de planificación (sprint planning).

# OBJECTIVE
A partir de las siguientes User Stories, desglosa cada una en tickets técnicos listos para desarrollo, simulando el nivel de detalle real de una planificación.

# REQUIREMENTS

## 1. Alcance
- Trabaja sobre las 3 primeras User Stories
- Genera tickets que cubran el flujo completo de la funcionalidad
- Incluye frontend, backend y validaciones cuando aplique

## 2. Para cada User Story incluye:
- ID y título de la User Story
- Breve contexto funcional

## 3. Para cada ticket incluye:
- ID del ticket
- Título claro y accionable
- Tipo (Frontend / Backend / Fullstack)
- Descripción técnica concreta (qué hay que construir)
- Criterios de aceptación (Given / When / Then)
- Dependencias (si existen)

## 4. Nivel de detalle
- Los tickets deben ser implementables en 1 día aprox.
- Evita descripciones genéricas
- Incluye detalles técnicos (ej: endpoints, validaciones, estados UI, estructura de datos si aplica)

## 5. Organización
- Agrupa los tickets bajo cada User Story
- Ordena los tickets en el orden en que se desarrollarían

## 6. Enfoque
- Prioriza claridad técnica sobre explicación teórica
- Simula una conversación real de planning (qué hay que hacer, no por qué)

# OUTPUT
Devuelve el resultado estructurado así:

1. User Story 1
   - Contexto
   - Lista de tickets

2. User Story 2
   - Contexto
   - Lista de tickets

3. User Story 3
   - Contexto
   - Lista de tickets

# ADDITIONAL INSTRUCTIONS
- No inventes funcionalidades fuera del PRD
- Mantén consistencia con el modelo de datos definido
- Asegura que los tickets cubren completamente la implementación de la historia
```

### Estimations

```md
# ROLE
Actúa como un Product Owner senior facilitando una sesión de estimación con un equipo de desarrollo (backend + frontend).

# OBJECTIVE
A partir de los siguientes tickets técnicos, estima el esfuerzo de cada uno utilizando Story Points.

# REQUIREMENTS

## 1. Estimación
- Asigna Story Points usando la escala Fibonacci: 1, 2, 3, 5, 8
- La estimación debe reflejar:
  - Complejidad técnica
  - Esfuerzo de implementación
  - Riesgo / incertidumbre

## 2. Para cada ticket incluye:
- ID del ticket
- Título
- Tipo (Frontend / Backend / Fullstack)
- Estimación en Story Points
- Justificación breve (1–2 líneas máximo)

## 3. Criterios de estimación
Ten en cuenta:
- Integraciones (API, servicios externos)
- Validaciones y edge cases
- Complejidad de UI (formularios, estados, navegación)
- Dependencias con otros tickets
- Posibles riesgos técnicos

## 4. Output adicional
- Identifica:
  - Ticket más complejo
  - Ticket más incierto
- Calcula:
  - Total de Story Points del conjunto

## 5. Formato de salida

Devuelve:

1. Tabla de estimación:
   - ID | Título | Tipo | Story Points | Justificación

2. Resumen:
   - Total Story Points
   - Ticket más complejo
   - Ticket con mayor incertidumbre

# ADDITIONAL INSTRUCTIONS
- No sobreestimes tickets simples (ej: CRUD básico no puede valer 5 puntos)
- Evita justificar con frases genéricas
- Sé consistente entre tickets similares
- Piensa como si el equipo tuviera experiencia media
```
> La estimación se realizó utilizando Story Points basados en la secuencia Fibonacci, considerando complejidad técnica, dependencias y riesgo, simulando una dinámica real de equipo