# Tarea 4: Casos de Uso Principales del Sistema LTI-GZL

## Diagramas UML - Casos de Uso

### Diagrama de Casos de Uso General

```mermaid
graph TB
    subgraph "Sistema LTI-GZL"
        UC1[Gestión Completa de Reclutamiento]
        UC2[Colaboración en Tiempo Real]
        UC3[Automatización Inteligente]
    end
    
    subgraph "Actores Primarios"
        REC[Reclutador Senior]
        HM[Hiring Manager]
        SYS[Sistema IA]
    end
    
    subgraph "Actores Secundarios"
        CAND[Candidatos]
        ENT[Entrevistadores]
        ADMIN[Administrador]
    end
    
    %% Relaciones principales
    REC --> UC1
    HM --> UC2
    SYS --> UC3
    
    %% Relaciones secundarias
    CAND -.-> UC1
    ENT -.-> UC2
    ADMIN -.-> UC3
    
    style UC1 fill:#FFB6C1
    style UC2 fill:#98FB98
    style UC3 fill:#87CEEB
```

### Diagrama de Secuencia - Proceso de Reclutamiento

```mermaid
sequenceDiagram
    participant R as Reclutador
    participant S as Sistema LTI
    participant IA as Motor IA
    participant HM as Hiring Manager
    participant C as Candidatos

    R->>S: Crear nueva vacante
    S->>IA: Analizar descripción del puesto
    IA-->>S: Sugerencias de competencias y criterios
    
    C->>S: Aplicar a posición
    S->>IA: Parsing y análisis de CV
    IA-->>S: Scoring inicial del candidato
    
    S->>IA: Ejecutar matching inteligente
    IA-->>S: Ranking de candidatos
    S-->>R: Notificar candidatos top
    
    R->>S: Compartir candidatos con HM
    HM->>S: Evaluar candidatos en workspace
    
    S->>IA: Consolidar feedback
    IA-->>S: Recomendación final
```

### Diagrama de Secuencia - Colaboración en Tiempo Real

```mermaid
sequenceDiagram
    participant S as Sistema LTI
    participant HM as Hiring Manager
    participant R as Reclutador
    participant IA as Motor IA

    S->>S: Detectar entrevistas completadas
    S->>S: Crear workspace de decisión
    S-->>HM: Notificar workspace listo
    S-->>R: Notificar workspace listo
    
    HM->>S: Ingresar a workspace colaborativo
    R->>S: Ingresar a workspace colaborativo
    
    S->>IA: Generar dashboard comparativo
    IA-->>S: Análisis consolidado de candidatos
    
    HM->>S: Emitir voto con justificación
    R->>S: Emitir voto con justificación
    
    S->>IA: Procesar votación ponderada
    IA-->>S: Decisión recomendada
    
    S-->>HM: Confirmar decisión final
```
