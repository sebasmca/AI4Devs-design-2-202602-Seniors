# 1. Lista de épicas

EPIC-01 — Job Openings Management
EPIC-02 — Candidate Management & Pipeline
EPIC-03 — AI-Assisted Screening
EPIC-04 — Interview Feedback & Assisted Evaluation

# 2. User stories por épica

## EPIC-01 — Job Openings Management

### US-01 — Create a job opening

User Story
Como Hiring Manager, quiero crear una vacante, para iniciar un proceso de selección.

Acceptance Criteria

Given I am on the job creation page, when I enter a title and description and submit the form, then the system creates a new job opening in active status.
Given I leave the title empty, when I submit the form, then the system shows a validation error and does not create the job opening.
Given a job opening is successfully created, when I navigate to the jobs list, then the new job opening appears in the list.

Dependencias
Ninguna.

Notas o supuestos
Se asume autenticación previa.

### US-02 — View job openings list

User Story
Como Hiring Manager, quiero ver el listado de vacantes, para acceder rápidamente a cada proceso de selección.

Acceptance Criteria

Given job openings exist, when I access the jobs page, then the system displays all job openings with title and status.
Given no job openings exist, when I access the jobs page, then the system shows an empty state.
Given I select a job opening from the list, when I click on it, then the system opens the corresponding job detail page.

Dependencias
US-01

Notas o supuestos
Ninguna.

### US-03 — View job opening details

User Story
Como Hiring Manager, quiero ver el detalle de una vacante, para consultar su información y gestionar candidatos.

Acceptance Criteria

Given a job opening exists, when I open its detail page, then the system shows its title, description, and status.
Given the job opening has candidates, when I view the detail page, then I can access the associated candidate list or pipeline.
Given the job opening does not exist, when I try to access it, then the system shows an error or not found state.

Dependencias
US-01, US-02

Notas o supuestos
Ninguna.

## EPIC-02 — Candidate Management & Pipeline

### US-04 — Create a candidate manually

User Story
Como Hiring Manager, quiero registrar un candidato manualmente, para evaluarlo dentro de una vacante.

Acceptance Criteria

Given I am on a job opening detail page, when I enter a candidate name and email and save, then the system creates the candidate and links it to that job opening.
Given I leave the email empty, when I submit the candidate form, then the system shows a validation error and does not create the candidate.
Given the candidate is created successfully, when the save process finishes, then the candidate appears in the job opening candidate list.

Dependencias
US-03

Notas o supuestos
La creación es manual en MVP.

### US-05 — Upload candidate CV

User Story
Como Hiring Manager, quiero subir el CV de un candidato, para disponer de su información durante la evaluación.

Acceptance Criteria

Given I am editing a candidate profile, when I upload a valid PDF or DOCX file, then the system attaches the CV to the candidate profile.
Given I upload an unsupported file format, when I confirm the upload, then the system rejects the file and shows an error.
Given the CV upload succeeds, when I open the candidate profile, then the CV is available for viewing or download.

Dependencias
US-04

Notas o supuestos
Solo PDF y DOCX en MVP.

US-06 — Create application with initial stage

User Story
Como sistema, quiero asignar automáticamente una etapa inicial cuando un candidato se añade a una vacante, para reflejar su entrada en el proceso.

Acceptance Criteria

Given a candidate is added to a job opening, when the creation process completes, then the system creates an application in the “Applied” stage.
Given the application exists, when I view the candidate or pipeline, then the current stage is shown as “Applied”.
Given application creation fails, when the candidate creation process ends, then the system prevents an inconsistent state and shows an error.

Dependencias
US-04

Notas o supuestos
Etapa inicial fija en MVP.

### US-07 — View candidates list for a job opening

User Story
Como Hiring Manager, quiero ver los candidatos asociados a una vacante, para revisar rápidamente quién está en proceso.

Acceptance Criteria

Given a job opening has candidates, when I access its candidates section, then the system displays the associated candidate list.
Given a job opening has no candidates, when I access its candidates section, then the system shows an empty state.
Given I select a candidate from the list, when I click on the candidate, then the system opens the candidate profile.

Dependencias
US-04, US-06

Notas o supuestos
Ninguna.

### US-08 — View candidate profile

User Story
Como Hiring Manager, quiero ver el perfil de un candidato, para revisar su información antes de decidir el siguiente paso.

Acceptance Criteria

Given a candidate exists, when I open the candidate profile, then the system shows name, email, CV, and current stage.
Given the candidate has a CV attached, when I open the profile, then the CV is accessible from the profile.
Given the candidate does not exist, when I try to access the profile, then the system shows an error or not found state.

Dependencias
US-05, US-07

Notas o supuestos
Ninguna.

### US-09 — View pipeline for a job opening

User Story
Como Hiring Manager, quiero visualizar el pipeline de una vacante, para entender el estado de cada candidato en el proceso.

Acceptance Criteria

Given a job opening has candidates, when I access the pipeline view, then the system shows the stages Applied, Screening, Interview, and Decision.
Given candidates exist in different stages, when I access the pipeline, then each candidate appears in the corresponding stage column.
Given a stage has no candidates, when I view the pipeline, then the stage remains visible and empty.

Dependencias
US-06

Notas o supuestos
Etapas no configurables en MVP.

### US-10 — Move candidate between stages

User Story
Como Hiring Manager, quiero mover un candidato entre etapas, para actualizar su progreso en el proceso de selección.

Acceptance Criteria

Given a candidate is in a valid stage, when I move the candidate to another valid stage, then the system updates the current stage.
Given the stage change is successful, when I reload the pipeline, then the candidate appears in the new stage.
Given I attempt an invalid stage transition, when I confirm the action, then the system rejects the action and shows an error.

Dependencias
US-09

Notas o supuestos
El movimiento puede implementarse con acción simple en MVP.

### US-11 — Record stage change history

User Story
Como Hiring Manager, quiero que el sistema registre el histórico de cambios de etapa, para mantener trazabilidad del proceso.

Acceptance Criteria

Given a candidate changes stage, when the update is saved, then the system records the previous stage, new stage, and timestamp.
Given a candidate has stage history, when I open the candidate profile, then I can see the recorded transitions.
Given no stage changes exist, when I view the stage history, then the system shows only the initial state or an empty state.

Dependencias
US-10

Notas o supuestos
Sin motivo de cambio en MVP.

## EPIC-03 — AI-Assisted Screening

### US-12 — Generate CV summary

User Story
Como Hiring Manager, quiero que el sistema genere un resumen del CV, para evaluar más rápido el perfil del candidato.

Acceptance Criteria

Given a candidate has a valid CV uploaded, when the system processes the file, then it generates a summary linked to the candidate.
Given the summary was generated successfully, when I open the candidate profile, then the summary is displayed.
Given the processing fails, when I open the candidate profile, then the system indicates that the summary is unavailable.

Dependencias
US-05, US-08

Notas o supuestos
Proceso asíncrono.

### US-13 — Show summary in candidate profile

User Story
Como Hiring Manager, quiero ver el resumen generado por IA dentro del perfil del candidato, para revisar rápidamente su experiencia relevante.

Acceptance Criteria

Given a generated summary exists, when I open the candidate profile, then the summary is shown in a visible section.
Given no generated summary exists yet, when I open the candidate profile, then the system shows a pending or empty state.
Given the summary is displayed, when I read it, then it appears in a structured and readable format.

Dependencias
US-12

Notas o supuestos
Ninguna.

### US-14 — Show summary in candidate list or pipeline

User Story
Como Hiring Manager, quiero ver un extracto del resumen en la vista de candidatos, para priorizar sin abrir cada perfil.

Acceptance Criteria

Given a candidate has a generated summary, when I view the candidate list or pipeline, then the system shows a short summary extract.
Given a candidate does not have a generated summary, when I view the candidate list or pipeline, then the system shows no summary extract or a pending state.
Given multiple candidates have summary extracts, when I compare them in the list or pipeline, then I can differentiate candidates more quickly.

Dependencias
US-07, US-09, US-12

Notas o supuestos
Extracto breve en MVP.

### US-15 — Generate recommendation to advance or reject

User Story
Como Hiring Manager, quiero recibir una recomendación de avanzar o descartar un candidato, para priorizar mejor mi tiempo.

Acceptance Criteria

Given a candidate CV has been processed, when the analysis completes, then the system generates either an “Advance” or “Reject” recommendation.
Given a recommendation exists, when I open the candidate profile, then the recommendation is clearly visible.
Given recommendation generation fails, when I open the candidate profile, then the system shows that the recommendation is unavailable.

Dependencias
US-12

Notas o supuestos
Basada solo en CV en MVP.

### US-16 — Show recommendation explanation

User Story
Como Hiring Manager, quiero ver la explicación de la recomendación, para confiar en la decisión sugerida por el sistema.

Acceptance Criteria

Given a recommendation exists, when I open the candidate profile, then the system shows a short explanation associated with it.
Given the recommendation is “Reject”, when I read the explanation, then the system shows at least one understandable reason.
Given no explanation is available, when I view the recommendation, then the system shows an empty or fallback state.

Dependencias
US-15

Notas o supuestos
Explicación breve y visible.

## EPIC-04 — Interview Feedback & Assisted Evaluation

### US-17 — Register an interview

User Story
Como Hiring Manager, quiero registrar una entrevista para un candidato, para dejar constancia de su paso por evaluación.

Acceptance Criteria

Given a candidate exists in the process, when I enter the interview date and time and save, then the system creates the interview linked to the candidate.
Given required fields are missing, when I submit the interview form, then the system shows validation errors and does not create the interview.
Given the interview is created successfully, when I open the candidate profile, then the interview appears in the candidate details.

Dependencias
US-08

Notas o supuestos
Sin integración de calendario en MVP.

### US-18 — Create manual evaluation after interview

User Story
Como Interviewer, quiero registrar feedback manual después de una entrevista, para documentar el resultado de forma estructurada.

Acceptance Criteria

Given an interview exists, when I enter strengths, weaknesses, and a recommendation and submit, then the system saves the evaluation.
Given the recommendation is missing, when I submit the evaluation, then the system shows a validation error and blocks submission.
Given the evaluation is saved successfully, when I open the candidate profile, then the feedback is visible.

Dependencias
US-17

Notas o supuestos
Recomendación simple: Hire / No Hire / Neutral.

### US-19 — Generate assisted feedback draft

User Story
Como Interviewer, quiero que el sistema genere un borrador de feedback, para completar la evaluación más rápido.

Acceptance Criteria

Given an interview exists, when I open the assisted evaluation flow, then the system generates a draft with strengths, weaknesses, and recommendation.
Given a feedback draft exists, when I review it, then I can edit all generated fields before saving.
Given draft generation fails, when I open the evaluation form, then the system allows me to continue with manual input.

Dependencias
US-17, US-18

Notas o supuestos
Siempre debe existir fallback manual.

### US-20 — Save edited assisted feedback

User Story
Como Interviewer, quiero guardar el feedback asistido tras editarlo, para dejar una evaluación final validada por mí.

Acceptance Criteria

Given an assisted feedback draft exists, when I edit the content and submit it, then the system saves the final evaluation.
Given the final evaluation is saved, when the Hiring Manager opens the candidate profile, then the feedback is visible.
Given required information is missing, when I submit the final feedback, then the system shows a validation error and blocks submission.

Dependencias
US-19

Notas o supuestos
No se guarda versionado intermedio en MVP.

### US-21 — Block move to Decision without feedback

User Story
Como Hiring Manager, quiero que el sistema impida avanzar un candidato a Decision sin feedback registrado, para asegurar decisiones informadas.

Acceptance Criteria

Given a candidate has no evaluation, when I try to move the candidate to the “Decision” stage, then the system blocks the action.
Given a candidate has at least one evaluation, when I move the candidate to the “Decision” stage, then the system allows the transition.
Given the action is blocked, when the validation is triggered, then the system shows a message explaining the reason.

Dependencias
US-10, US-18

Notas o supuestos
Al menos una evaluación requerida.

# 3. Backlog por épicas

## EPIC-01 — Job Openings Management


| ID    | Historia                 | Prioridad | Justificación                                                                    |
| ----- | ------------------------ | --------- | -------------------------------------------------------------------------------- |
| US-01 | Create a job opening     | Must      | Es el punto de entrada del sistema. Sin vacantes no existe proceso de selección. |
| US-02 | View job openings list   | Must      | Necesario para navegar y acceder a vacantes creadas.                             |
| US-03 | View job opening details | Must      | Permite operar sobre la vacante y gestionar candidatos.                          |


## EPIC-02 — Candidate Management & Pipeline


| ID    | Historia                              | Prioridad | Justificación                                                         |
| ----- | ------------------------------------- | --------- | --------------------------------------------------------------------- |
| US-04 | Create a candidate manually           | Must      | Necesario para introducir candidatos en el sistema.                   |
| US-06 | Create application with initial stage | Must      | Define el inicio del pipeline; sin esto no hay flujo de selección.    |
| US-05 | Upload candidate CV                   | Must      | Permite disponer de información básica del candidato para evaluación. |
| US-07 | View candidates list                  | Must      | Necesario para visualizar y gestionar candidatos en una vacante.      |
| US-08 | View candidate profile                | Must      | Permite acceder al detalle del candidato para tomar decisiones.       |
| US-09 | View pipeline                         | Must      | Proporciona visibilidad del proceso completo.                         |
| US-10 | Move candidate between stages         | Must      | Acción clave del flujo de selección; sin esto no hay progreso.        |
| US-11 | Record stage change history           | Should    | Aporta trazabilidad, pero no es imprescindible para el MVP.           |


## EPIC-03 — AI-Assisted Screening


| ID    | Historia                        | Prioridad | Justificación                                                   |
| ----- | ------------------------------- | --------- | --------------------------------------------------------------- |
| US-12 | Generate CV summary             | Could     | Mejora eficiencia, pero depende de que el flujo base ya exista. |
| US-13 | Show summary in profile         | Could     | Depende de US-12; solo aporta valor adicional.                  |
| US-14 | Show summary in list/pipeline   | Could     | Optimiza UX, pero no es necesario para operar el sistema.       |
| US-15 | Generate recommendation         | Could     | Aporta valor diferencial, pero no es core para MVP.             |
| US-16 | Show recommendation explanation | Could     | Depende de US-15; mejora confianza pero no es esencial.         |


## EPIC-04 — Interview Feedback & Assisted Evaluation


| ID    | Historia                                | Prioridad | Justificación                                                                                         |
| ----- | --------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------- |
| US-17 | Register interview                      | Should    | Necesario para estructurar el proceso, pero el sistema puede funcionar sin entrevistas en MVP básico. |
| US-18 | Create manual evaluation                | Should    | Permite decisiones informadas, pero no bloquea funcionamiento inicial.                                |
| US-21 | Block move to Decision without feedback | Should    | Mejora calidad del proceso, pero no es imprescindible inicialmente.                                   |
| US-19 | Generate assisted feedback              | Could     | Feature avanzada dependiente de evaluación manual.                                                    |
| US-20 | Save assisted feedback                  | Could     | Depende de US-19; mejora eficiencia pero no es core.                                                  |


# 4. Backlog global priorizado

### 🔴 MUST

US-01 — Create a job opening
US-02 — View job openings list
US-03 — View job opening details
US-04 — Create a candidate manually
US-06 — Create application with initial stage
US-05 — Upload candidate CV
US-07 — View candidates list
US-08 — View candidate profile
US-09 — View pipeline
US-10 — Move candidate between stages

### 🟡 SHOULD

US-11 — Record stage change history
US-17 — Register interview
US-18 — Create manual evaluation
US-21 — Block move to Decision without feedback

### 🟢 COULD

US-12 — Generate CV summary
US-13 — Show summary in profile
US-14 — Show summary in list/pipeline
US-15 — Generate recommendation
US-16 — Show recommendation explanation
US-19 — Generate assisted feedback
US-20 — Save assisted feedback

# 5. Explicación de la lógica de priorización

La priorización se basa en la metodología MoSCoW, enfocada en construir un MVP funcional con el menor riesgo posible.

Las historias clasificadas como Must corresponden al núcleo del sistema: permiten crear vacantes, añadir candidatos y gestionar su progreso en el pipeline. Sin estas funcionalidades, no existe un flujo de selección operativo.

Las historias Should mejoran la calidad del proceso al añadir trazabilidad y evaluación estructurada, pero no son estrictamente necesarias para validar el producto en una primera versión.

Las historias Could representan capacidades avanzadas, principalmente relacionadas con inteligencia artificial y automatización. Estas funcionalidades aportan diferenciación y eficiencia, pero dependen completamente de que el sistema base esté ya implementado y funcionando.

Esta estrategia permite validar primero el valor fundamental del producto y posteriormente añadir mejoras incrementales con menor riesgo.

# 6. Tickets para las primeras User Stories

## User Story 1 — US-01 Create a job opening

Contexto

Permitir a un Hiring Manager crear una vacante básica con título y descripción para iniciar el proceso de selección.

## Tickets

### T1-01 — Crear endpoint para creación de vacante

Tipo: Backend
Descripción:
Implementar endpoint POST /job-openings que permita crear una nueva vacante.

Body:

```json
{
  "title": "string",
  "description": "string"
}
```

Guardar en tabla JOB_OPENING
Setear status = 'OPEN'
Asociar created_by con usuario autenticado

Acceptance Criteria:

Given valid title and description, when request is sent, then a new job opening is created in DB
Given missing title, when request is sent, then API returns 400 error
Given valid request, when completed, then response returns created job ID

Dependencias: Auth middleware

### T1-02 — Validaciones backend creación vacante

Tipo: Backend
Descripción:
Añadir validaciones:

title obligatorio (min 3 chars)
description opcional pero limitado (ej: 2000 chars)

Acceptance Criteria:

Given empty title, when request is sent, then validation error is returned
Given short title (<3), when request is sent, then validation error is returned
Given valid input, when request is sent, then request succeeds

Dependencias: T1-01

### T1-03 — Formulario frontend creación vacante

Tipo: Frontend
Descripción:
Crear pantalla/formulario:

Input: title
Textarea: description
Botón submit

Acceptance Criteria:

Given user is on create job page, when form is displayed, then title and description inputs are visible
Given user fills form and submits, when clicking submit, then request is sent to backend
Given required fields missing, when submitting, then validation errors are shown

Dependencias: T1-01

### T1-04 — Manejo de estados UI (loading / success / error)

Tipo: Frontend
Descripción:
Gestionar estados:

loading spinner
success redirect a listado
error message

Acceptance Criteria:

Given form submission, when request is pending, then loading state is shown
Given success response, when completed, then user is redirected to jobs list
Given error response, when failed, then error message is displayed

Dependencias: T1-03

## User Story 2 — US-02 View job openings list

Contexto

Permitir al usuario visualizar todas las vacantes creadas para acceder a ellas.

## Tickets

### T2-01 — Endpoint listado de vacantes

Tipo: Backend
Descripción:
Implementar GET /job-openings

Devuelve:

```json
[
  { "id": "", "title": "", "status": "" }
]
```

Acceptance Criteria:

Given jobs exist, when endpoint is called, then list is returned
Given no jobs exist, when endpoint is called, then empty array is returned
Given authenticated user, when request is sent, then only company jobs are returned

Dependencias: T1-01

### T2-02 — UI listado de vacantes

Tipo: Frontend
Descripción:
Crear vista lista:

listado de jobs
mostrar título + status

Acceptance Criteria:

Given jobs exist, when page loads, then jobs are displayed in list
Given no jobs, when page loads, then empty state is shown
Given list loaded, when rendered, then each job shows title and status

Dependencias: T2-01

### T2-03 — Navegación a detalle de vacante

Tipo: Frontend
Descripción:
Añadir interacción click en item → navegar a /jobs/:id

Acceptance Criteria:

Given job list is visible, when user clicks a job, then navigates to job detail page
Given invalid job id, when navigating, then error page is shown
Given valid job, when clicked, then correct job detail loads

Dependencias: T2-02

## User Story 3 — US-03 View job opening details

Contexto

Permitir visualizar el detalle de una vacante y acceder a la gestión de candidatos.

## Tickets

### T3-01 — Endpoint detalle de vacante

Tipo: Backend
Descripción:
Implementar GET /job-openings/{id}

Devuelve:

```json
{
  "id": "",
  "title": "",
  "description": "",
  "status": ""
}
```

Acceptance Criteria:

Given valid job ID, when request is sent, then job data is returned
Given invalid job ID, when request is sent, then 404 is returned
Given authorized user, when accessing job, then job belongs to user company

Dependencias: T1-01

### T3-02 — UI detalle de vacante

Tipo: Frontend
Descripción:
Crear pantalla de detalle:

título
descripción
estado

Acceptance Criteria:

Given job exists, when page loads, then job details are displayed
Given loading state, when fetching data, then loading indicator is shown
Given error, when fetch fails, then error state is shown

Dependencias: T3-01

### T3-03 — Integración con candidatos (entry point)

Tipo: Frontend
Descripción:
Añadir sección placeholder para candidatos:

botón “View candidates”
navegación futura

Acceptance Criteria:

Given job detail page, when loaded, then candidates section is visible
Given user clicks “View candidates”, when action triggered, then navigation occurs (aunque sea placeholder)
Given no candidatos aún, when viewing section, then empty state is shown

Dependencias: T3-02

# 7. Estimaciones de Tickets

## 1. Tabla de estimación


| ID    | Título                                 | Tipo     | Story Points | Justificación                                                                 |
| ----- | -------------------------------------- | -------- | ------------ | ----------------------------------------------------------------------------- |
| T1-01 | Crear endpoint creación vacante        | Backend  | 3            | CRUD simple con persistencia y auth, pero requiere modelo y validación básica |
| T1-02 | Validaciones backend                   | Backend  | 1            | Validaciones simples sobre campos ya definidos                                |
| T1-03 | Formulario frontend creación           | Frontend | 3            | Formulario con inputs, estado y conexión a API                                |
| T1-04 | Estados UI (loading / error / success) | Frontend | 2            | Manejo de estados estándar, sin mucha complejidad                             |
| T2-01 | Endpoint listado de vacantes           | Backend  | 2            | Lectura simple con filtro por usuario/empresa                                 |
| T2-02 | UI listado de vacantes                 | Frontend | 3            | Render de lista + estado vacío                                                |
| T2-03 | Navegación a detalle                   | Frontend | 1            | Routing simple sin lógica compleja                                            |
| T3-01 | Endpoint detalle de vacante            | Backend  | 2            | Similar a listado pero con lookup por ID                                      |
| T3-02 | UI detalle de vacante                  | Frontend | 2            | Render de datos + estados básicos                                             |
| T3-03 | Entry point candidatos (placeholder)   | Frontend | 1            | UI simple sin lógica real aún                                                 |


## 2. Resumen

Total Story Points: 20
Ticket más complejo:
  T1-01 — Crear endpoint creación vacante (3 pts)
Porque implica modelo, persistencia, auth y estructura base del sistema.
Ticket con mayor incertidumbre:
  T1-03 — Formulario frontend creación (3 pts)
Puede variar según manejo de estado, validaciones y cómo esté montado el frontend.