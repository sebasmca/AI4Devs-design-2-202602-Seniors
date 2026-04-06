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
>
> - Priorización poco clara
> - Sin criterio definido
> - Justificaciones superficiales

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
>
> - Priorización clara y estructurada
> - Uso de criterio explícito (MoSCoW)
> - Mejor justificación de decisiones
> - Backlog más profesional

PROMPT 3 (Usando User Story Mapping)

```md
# ROLE 
Actúa como un Product Owner senior con experiencia en definición de producto mediante User Story Mapping. 

# OBJECTIVE 
A partir de las siguientes user stories, genera un Product Backlog priorizado utilizando la técnica de User Story Mapping. 

# REQUIREMENTS 

## 1. User Story Mapping 
- Organiza las historias siguiendo un flujo de usuario de izquierda a derecha (actividades principales) 
- Agrupa las historias en bloques funcionales que representen pasos del journey del usuario 
- No incluyas subdivisión horizontal (todas las historias pertenecen al MVP) 

## 2. Estructura 
- Define primero las actividades principales (ej: gestionar vacantes, gestionar candidatos, evaluar candidatos) 
- Bajo cada actividad, agrupa las user stories correspondientes en orden lógico 

## 3. Priorización 
- Ordena las historias dentro de cada actividad en orden de ejecución real 
- Justifica brevemente el orden basado en dependencias y valor para el usuario 

## 4. Representación visual 
- Genera un diagrama en Mermaid que represente el User Story Mapping: 
- Flujo horizontal = actividades - Bajo cada actividad = user stories asociadas 

## 5. Formato de salida 
Devuelve el resultado en este orden: 
1. Actividades principales del usuario 
2. User Story Mapping (estructura textual) 
3. Diagrama Mermaid del mapping 
4. Backlog global priorizado 
5. Explicación de la lógica de priorización 

# ADDITIONAL INSTRUCTIONS 
- Mantén foco en el flujo real del usuario definido en el PRD 
- No inventes funcionalidades fuera del scope - Prioriza claridad visual y lógica de producto 
- Asegúrate de que el mapping refleje cómo se usaría realmente el sistema
```

