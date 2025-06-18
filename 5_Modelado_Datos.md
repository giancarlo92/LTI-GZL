# Tarea 5: Modelado de Datos del Sistema LTI-GZL

## Diagrama Entidad-Relación

Modelo de datos completo para el sistema LTI-GZL que incluye las entidades principales para gestión de candidatos, vacantes, colaboración, IA y analytics.

```mermaid
erDiagram
    EMPRESA {
        UUID empresa_id PK
        VARCHAR nombre_empresa
        VARCHAR industria
        INT tamaño_empresa
        VARCHAR direccion
        VARCHAR telefono
        VARCHAR email_contacto
        VARCHAR sitio_web
        JSON configuracion_reclutamiento
        TIMESTAMP fecha_creacion
        TIMESTAMP fecha_actualizacion
        BOOLEAN activo
    }
    
    USUARIO {
        UUID usuario_id PK
        UUID empresa_id FK
        VARCHAR nombre_completo
        VARCHAR email
        VARCHAR telefono
        ENUM rol
        VARCHAR password_hash
        JSON permisos
        JSON preferencias
        TIMESTAMP ultimo_login
        TIMESTAMP fecha_creacion
        BOOLEAN activo
    }
    
    VACANTE {
        UUID vacante_id PK
        UUID empresa_id FK
        UUID creado_por FK
        VARCHAR titulo_posicion
        TEXT descripcion_completa
        JSON requisitos_tecnicos
        JSON competencias_requeridas
        DECIMAL salario_minimo
        DECIMAL salario_maximo
        VARCHAR modalidad_trabajo
        VARCHAR ubicacion
        INT experiencia_minima
        ENUM nivel_senioridad
        ENUM estado_vacante
        JSON criterios_evaluacion
        INT numero_posiciones
        DATE fecha_limite
        TIMESTAMP fecha_creacion
        TIMESTAMP fecha_actualizacion
    }
    
    CANDIDATO {
        UUID candidato_id PK
        VARCHAR nombre_completo
        VARCHAR email
        VARCHAR telefono
        TEXT resumen_profesional
        JSON experiencia_laboral
        JSON educacion
        JSON habilidades_tecnicas
        JSON habilidades_blandas
        JSON certificaciones
        VARCHAR linkedin_url
        VARCHAR portfolio_url
        JSON preferencias_trabajo
        DECIMAL salario_esperado
        VARCHAR ubicacion_actual
        BOOLEAN disponible_reubicacion
        TIMESTAMP fecha_creacion
        TIMESTAMP fecha_actualizacion
    }
    
    APLICACION {
        UUID aplicacion_id PK
        UUID vacante_id FK
        UUID candidato_id FK
        ENUM estado_aplicacion
        DECIMAL score_inicial
        DECIMAL score_actual
        TEXT cover_letter
        JSON documentos_adjuntos
        VARCHAR canal_aplicacion
        TIMESTAMP fecha_aplicacion
        TIMESTAMP fecha_ultima_actualizacion
        UUID asignado_a FK
    }
    
    ETAPA_PROCESO {
        UUID etapa_id PK
        UUID vacante_id FK
        VARCHAR nombre_etapa
        TEXT descripcion
        INT orden_secuencial
        ENUM tipo_etapa
        JSON criterios_evaluacion
        BOOLEAN es_eliminatoria
        INT duracion_estimada_dias
        JSON configuracion_automatizacion
        TIMESTAMP fecha_creacion
    }
    
    APLICACION_ETAPA {
        UUID aplicacion_etapa_id PK
        UUID aplicacion_id FK
        UUID etapa_id FK
        ENUM estado_etapa
        DECIMAL puntuacion
        TEXT comentarios
        JSON feedback_estructurado
        TIMESTAMP fecha_inicio
        TIMESTAMP fecha_completado
        UUID evaluado_por FK
    }
    
    ENTREVISTA {
        UUID entrevista_id PK
        UUID aplicacion_id FK
        UUID etapa_id FK
        ENUM tipo_entrevista
        DATETIME fecha_programada
        INT duracion_minutos
        VARCHAR modalidad
        VARCHAR enlace_reunion
        ENUM estado_entrevista
        JSON agenda_entrevista
        TEXT notas_preparacion
        TIMESTAMP fecha_creacion
        UUID creado_por FK
    }
    
    EVALUACION_ENTREVISTA {
        UUID evaluacion_id PK
        UUID entrevista_id FK
        UUID evaluador_id FK
        JSON criterios_evaluados
        DECIMAL puntuacion_total
        TEXT comentarios_generales
        JSON fortalezas_identificadas
        JSON areas_mejora
        ENUM recomendacion
        TIMESTAMP fecha_evaluacion
    }
    
    COLABORACION_WORKSPACE {
        UUID workspace_id PK
        UUID vacante_id FK
        VARCHAR nombre_workspace
        TEXT descripcion
        ENUM tipo_workspace
        JSON participantes
        JSON configuracion
        ENUM estado_workspace
        TIMESTAMP fecha_creacion
        UUID creado_por FK
    }
    
    MENSAJE_COLABORACION {
        UUID mensaje_id PK
        UUID workspace_id FK
        UUID usuario_id FK
        UUID candidato_referencia FK
        TEXT contenido_mensaje
        ENUM tipo_mensaje
        JSON metadatos
        TIMESTAMP fecha_envio
        BOOLEAN es_sistema
    }
    
    DECISION_COLABORATIVA {
        UUID decision_id PK
        UUID workspace_id FK
        UUID aplicacion_id FK
        JSON votos_stakeholders
        DECIMAL peso_total_votos
        ENUM decision_final
        TEXT justificacion
        TIMESTAMP fecha_decision
        UUID facilitado_por FK
    }
    
    NOTIFICACION_IA {
        UUID notificacion_id PK
        UUID usuario_id FK
        UUID entidad_referencia FK
        ENUM tipo_entidad
        VARCHAR tipo_notificacion
        TEXT mensaje
        JSON datos_contextuales
        ENUM prioridad
        BOOLEAN leido
        TIMESTAMP fecha_creacion
        TIMESTAMP fecha_leido
    }
    
    ANALISIS_IA {
        UUID analisis_id PK
        UUID candidato_id FK
        UUID vacante_id FK
        JSON score_compatibilidad
        JSON predicciones_performance
        JSON analisis_cultural_fit
        JSON recomendaciones_mejora
        DECIMAL confidence_score
        JSON factores_decision
        TIMESTAMP fecha_analisis
        VARCHAR version_modelo
    }
    
    REPORTE_ANALYTICS {
        UUID reporte_id PK
        UUID empresa_id FK
        VARCHAR tipo_reporte
        JSON parametros_reporte
        JSON datos_resultado
        JSON insights_generados
        ENUM formato_salida
        TIMESTAMP fecha_generacion
        UUID generado_por FK
        BOOLEAN es_automatico
    }
    
    INTEGRACION_EXTERNA {
        UUID integracion_id PK
        UUID empresa_id FK
        VARCHAR plataforma_externa
        JSON configuracion_conexion
        JSON mapping_campos
        ENUM estado_integracion
        TIMESTAMP ultima_sincronizacion
        JSON log_errores
        BOOLEAN activa
    }
    
    AUDITORIA_SISTEMA {
        UUID auditoria_id PK
        UUID usuario_id FK
        UUID entidad_afectada FK
        ENUM tipo_entidad
        ENUM accion_realizada
        JSON datos_anteriores
        JSON datos_nuevos
        VARCHAR ip_address
        VARCHAR user_agent
        TIMESTAMP fecha_accion
    }
    
    CONFIGURACION_IA {
        UUID config_id PK
        UUID empresa_id FK
        VARCHAR modelo_ia
        JSON parametros_modelo
        JSON umbrales_decision
        JSON reglas_negocio
        DECIMAL version_modelo
        BOOLEAN activo
        TIMESTAMP fecha_configuracion
        UUID configurado_por FK
    }
    
    FEEDBACK_PERFORMANCE {
        UUID feedback_id PK
        UUID candidato_id FK
        UUID empresa_id FK
        INT dias_post_contratacion
        ENUM performance_rating
        JSON metricas_especificas
        TEXT comentarios_manager
        BOOLEAN recomendaria_nuevamente
        TIMESTAMP fecha_feedback
        UUID proporcionado_por FK
    }

    %% Relaciones principales
    EMPRESA ||--o{ USUARIO : "emplea"
    EMPRESA ||--o{ VACANTE : "publica"
    EMPRESA ||--o{ INTEGRACION_EXTERNA : "configura"
    EMPRESA ||--o{ REPORTE_ANALYTICS : "genera"
    EMPRESA ||--o{ CONFIGURACION_IA : "personaliza"
    
    USUARIO ||--o{ VACANTE : "crea"
    USUARIO ||--o{ APLICACION : "gestiona"
    USUARIO ||--o{ ENTREVISTA : "programa"
    USUARIO ||--o{ EVALUACION_ENTREVISTA : "evalua"
    USUARIO ||--o{ COLABORACION_WORKSPACE : "participa"
    USUARIO ||--o{ MENSAJE_COLABORACION : "envía"
    USUARIO ||--o{ NOTIFICACION_IA : "recibe"
    USUARIO ||--o{ AUDITORIA_SISTEMA : "genera_accion"
    
    VACANTE ||--o{ APLICACION : "recibe"
    VACANTE ||--o{ ETAPA_PROCESO : "define"
    VACANTE ||--o{ COLABORACION_WORKSPACE : "asocia"
    
    CANDIDATO ||--o{ APLICACION : "presenta"
    CANDIDATO ||--o{ ANALISIS_IA : "es_analizado"
    CANDIDATO ||--o{ FEEDBACK_PERFORMANCE : "recibe_feedback"
    
    APLICACION ||--o{ APLICACION_ETAPA : "progresa"
    APLICACION ||--o{ ENTREVISTA : "requiere"
    APLICACION ||--o{ DECISION_COLABORATIVA : "decide"
    APLICACION ||--o{ ANALISIS_IA : "analiza"
    
    ETAPA_PROCESO ||--o{ APLICACION_ETAPA : "ejecuta"
    ETAPA_PROCESO ||--o{ ENTREVISTA : "incluye"
    
    ENTREVISTA ||--o{ EVALUACION_ENTREVISTA : "genera"
    
    COLABORACION_WORKSPACE ||--o{ MENSAJE_COLABORACION : "contiene"
    COLABORACION_WORKSPACE ||--o{ DECISION_COLABORATIVA : "facilita"
```

## Entidades Principales
- **EMPRESA**: Organizaciones cliente del sistema
- **USUARIO**: Reclutadores, hiring managers, entrevistadores
- **VACANTE**: Posiciones abiertas para reclutamiento
- **CANDIDATO**: Perfiles de personas que buscan empleo
- **APLICACION**: Candidaturas a posiciones específicas
- **ENTREVISTA**: Sesiones de evaluación
- **COLABORACION_WORKSPACE**: Espacios de trabajo colaborativo
- **ANALISIS_IA**: Resultados de análisis de inteligencia artificial
- **REPORTE_ANALYTICS**: Dashboards y reportes del sistema
