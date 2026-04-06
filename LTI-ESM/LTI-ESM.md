# LTI — Diseño inicial del sistema de gestión de candidatos

## 1. Introducción

Este documento describe el diseño de la primera versión de **LTI**, una plataforma SaaS de gestión de candidatos (ATS). El objetivo es definir una base sólida que permita gestionar el proceso completo de selección, facilitando la colaboración entre equipos de contratación y mejorando la eficiencia operativa.

El diseño prioriza simplicidad, claridad y capacidad de evolución, permitiendo iterar rápidamente sobre el producto a medida que se valida su uso en entornos reales.

---

## 2. Descripción del producto

### 2.1 Visión

LTI es una plataforma diseñada para centralizar y optimizar el proceso de contratación, proporcionando visibilidad completa del pipeline de selección y facilitando la toma de decisiones basada en información estructurada.

### 2.2 Problema

En muchas organizaciones, el proceso de selección está fragmentado en múltiples herramientas (emails, hojas de cálculo, calendarios), lo que genera:

- pérdida de información relevante;
- falta de trazabilidad del candidato;
- descoordinación entre recruiters y managers;
- lentitud en la toma de decisiones;
- alta carga operativa manual.

### 2.3 Propuesta de valor

LTI transforma el proceso de selección en un flujo estructurado, colaborativo y medible, permitiendo:

- centralizar toda la información del candidato;
- mejorar la coordinación entre equipos;
- reducir tiempos de contratación;
- automatizar tareas repetitivas;
- mejorar la calidad de las decisiones.

### 2.4 Ventajas competitivas

- Colaboración en tiempo real entre stakeholders del proceso  
- Pipeline visual y trazable de candidatos  
- Automatización de tareas operativas  
- Integración de capacidades de IA para soporte en screening y evaluación  
- Experiencia de usuario simple y rápida de adoptar

---

## 3. Funcionalidades principales

### 3.1 Gestión de vacantes

- Creación, edición y publicación de vacantes  
- Definición de requisitos, descripción y responsables  
- Gestión del estado (borrador, abierta, cerrada)

### 3.2 Gestión de candidaturas

- Registro de candidatos  
- Asociación a vacantes  
- Almacenamiento de CV y datos relevantes  
- Seguimiento del estado dentro del proceso

### 3.3 Pipeline de selección

- Flujo por etapas configurable  
- Visualización del estado de cada candidato  
- Historial de cambios

### 3.4 Gestión de entrevistas

- Programación de entrevistas  
- Asignación de entrevistadores  
- Registro de resultados

### 3.5 Evaluación colaborativa

- Feedback estructurado  
- Valoraciones cuantitativas y cualitativas  
- Consolidación de decisiones

### 3.6 Automatización

- Notificaciones de eventos relevantes  
- Recordatorios de entrevistas  
- Alertas de candidatos pendientes  
- Seguimiento de estados

### 3.7 Asistencia inteligente

- Resumen automático de CV  
- Extracción de información clave  
- Soporte en generación de feedback  
- Ayuda en screening inicial

### 3.8 Reporting

- Métricas de proceso de selección  
- Tiempo medio de contratación  
- Conversión entre etapas  
- Rendimiento de vacantes

---

## 4. Modelo de negocio (Lean Canvas)


| Bloque             | Descripción                                             |
| ------------------ | ------------------------------------------------------- |
| Problema           | Procesos de selección desorganizados y manuales         |
| Clientes           | Startups, pymes y equipos de HR                         |
| Propuesta de valor | Plataforma colaborativa e inteligente para contratación |
| Solución           | Gestión de vacantes, pipeline, entrevistas y evaluación |
| Canales            | Venta B2B, demos, marketing digital                     |
| Ingresos           | Suscripción SaaS                                        |
| Costes             | Desarrollo, infraestructura, soporte                    |
| Métricas           | Time-to-hire, conversión por etapa                      |
| Ventaja            | Simplicidad + automatización + IA                       |


```mermaid
flowchart TB
    A[Problema]
    B[Clientes]
    C[Valor]
    D[Solución]
    E[Canales]
    F[Ingresos]
    G[Costes]
    H[Métricas]
    I[Ventaja]

    C --> A
    C --> B
    C --> D
    C --> E
    C --> F
    C --> G
    C --> H
    C --> I
```



---

## 5. Casos de uso principales

### 5.1 Crear y publicar vacante

Actor: Recruiter

Flujo:

Crear vacante
Definir datos
Asignar responsable
Publicar

```mermaid
flowchart LR
    A[Recruiter]

    subgraph UC1[Sistema LTI]
        U1((Crear vacante))
        U2((Definir datos))
        U3((Asignar responsable))
        U4((Publicar vacante))
    end

    A --> U1
    A --> U2
    A --> U3
    A --> U4

    U1 -. incluye .-> U2
    U1 -. incluye .-> U3
    U1 -. incluye .-> U4
```



### 5.2 Gestionar candidatura

Actor: Recruiter

Flujo:

Registrar candidatura
Revisar perfil
Avanzar o rechazar
Registrar histórico  

```mermaid
flowchart LR

    A[Recruiter]

    subgraph UC2[Sistema LTI]

        U1((Registrar candidatura))

        U2((Revisar perfil))

        U3((Avanzar candidatura))

        U4((Rechazar candidatura))

        U5((Registrar histórico))

    end

    A --> U1

    A --> U2

    A --> U3

    A --> U4

    A --> U5

    U1 -. incluye .-> U2

    U2 -. puede derivar en .-> U3

    U2 -. puede derivar en .-> U4

    U3 -. incluye .-> U5

    U4 -. incluye .-> U5

```



### 5.3 Entrevista y evaluación

Actores: Recruiter, Interviewer

Flujo:

Programar entrevista
Realizar entrevista
Registrar feedback
Decidir siguiente paso

```mermaid
flowchart LR
    A[Recruiter]
    B[Interviewer]

    subgraph UC3[Sistema LTI]
        U1((Programar entrevista))
        U2((Realizar entrevista))
        U3((Registrar feedback))
        U4((Decidir siguiente paso))
    end

    A --> U1
    A --> U4
    B --> U2
    B --> U3

    U1 -. incluye .-> U2
    U2 -. incluye .-> U3
    U3 -. incluye .-> U4
```



---

## 6. Modelo de datos

### Entidades principales

Company

- id: UUID
- name: String

User

- id: UUID
- company_id: UUID
- email: String
- role: Enum

JobOpening

- id: UUID
- title: String
- status: Enum
- hiring_manager_id: UUID

Candidate

- id: UUID
- name: String
- email: String

Application

- id: UUID
- candidate_id: UUID
- job_id: UUID
- stage: Enum

Interview

- id: UUID
- application_id: UUID
- scheduled_at: DateTime

Evaluation

- id: UUID
- score: Integer
- comments: Text

```mermaid
 erDiagram
    COMPANY {
        UUID id PK
        VARCHAR name
        VARCHAR domain
        VARCHAR plan
        TIMESTAMP created_at
    }

    USER {
        UUID id PK
        UUID company_id FK
        VARCHAR full_name
        VARCHAR email
        VARCHAR password_hash
        ENUM role
        ENUM status
        TIMESTAMP created_at
    }

    JOB_OPENING {
        UUID id PK
        UUID company_id FK
        VARCHAR title
        TEXT description
        VARCHAR location
        ENUM work_mode
        ENUM employment_type
        DECIMAL salary_min
        DECIMAL salary_max
        ENUM status
        UUID hiring_manager_id FK
        UUID created_by FK
        TIMESTAMP created_at
        TIMESTAMP published_at
    }

    CANDIDATE {
        UUID id PK
        VARCHAR first_name
        VARCHAR last_name
        VARCHAR email
        VARCHAR phone
        VARCHAR linkedin_url
        VARCHAR resume_url
        VARCHAR location
        INTEGER years_experience
        TIMESTAMP created_at
    }

    APPLICATION {
        UUID id PK
        UUID candidate_id FK
        UUID job_opening_id FK
        ENUM source
        ENUM current_stage
        ENUM status
        TEXT ai_summary
        UUID recruiter_owner_id FK
        TIMESTAMP applied_at
        TIMESTAMP updated_at
    }

    INTERVIEW {
        UUID id PK
        UUID application_id FK
        ENUM type
        TIMESTAMP scheduled_at
        INTEGER duration_minutes
        VARCHAR meeting_url
        ENUM status
        UUID created_by FK
    }

    INTERVIEW_PARTICIPANT {
        UUID id PK
        UUID interview_id FK
        UUID user_id FK
        ENUM participation_role
    }

    EVALUATION {
        UUID id PK
        UUID application_id FK
        UUID interview_id FK
        UUID evaluator_user_id FK
        INTEGER score
        ENUM recommendation
        TEXT comments
        TIMESTAMP created_at
    }

    STAGE_HISTORY {
        UUID id PK
        UUID application_id FK
        VARCHAR from_stage
        VARCHAR to_stage
        UUID changed_by_user_id FK
        TEXT reason
        TIMESTAMP changed_at
    }

    NOTIFICATION {
        UUID id PK
        UUID user_id FK
        ENUM type
        VARCHAR title
        TEXT body
        TIMESTAMP read_at
        TIMESTAMP created_at
    }

    COMPANY ||--o{ USER : has
    COMPANY ||--o{ JOB_OPENING : owns
    USER ||--o{ JOB_OPENING : creates
    USER ||--o{ JOB_OPENING : manages
    CANDIDATE ||--o{ APPLICATION : submits
    JOB_OPENING ||--o{ APPLICATION : receives
    USER ||--o{ APPLICATION : owns
    APPLICATION ||--o{ INTERVIEW : includes
    INTERVIEW ||--o{ INTERVIEW_PARTICIPANT : has
    USER ||--o{ INTERVIEW_PARTICIPANT : participates
    APPLICATION ||--o{ EVALUATION : gets
    INTERVIEW ||--o{ EVALUATION : generates
    USER ||--o{ EVALUATION : writes
    APPLICATION ||--o{ STAGE_HISTORY : tracks
    USER ||--o{ STAGE_HISTORY : performs
    USER ||--o{ NOTIFICATION : receives
```



---

## 7. Diseño del sistema a alto nivel

### 7.1 Enfoque arquitectónico

El sistema se diseña como un **monolito modular con separación clara entre frontend y backend**, desplegado como una aplicación web SaaS.

Este enfoque permite:

- reducir la complejidad inicial del sistema;
- acelerar el desarrollo y la iteración;
- mantener una base coherente del dominio;
- facilitar una futura evolución hacia arquitecturas distribuidas si el producto lo requiere.

El sistema se estructura siguiendo principios de **separación de responsabilidades**, organizando el backend en módulos de dominio independientes.

---

### 7.2 Componentes del sistema

#### Frontend

Aplicación web que permite a los usuarios interactuar con el sistema:

- gestión de vacantes;
- visualización del pipeline;
- evaluación de candidatos;
- gestión de entrevistas.

Se comunica exclusivamente con el backend mediante API.

---

#### Backend API

Encapsula toda la lógica de negocio del sistema y expone endpoints para el frontend.

Se organiza en los siguientes módulos:

- **Auth & Users**: gestión de usuarios, autenticación y roles  
- **Job Openings**: gestión de vacantes  
- **Candidates & Applications**: gestión de candidatos y pipeline  
- **Interviews & Evaluations**: entrevistas y feedback  
- **Notifications**: gestión de eventos y avisos  
- **Automation Engine**: ejecución de reglas automáticas  
- **AI Assistant Adapter**: integración con servicios de IA  
- **Reporting**: generación de métricas y análisis

---

#### Base de datos

Sistema de persistencia relacional encargado de almacenar:

- entidades principales del dominio;
- relaciones entre datos;
- histórico del proceso de selección.

---

#### Almacenamiento de documentos

Sistema externo para almacenar archivos como CVs y documentos adjuntos.

---

#### Servicio de notificaciones

Encargado de enviar comunicaciones:

- emails;
- notificaciones internas.

---

#### Servicio de IA

Componente externo o desacoplado que permite:

- análisis de CVs;
- generación de resúmenes;
- asistencia en evaluación.

---

### 7.3 Comunicación entre componentes

- El **frontend** interactúa con el sistema a través del **backend API**.
- El **backend** gestiona la lógica de negocio y accede a la base de datos.
- Los módulos internos del backend se comunican entre sí mediante llamadas internas.
- El backend se integra con:
  - almacenamiento de documentos;
  - servicio de notificaciones;
  - proveedor de IA.

---

### 7.4 Diagrama de arquitectura

```mermaid
flowchart TB
    Users[Usuarios] --> FE[Frontend Web]

    FE --> API[Backend API]

    subgraph Backend
        API --> M1[Auth & Users]
        API --> M2[Job Openings]
        API --> M3[Candidates & Applications]
        API --> M4[Interviews & Evaluations]
        API --> M5[Automation Engine]
        API --> M6[AI Assistant Adapter]
        API --> M7[Notifications]
        API --> M8[Reporting]
    end

    M1 --> DB[(Database)]
    M2 --> DB
    M3 --> DB
    M4 --> DB
    M8 --> DB

    M3 --> FS[(Document Storage)]
    M7 --> MAIL[Email Service]
    M6 --> AI[AI Service]
```



---

## 8. Diagrama C4

Para describir la arquitectura con mayor nivel de detalle, se utiliza el modelo C4, profundizando en el componente de **gestión de candidaturas (Applications)**, que constituye el núcleo funcional del sistema.

---

### 8.1 Nivel 1 — Contexto

Representa el sistema en relación con usuarios y servicios externos.
```mermaid
flowchart LR
    Candidate[Candidate]
    Recruiter[Recruiter]
    Manager[Hiring Manager]
    Interviewer[Interviewer]

    System[LTI ATS]

    Email[Email Service]
    AI[AI Service]

    Candidate --> System
    Recruiter --> System
    Manager --> System
    Interviewer --> System

    System --> Email
    System --> AI
```

### 8.2 Nivel 2 — Contenedores

Describe las principales piezas desplegables del sistema.
```mermaid
flowchart LR
    Users[Usuarios]
    Web[Frontend Web]
    API[Backend API]
    DB[(Database)]
    Storage[(Document Storage)]
    Email[Email Service]
    AI[AI Service]

    Users --> Web
    Web --> API
    API --> DB
    API --> Storage
    API --> Email
    API --> AI
```

---

### 8.3 Nivel 3 — Componentes (Applications)

Se detalla el módulo encargado de la gestión de candidaturas

```mermaid
flowchart TB
    Controller[Applications Controller]

    ApplicationService[Application Service]
    CandidateService[Candidate Service]
    PipelineService[Pipeline Service]
    ScreeningService[AI Screening Service]
    HistoryService[Stage History Service]
    NotificationService[Notification Service]

    ApplicationRepository[(Application Repository)]
    CandidateRepository[(Candidate Repository)]
    HistoryRepository[(Stage History Repository)]

    Controller --> ApplicationService
    Controller --> CandidateService
    Controller --> PipelineService

    ApplicationService --> ApplicationRepository
    ApplicationService --> ScreeningService
    ApplicationService --> NotificationService

    CandidateService --> CandidateRepository

    PipelineService --> HistoryService
    PipelineService --> ApplicationRepository

    ScreeningService --> AI[AI Service]
    HistoryService --> HistoryRepository
    NotificationService --> Email[Email Service]
```


### 8.4 Justificación del componente seleccionado

El módulo de **candidaturas (Applications)** se considera el núcleo del sistema, ya que:

- conecta candidatos con vacantes;
- gestiona el estado del pipeline;
- almacena el histórico de decisiones;
- activa automatizaciones;
- integra capacidades de inteligencia artificial.

Este componente concentra la mayor parte del valor del sistema y actúa como punto central de coordinación entre el resto de módulos..