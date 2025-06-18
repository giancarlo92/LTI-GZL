# Tarea 7: Diagrama C4 - Sistema de IA/ML (Componente Crítico)

## Sistema de IA/ML - Análisis C4

El Sistema de IA/ML es el diferenciador clave que proporciona matching inteligente, predicciones de éxito y automatización adaptativa.

---

## **NIVEL 1 - CONTEXTO DEL SISTEMA**

### Diagrama de Contexto

```mermaid
graph TB
    subgraph "Usuarios Externos"
        RECRUITER[Reclutadores]
        MANAGERS[Hiring Managers]
        CANDIDATES[Candidatos]
        ADMINS[Administradores]
    end
    
    subgraph "Sistema LTI-GZL"
        AI_SYSTEM[Sistema de IA/ML<br/>Motor Inteligente Central]
    end
    
    subgraph "Sistemas Externos"
        LINKEDIN[LinkedIn API]
        INDEED[Indeed API]
        EMAIL_SYS[Sistema de Email]
        CALENDAR[Sistemas de Calendario]
        HRMS[Sistemas HRMS<br/>Workday/SAP]
        ASSESSMENT[Plataformas de Assessment<br/>HackerRank/Codility]
    end
    
    subgraph "Sistemas Internos LTI-GZL"
        CORE_SERVICES[Servicios Core<br/>Candidatos/Vacantes/Aplicaciones]
        COLLABORATION[Sistema de Colaboración]
        ANALYTICS[Sistema de Analytics]
        NOTIFICATION[Sistema de Notificaciones]
    end
    
    %% Interacciones con usuarios
    RECRUITER -.->|"Configura criterios de matching<br/>Revisa recomendaciones"| AI_SYSTEM
    AI_SYSTEM -.->|"Candidatos rankeados<br/>Insights predictivos"| RECRUITER
    
    MANAGERS -.->|"Feedback de contrataciones<br/>Ajusta pesos de evaluación"| AI_SYSTEM
    AI_SYSTEM -.->|"Recomendaciones de candidatos<br/>Predicciones de éxito"| MANAGERS
    
    CANDIDATES -.->|"Completa evaluaciones<br/>Proporciona información"| AI_SYSTEM
    AI_SYSTEM -.->|"Recomendaciones de posiciones<br/>Feedback personalizado"| CANDIDATES
    
    ADMINS -.->|"Configura modelos<br/>Monitorea performance"| AI_SYSTEM
    AI_SYSTEM -.->|"Métricas de modelos<br/>Alertas de performance"| ADMINS
    
    %% Interacciones con sistemas externos
    AI_SYSTEM <-->|"Enriquecimiento de perfiles<br/>Benchmarking salarial"| LINKEDIN
    AI_SYSTEM <-->|"Análisis de mercado laboral<br/>Trending skills"| INDEED
    AI_SYSTEM -->|"Comunicaciones personalizadas<br/>Recomendaciones automáticas"| EMAIL_SYS
    AI_SYSTEM <-->|"Optimización de scheduling<br/>Análisis de disponibilidad"| CALENDAR
    AI_SYSTEM <-->|"Sincronización de datos<br/>Predicciones de performance"| HRMS
    AI_SYSTEM <-->|"Resultados de evaluaciones<br/>Scoring técnico"| ASSESSMENT
    
    %% Interacciones con sistemas internos
    CORE_SERVICES <-->|"Datos de candidatos/vacantes<br/>Scoring y rankings"| AI_SYSTEM
    COLLABORATION <-->|"Contexto de decisiones<br/>Sugerencias de colaboración"| AI_SYSTEM
    ANALYTICS <-->|"Datos para reportes<br/>Insights predictivos"| AI_SYSTEM
    NOTIFICATION <-->|"Triggers inteligentes<br/>Contenido personalizado"| AI_SYSTEM
    
    style AI_SYSTEM fill:#FFD700,stroke:#FF6B6B,stroke-width:4px
    style RECRUITER fill:#E6F3FF
    style MANAGERS fill:#E6F3FF
    style LINKEDIN fill:#F0F8FF
    style INDEED fill:#F0F8FF
```

## **NIVEL 1 - CONTEXTO DEL SISTEMA**

```mermaid
graph TB
    subgraph "Usuarios Externos"
        RECRUITER[Reclutadores]
        MANAGERS[Hiring Managers]
        CANDIDATES[Candidatos]
    end
    
    subgraph "Sistema LTI-GZL"
        AI_SYSTEM[Sistema de IA/ML<br/>Motor Inteligente Central]
    end
    
    subgraph "Sistemas Externos"
        LINKEDIN[LinkedIn API]
        INDEED[Indeed API]
        HRMS[Sistemas HRMS]
    end
    
    subgraph "Sistemas Internos LTI-GZL"
        CORE_SERVICES[Servicios Core]
        COLLABORATION[Sistema de Colaboración]
        ANALYTICS[Sistema de Analytics]
    end
    
    %% Interacciones principales
    RECRUITER <--> AI_SYSTEM
    MANAGERS <--> AI_SYSTEM
    CANDIDATES <--> AI_SYSTEM
    
    AI_SYSTEM <--> LINKEDIN
    AI_SYSTEM <--> INDEED
    AI_SYSTEM <--> HRMS
    
    CORE_SERVICES <--> AI_SYSTEM
    COLLABORATION <--> AI_SYSTEM
    ANALYTICS <--> AI_SYSTEM
    
    style AI_SYSTEM fill:#FFD700,stroke:#FF6B6B,stroke-width:4px
```

## **NIVEL 2 - CONTENEDORES**

```mermaid
graph TB
    subgraph "Sistema de IA/ML"
        AI_API[AI API Gateway<br/>FastAPI]
        ML_ENGINE[ML Matching Engine<br/>scikit-learn]
        NLP_SERVICE[NLP Processor<br/>spaCy/BERT]
        PREDICTION[Prediction Service<br/>TensorFlow]
        ORCHESTRATOR[AI Orchestrator<br/>Celery]
        MODEL_REGISTRY[Model Registry<br/>MLflow]
        VECTOR_DB[(Vector Database<br/>Pinecone)]
        FEATURE_STORE[Feature Store<br/>Feast]
    end
    
    %% Conexiones
    AI_API --> ML_ENGINE
    AI_API --> NLP_SERVICE
    AI_API --> PREDICTION
    ORCHESTRATOR --> ML_ENGINE
    ORCHESTRATOR --> NLP_SERVICE
    ML_ENGINE --> VECTOR_DB
    NLP_SERVICE --> MODEL_REGISTRY
    PREDICTION --> MODEL_REGISTRY
    ML_ENGINE --> FEATURE_STORE
    
    style AI_API fill:#FFB6C1
    style ML_ENGINE fill:#98FB98
    style ORCHESTRATOR fill:#87CEEB
```

## **NIVEL 3 - COMPONENTES (ML Matching Engine)**

```mermaid
graph TB
    subgraph "ML Matching Engine"
        MATCHING_API[Matching API Controller]
        SKILL_MATCHER[Skill Matching Component]
        EXPERIENCE_ANALYZER[Experience Analyzer]
        CULTURAL_FIT[Cultural Fit Analyzer]
        EMBEDDINGS_ENGINE[Embeddings Engine]
        SCORING_ENGINE[Scoring Engine]
        CACHE_MANAGER[Cache Manager]
        MODEL_LOADER[Model Loader]
    end
    
    %% Flujo de componentes
    MATCHING_API --> SKILL_MATCHER
    MATCHING_API --> EXPERIENCE_ANALYZER
    MATCHING_API --> CULTURAL_FIT
    
    SKILL_MATCHER --> EMBEDDINGS_ENGINE
    EXPERIENCE_ANALYZER --> SCORING_ENGINE
    CULTURAL_FIT --> SCORING_ENGINE
    
    EMBEDDINGS_ENGINE --> CACHE_MANAGER
    SCORING_ENGINE --> MODEL_LOADER
    
    style MATCHING_API fill:#FFB6C1
    style SKILL_MATCHER fill:#98FB98
    style EMBEDDINGS_ENGINE fill:#87CEEB
```

## **NIVEL 4 - CÓDIGO (Skill Matching Component)**

```mermaid
classDiagram
    class SkillMatchingComponent {
        -embeddings_engine: EmbeddingsEngine
        -similarity_calculator: SimilarityCalculator
        -cache_manager: CacheManager
        
        +calculate_skill_match(candidate_skills, required_skills)
        +get_skill_recommendations(candidate_skills)
        +calculate_skill_gap(candidate_skills, required_skills)
    }
    
    class EmbeddingsEngine {
        -model: SentenceTransformer
        -vector_db_client: VectorDBClient
        
        +get_skill_embedding(skill_text)
        +batch_get_embeddings(skills)
        +find_similar_skills(skill_embedding, top_k)
    }
    
    class SimilarityCalculator {
        +cosine_similarity(vector1, vector2)
        +euclidean_distance(vector1, vector2)
        +weighted_similarity(similarities, weights)
    }
    
    class SkillMatchResult {
        +overall_score: float
        +individual_matches: List
        +missing_skills: List
        +confidence: float
    }
    
    SkillMatchingComponent --> EmbeddingsEngine
    SkillMatchingComponent --> SimilarityCalculator
    SkillMatchingComponent ..> SkillMatchResult : creates
```

## Tecnologías Clave

### **API Layer**
- **FastAPI**: API Gateway con documentación automática
- **Pydantic**: Validación de datos y serialización

### **AI Services**
- **scikit-learn**: Algoritmos de machine learning clásicos
- **spaCy + BERT**: Procesamiento de lenguaje natural
- **TensorFlow**: Modelos de deep learning y predicción

### **Orquestación**
- **Celery**: Task queues para procesamiento asíncrono
- **MLflow**: Gestión de modelos y experimentos
- **Feast**: Feature store para ML

### **Almacenamiento**
- **Pinecone/Weaviate**: Base de datos vectorial
- **Redis**: Cache para embeddings y resultados
- **PostgreSQL**: Metadatos y configuraciones
