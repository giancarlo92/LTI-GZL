# Prompts para el Desarrollo del Sistema LTI-GZL

## 1. Prompt para Descripción del Software y Ventajas Competitivas

```
Actúa como un product manager experto en sistemas ATS (Applicant-Tracking System). 

Necesito que diseñes LTI, un ATS innovador para una startup que busca revolucionar el mercado. El sistema debe destacar por:
- Aumentar la eficiencia para departamentos de HR
- Mejorar la colaboración en tiempo real entre reclutadores y managers
- Incorporar automatizaciones inteligentes
- Incluir asistencia de IA en diversas tareas

Proporciona:
1. Una descripción breve y atractiva del software LTI (máximo 200 palabras)
2. El valor añadido que aporta al mercado
3. Las principales ventajas competitivas frente a otros ATS existentes
4. Una propuesta de valor única que lo diferencie

Enfócate en aspectos innovadores que realmente marquen la diferencia en el mercado actual.
```

## 2. Prompt para Funciones Principales

```
Como experto en sistemas de reclutamiento y HR tech, define las funciones principales de LTI, nuestro ATS innovador.

Contexto: LTI debe ser superior a la competencia mediante eficiencia, colaboración en tiempo real, automatización e IA.

Necesito que identifiques y describas:
1. Las 8-10 funciones principales del sistema
2. Para cada función, explica:
   - Qué hace específicamente
   - Cómo mejora la eficiencia del proceso
   - Qué elementos de IA o automatización incluye
   - Cómo facilita la colaboración

Organiza las funciones por categorías (ej: Gestión de candidatos, Colaboración, Automatización, Analytics, etc.)

Asegúrate de que cada función aporte valor diferencial y no sea solo una característica estándar de cualquier ATS.
```

## 3. Prompt para Lean Canvas

```
Actúa como un business analyst especializado en startups de HR tech.

Crea un Lean Canvas completo para LTI, nuestro ATS innovador. 

Contexto del producto:
- ATS del futuro enfocado en eficiencia de HR
- Colaboración en tiempo real entre reclutadores y managers
- Automatizaciones e IA integradas
- Target: empresas medianas y grandes que buscan optimizar sus procesos de reclutamiento

Para cada sección del Lean Canvas, proporciona:

1. **Problema**: Los principales pain points en reclutamiento actual
2. **Segmentos de clientes**: Tipos específicos de empresas/usuarios
3. **Propuesta de valor única**: Qué nos hace únicos
4. **Solución**: Nuestras funciones clave que resuelven los problemas
5. **Canales**: Cómo llegaremos a nuestros clientes
6. **Flujos de ingresos**: Modelos de monetización
7. **Estructura de costos**: Principales gastos del negocio
8. **Métricas clave**: KPIs para medir el éxito
9. **Ventaja competitiva**: Barreras de entrada para competidores

Presenta el resultado en formato de tabla o estructura clara para visualizar fácilmente.
```

## 4. Prompt para Casos de Uso Principales

```
Como analista de sistemas especializado en aplicaciones de reclutamiento, necesito que identifiques y desarrolles los 3 casos de uso principales para LTI.

Contexto: LTI es un ATS innovador con IA, colaboración en tiempo real y automatizaciones.

Para cada caso de uso, proporciona:

1. **Título del caso de uso**
2. **Actor principal**
3. **Actores secundarios**
4. **Precondiciones**
5. **Flujo principal** (paso a paso detallado)
6. **Flujos alternativos** (si aplica)
7. **Postcondiciones**
8. **Reglas de negocio relevantes**

Los casos de uso deben cubrir:
- Uno enfocado en el proceso de reclutamiento end-to-end
- Uno centrado en la colaboración entre stakeholders
- Uno que destaque las capacidades de IA/automatización

Asegúrate de que cada caso de uso refleje las ventajas competitivas de LTI y no sea un proceso genérico de cualquier ATS.

Después de describir cada caso de uso, proporciona las instrucciones específicas para crear el diagrama UML correspondiente.
```

## 5. Prompt para Modelado de Datos

```
Actúa como un arquitecto de datos experto en sistemas de reclutamiento.

Diseña el modelo de datos completo para LTI, considerando:
- Gestión de candidatos y aplicaciones
- Colaboración en tiempo real entre usuarios
- Automatizaciones e IA
- Analytics y reportes
- Gestión de empresas y vacantes

Para cada entidad, proporciona:
1. **Nombre de la entidad**
2. **Atributos** con:
   - Nombre del atributo
   - Tipo de dato
   - Restricciones (PK, FK, NOT NULL, etc.)
   - Descripción breve
3. **Relaciones** con otras entidades:
   - Tipo de relación (1:1, 1:N, N:M)
   - Cardinalidad
   - Descripción de la relación

Entidades mínimas a considerar: Usuario, Empresa, Vacante, Candidato, Aplicación, Entrevista, Evaluación, Etapa, Colaboración, NotificaciónAI, ReporteAnalytics.

También incluye entidades específicas para las funciones de IA y colaboración que diferencian a LTI.

Presenta el resultado de forma estructurada y clara, indicando también las reglas de integridad referencial.
```

## 6. Prompt para Diseño de Alto Nivel

```
Como arquitecto de software senior especializado en sistemas distribuidos y aplicaciones SaaS, diseña la arquitectura de alto nivel para LTI.

Contexto técnico:
- ATS moderno con capacidades de IA
- Colaboración en tiempo real
- Sistema SaaS multi-tenant
- Escalabilidad para empresas medianas/grandes
- Integración con múltiples sistemas externos

Define:

1. **Arquitectura general**:
   - Patrón arquitectónico elegido (ej: microservicios, modular monolith)
   - Justificación de la elección

2. **Componentes principales**:
   - Frontend (tecnologías y responsabilidades)
   - Backend (servicios/módulos principales)
   - Base de datos (tipo y estrategia)
   - Servicios de IA/ML
   - Sistema de notificaciones en tiempo real
   - APIs y integraciones

3. **Infraestructura**:
   - Cloud provider y servicios
   - Estrategia de escalabilidad
   - Seguridad y autenticación
   - Monitoreo y logging

4. **Flujo de datos** entre componentes principales

5. **Decisiones técnicas clave** y sus justificaciones

Enfócate en decisiones que soporten las ventajas competitivas de LTI (IA, colaboración, automatización).

Al final, proporciona instrucciones para crear el diagrama de arquitectura correspondiente.
```

## 7. Prompt para Diagrama C4 - Componente Específico

```
Como arquitecto de software, necesito profundizar en uno de los componentes más críticos de LTI usando el modelo C4.

Elige el componente que consideres más importante para las ventajas competitivas de LTI (sugerencia: Sistema de IA/ML, Motor de Colaboración, o Sistema de Automatización).

Para el componente elegido, desarrolla:

**Nivel 1 - Contexto del Sistema:**
- Cómo este componente se relaciona con usuarios externos y sistemas externos

**Nivel 2 - Contenedores:**
- Containers/servicios que componen este componente
- Tecnologías principales de cada container
- Protocolos de comunicación

**Nivel 3 - Componentes:**
- Componentes software dentro del container principal
- Responsabilidades de cada componente
- Interfaces y dependencias

**Nivel 4 - Código (opcional):**
- Clases/módulos principales del componente más crítico
- Patrones de diseño aplicados

Para cada nivel, proporciona:
1. Descripción textual detallada
2. Elementos que debe contener el diagrama
3. Relaciones y flujos de datos
4. Tecnologías y protocolos específicos

Justifica por qué elegiste este componente como el más importante para detallar.
```