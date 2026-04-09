# **IA para Desarrolladores — Guía Práctica de Desarrollo con Inteligencia Artificial** ⚡

> 🚀 Esta guía está enfocada exclusivamente en **cómo utilizar la IA en entornos de desarrollo de software**. No se trata de entrenar modelos ni construir redes neuronales — sino de entender, integrar y aprovechar la IA como **herramienta de desarrollo**: agentes, sub-agentes, protocolos de comunicación, patrones arquitectónicos y las metodologías que están redefiniendo cómo construimos software.

---

## 📑 Índice

1. [El Nuevo Paradigma: IA en el Desarrollo de Software](#1-el-nuevo-paradigma-ia-en-el-desarrollo-de-software)
2. [Asistentes de Código con IA](#2-asistentes-de-código-con-ia)
3. [Agentes de IA — Concepto y Arquitectura](#3-agentes-de-ia--concepto-y-arquitectura)
4. [Sub-Agentes y Sistemas Multi-Agente](#4-sub-agentes-y-sistemas-multi-agente)
5. [Patrones de Arquitectura Agentica](#5-patrones-de-arquitectura-agentica)
6. [MCP — Model Context Protocol](#6-mcp--model-context-protocol)
7. [A2A — Agent-to-Agent Protocol](#7-a2a--agent-to-agent-protocol)
8. [RAG — Retrieval-Augmented Generation](#8-rag--retrieval-augmented-generation)
9. [Metodologías de Desarrollo con IA](#9-metodologías-de-desarrollo-con-ia)
10. [Context Engineering — La Evolución del Prompt Engineering](#10-context-engineering--la-evolución-del-prompt-engineering)
11. [Frameworks y Herramientas para Desarrollo con Agentes](#11-frameworks-y-herramientas-para-desarrollo-con-agentes)
12. [Skills, Custom Instructions y Plugins](#12-skills-custom-instructions-y-plugins)
13. [Mejores Prácticas y Anti-Patrones](#13-mejores-prácticas-y-anti-patrones)
14. [Ecosistemas Gemini y Claude — Guía Completa para Desarrolladores](#14-ecosistemas-gemini-y-claude--guía-completa-para-desarrolladores)

---

## 1. El Nuevo Paradigma: IA en el Desarrollo de Software

El rol de la IA en el desarrollo ha evolucionado drásticamente. Ya no se limita a autocompletar líneas de código — ahora abarca **agentes autónomos** que pueden planificar, ejecutar, testear e iterar sobre codebases completos.

```
┌────────────────────────────────────────────────────────────────────────────┐
│              EVOLUCIÓN DE LA IA EN EL DESARROLLO                           │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  2021-2022                2023-2024               2025-2026                │
│  ─────────               ──────────              ─────────                 │
│  Autocompletado          Chat + Código           Agentes Autónomos         │
│                                                                            │
│  ┌──────────┐           ┌──────────┐           ┌──────────────────┐       │
│  │ Copilot  │           │ ChatGPT  │           │ Agentes que      │       │
│  │ sugiere  │    ──▶    │ explica  │    ──▶    │ planifican,      │       │
│  │ líneas   │           │ y genera │           │ ejecutan, testan │       │
│  │          │           │ bloques  │           │ e iteran solos   │       │
│  └──────────┘           └──────────┘           └──────────────────┘       │
│                                                                            │
│  "Sugiereme"            "Genérame"             "Hazlo tú: planifica,      │
│                                                 ejecuta y valida"          │
│                                                                            │
│  Skill: Typing          Skill: Prompting        Skill: Context             │
│                                                  Engineering               │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### ¿Qué cambió para el desarrollador?

| Antes (2022) | Ahora (2026) |
| --- | --- |
| Escribías código línea a línea | Diriges agentes que escriben, testan y refactorizan |
| Prompt engineering era la habilidad clave | **Context engineering** es la habilidad clave |
| IA como autocompletado inteligente | IA como **colaborador autónomo** con herramientas |
| Integraciones punto-a-punto custom | Protocolos estándar (MCP, A2A) |
| Un modelo, una tarea | Múltiples agentes especializados colaborando |

---

## 2. Asistentes de Código con IA

Los asistentes de código son la forma más directa en que los desarrolladores interactúan con la IA diariamente. En 2026 se clasifican en tres categorías:

### 2.1 Clasificación de Herramientas

```
┌────────────────────────────────────────────────────────────────────────────┐
│             CATEGORÍAS DE ASISTENTES IA PARA DESARROLLO                    │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  📌 EXTENSIONES DE IDE (Plugins)                                     │  │
│  │  Se integran en tu IDE existente (VS Code, IntelliJ, etc.)          │  │
│  │                                                                      │  │
│  │  • GitHub Copilot — Estándar de la industria, enterprise-ready       │  │
│  │  • Gemini Code Assist — Deep integration con GCP/Android             │  │
│  │  • Amazon Q Developer — Integración nativa con AWS                   │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  🧠 IDEs NATIVOS DE IA (AI-First IDEs)                               │  │
│  │  Construidos ALREDEDOR de la IA, no como add-on                      │  │
│  │                                                                      │  │
│  │  • Cursor — Líder del mercado, multi-file editing, Composer mode     │  │
│  │  • Windsurf — Privacy-first, Cascade (indexación autónoma)           │  │
│  │  • Augment — Enfocado en contexto de codebase grande                 │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  ⌨️ AGENTES DE TERMINAL (CLI Agents)                                 │  │
│  │  Para desarrolladores que viven en la terminal                       │  │
│  │                                                                      │  │
│  │  • Claude Code — Razonamiento complejo, refactoring autónomo         │  │
│  │  • Gemini CLI — Integración con ecosistema Google                    │  │
│  │  • Aider — Open-source, multi-modelo                                │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### 2.2 Comparativa de Herramientas Principales

| Herramienta | Tipo | Mejor Para | Modelos | Destacado |
| --- | --- | --- | --- | --- |
| **GitHub Copilot** | Plugin IDE | Enterprise, compliance, ecosistema GitHub | GPT-4o, Claude, Gemini | IP indemnification, SOC 2, amplio soporte IDE |
| **Cursor** | AI-Native IDE | Experiencia AI-first, multi-file editing | Multi-modelo (toggle) | Composer mode, indexación profunda del codebase |
| **Windsurf** | AI-Native IDE | Privacidad, equipos sensibles | Multi-modelo | Zero Data Retention, Cascade autónomo |
| **Gemini Code Assist** | Plugin IDE | GCP, Android, contexto largo | Gemini | Contexto 1M+ tokens, citaciones |
| **Claude Code** | CLI Agent | Refactoring complejo, tareas autónomas | Claude | Razonamiento superior en terminal |
| **Aider** | CLI Agent | Open-source, flexibilidad total | Cualquier modelo | Git-aware, pair programming en terminal |

### 2.3 El Stack Profesional en 2026

> 💡 Los desarrolladores más productivos **no usan una sola herramienta**. Combinan:

```
┌────────────────────────────────────────────────────────────────┐
│              STACK DE IA DEL DESARROLLADOR PRO                  │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  🖥️  DÍA A DÍA (Autoría de código)                            │
│      AI-Native IDE (Cursor / Windsurf)                         │
│      → Escribir features, navegar codebase, multi-file edits   │
│                                                                │
│  ⌨️  TAREAS COMPLEJAS (Refactoring autónomo)                   │
│      CLI Agent (Claude Code / Gemini CLI)                      │
│      → Migraciones, refactoring masivo, tareas autónomas       │
│                                                                │
│  🤖 REVISIÓN Y CALIDAD                                        │
│      CodeRabbit / Copilot PR Review                            │
│      → Review automático de PRs, sugerencias de seguridad      │
│                                                                │
│  📋  PLANIFICACIÓN Y DISEÑO                                   │
│      Claude / Gemini / ChatGPT (chat directo)                  │
│      → Arquitectura, trade-offs, exploración de soluciones      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 3. Agentes de IA — Concepto y Arquitectura

### ¿Qué es un Agente de IA?

Un **agente de IA** es un sistema que va más allá de responder preguntas — puede **planificar, tomar decisiones, usar herramientas y ejecutar acciones** de forma autónoma para lograr un objetivo.

> 💡 **Diferencia clave:**
> - **LLM:** Recibe un prompt → genera texto
> - **Agente:** Recibe un **objetivo** → planifica pasos → ejecuta acciones → evalúa resultados → itera

### Anatomía de un Agente

```
┌────────────────────────────────────────────────────────────────────────────┐
│                      ANATOMÍA DE UN AGENTE DE IA                           │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│                       ┌──────────────┐                                     │
│                       │   OBJETIVO    │                                     │
│                       │  (del humano) │                                     │
│                       └──────┬───────┘                                     │
│                              │                                             │
│                       ┌──────▼───────┐                                     │
│                       │   CEREBRO    │ ← LLM (GPT, Gemini, Claude)         │
│                       │  (Razona,    │                                      │
│                       │   planifica) │                                      │
│                       └──────┬───────┘                                     │
│                              │                                             │
│               ┌──────────────┼──────────────┐                              │
│               │              │              │                              │
│        ┌──────▼─────┐ ┌─────▼──────┐ ┌─────▼──────┐                      │
│        │ MEMORIA    │ │ HERRAMIEN- │ │ ACCIONES   │                       │
│        │            │ │ TAS/TOOLS  │ │            │                       │
│        │ • Corto    │ │            │ │ • Leer/    │                       │
│        │   plazo    │ │ • APIs     │ │   Escribir │                       │
│        │ • Largo    │ │ • DB       │ │   archivos │                       │
│        │   plazo    │ │ • Search   │ │ • Ejecutar │                       │
│        │ • Contexto │ │ • Code     │ │   comandos │                       │
│        │   de       │ │   exec     │ │ • Llamar   │                       │
│        │   sesión   │ │ • File     │ │   APIs     │                       │
│        │            │ │   system   │ │            │                       │
│        └────────────┘ └────────────┘ └────────────┘                       │
│                              │                                             │
│                       ┌──────▼───────┐                                     │
│                       │  EVALUACIÓN  │                                     │
│                       │  ¿Logré el   │──── NO ──▶ Volver a planificar     │
│                       │  objetivo?   │                                     │
│                       └──────┬───────┘                                     │
│                              │ SÍ                                          │
│                       ┌──────▼───────┐                                     │
│                       │  RESULTADO   │                                     │
│                       └──────────────┘                                     │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Componentes Fundamentales

| Componente | Descripción | Ejemplo en Desarrollo |
| --- | --- | --- |
| **LLM (Cerebro)** | El modelo de lenguaje que razona y toma decisiones | Gemini Pro decide qué archivos modificar |
| **Tools (Herramientas)** | Funciones externas que el agente puede invocar | Ejecutar `mvn test`, leer un archivo, llamar un API |
| **Memory (Memoria)** | Contexto que persiste entre interacciones | Historial de la conversación, estado del proyecto |
| **Planning (Planificación)** | Capacidad de descomponer tareas complejas en pasos | "Primero creo el Service, luego el Controller, luego los Tests" |
| **Evaluation (Evaluación)** | Verificar si el resultado cumple el objetivo | "¿Los tests pasan? ¿El build compila?" |

### El Ciclo del Agente (Agent Loop)

```
┌────────────────────────────────────────────────────────────────┐
│                   AGENT LOOP (Ciclo del Agente)                 │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│     ┌──────────┐                                               │
│     │ OBSERVE  │ ← Recibe objetivo + contexto del entorno      │
│     └────┬─────┘                                               │
│          │                                                     │
│          ▼                                                     │
│     ┌──────────┐                                               │
│     │  THINK   │ ← El LLM razona: ¿qué hago primero?          │
│     └────┬─────┘                                               │
│          │                                                     │
│          ▼                                                     │
│     ┌──────────┐                                               │
│     │   ACT    │ ← Ejecuta herramienta (tool call)             │
│     └────┬─────┘                                               │
│          │                                                     │
│          ▼                                                     │
│     ┌──────────┐     ┌───────────┐                             │
│     │ EVALUATE │────▶│ ¿Listo?   │── NO ──▶ Volver a OBSERVE  │
│     └──────────┘     └─────┬─────┘                             │
│                            │ SÍ                                │
│                      ┌─────▼─────┐                             │
│                      │ RESPONDER │                              │
│                      └───────────┘                             │
│                                                                │
│  Observe → Think → Act → Evaluate → (repetir o responder)     │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 4. Sub-Agentes y Sistemas Multi-Agente

### ¿Qué es un Sub-Agente?

Un **sub-agente** es un agente especializado que es invocado por un agente principal (orquestador) para realizar una tarea específica. En lugar de tener un solo agente que haga todo, se crea un **equipo de especialistas**.

```
┌────────────────────────────────────────────────────────────────────────────┐
│             AGENTE ÚNICO vs SISTEMA MULTI-AGENTE                           │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ❌ AGENTE ÚNICO (Monolítico)        ✅ MULTI-AGENTE (Especializado)      │
│                                                                            │
│  ┌───────────────────────┐          ┌─────────────────────────────┐       │
│  │      UN AGENTE        │          │      ORQUESTADOR            │       │
│  │                       │          │  (Planifica y delega)       │       │
│  │  • Escribe código     │          └────────┬────────────────────┘       │
│  │  • Hace tests         │                   │                            │
│  │  • Revisa seguridad   │          ┌────────┼─────────┬──────────┐      │
│  │  • Documenta          │          │        │         │          │       │
│  │  • Despliega          │     ┌────▼───┐ ┌──▼────┐ ┌──▼───┐ ┌───▼──┐   │
│  │                       │     │ Coder  │ │Tester │ │ Sec  │ │ Docs │   │
│  │  → Se confunde        │     │ Agent  │ │Agent  │ │Agent │ │Agent │   │
│  │  → Pierde contexto    │     └────────┘ └───────┘ └──────┘ └──────┘   │
│  │  → Hace todo "regular"│                                               │
│  └───────────────────────┘     → Cada uno es EXPERTO en su área          │
│                                → Mejor calidad en cada tarea              │
│                                → Escalable y modular                      │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Ejemplo: Sistema Multi-Agente para Desarrollo

```
┌────────────────────────────────────────────────────────────────────────────┐
│         EJEMPLO: EQUIPO DE AGENTES PARA DESARROLLO DE SOFTWARE             │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│                     ┌──────────────────────┐                               │
│                     │   🧠 ORQUESTADOR     │                               │
│                     │   (Agente Principal)  │                               │
│                     │                      │                               │
│                     │ "Implementa el       │                               │
│                     │  endpoint de pagos"  │                               │
│                     └──────────┬───────────┘                               │
│                                │                                           │
│          ┌─────────────────────┼─────────────────────┐                     │
│          │                     │                     │                     │
│   ┌──────▼──────┐      ┌──────▼──────┐      ┌──────▼──────┐              │
│   │ 👨‍💻 CODER   │      │ 🧪 TESTER  │      │ 📝 REVIEWER │              │
│   │             │      │             │      │             │              │
│   │ Modelo:     │      │ Modelo:     │      │ Modelo:     │              │
│   │ Claude      │      │ Gemini      │      │ GPT-4o      │              │
│   │             │      │             │      │             │              │
│   │ Tools:      │      │ Tools:      │      │ Tools:      │              │
│   │ • read_file │      │ • run_tests │      │ • read_file │              │
│   │ • write_file│      │ • coverage  │      │ • lint      │              │
│   │ • search    │      │ • mock_gen  │      │ • security  │              │
│   │             │      │             │      │   scan      │              │
│   │ Tarea:      │      │ Tarea:      │      │ Tarea:      │              │
│   │ "Escribe    │      │ "Genera     │      │ "Revisa     │              │
│   │  PaymentSvc"│      │  los tests" │      │  calidad y  │              │
│   │             │      │             │      │  seguridad" │              │
│   └──────┬──────┘      └──────┬──────┘      └──────┬──────┘              │
│          │                     │                     │                     │
│          └─────────────────────┼─────────────────────┘                     │
│                                │                                           │
│                     ┌──────────▼───────────┐                               │
│                     │   🧠 ORQUESTADOR     │                               │
│                     │   Integra resultados │                               │
│                     │   y entrega final    │                               │
│                     └──────────────────────┘                               │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Cuándo usar Multi-Agente vs Agente Único

| Escenario | Agente Único | Multi-Agente |
| --- | --- | --- |
| Generar una función simple | ✅ | ❌ (overkill) |
| Implementar un feature completo con tests | ⚠️ | ✅ |
| Migración de framework (ej: Java 11 → 21) | ❌ | ✅ |
| Code review automatizado | ✅ | ✅ |
| Pipeline CI/CD completo con seguridad | ❌ | ✅ |
| Pregunta técnica rápida | ✅ | ❌ |

---

## 5. Patrones de Arquitectura Agéntica

Los patrones agénticos son **formas probadas** de organizar agentes para resolver problemas complejos de manera confiable.

### 5.1 Patrón Orquestador-Trabajador (Orchestrator-Worker)

Un agente **manager** descompone el objetivo en subtareas y las delega a agentes **worker** especializados.

```
┌────────────────────────────────────────────────────────────────┐
│            PATRÓN ORQUESTADOR-TRABAJADOR                       │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│                 ┌──────────────┐                               │
│                 │ ORQUESTADOR  │                               │
│                 │ "Implementa  │                               │
│                 │  feature X" │                               │
│                 └──────┬───────┘                               │
│                        │ Descompone                            │
│           ┌────────────┼────────────┐                          │
│           │            │            │                          │
│     ┌─────▼────┐ ┌─────▼────┐ ┌────▼─────┐                   │
│     │ Worker 1 │ │ Worker 2 │ │ Worker 3 │                    │
│     │ "Crea    │ │ "Escribe │ │ "Actualiza│                   │
│     │  modelo" │ │  service"│ │  docs"    │                   │
│     └─────┬────┘ └─────┬────┘ └────┬─────┘                   │
│           │            │            │                          │
│           └────────────┼────────────┘                          │
│                        │ Sintetiza                             │
│                 ┌──────▼───────┐                               │
│                 │ ORQUESTADOR  │                               │
│                 │ Integra y    │                               │
│                 │ entrega      │                               │
│                 └──────────────┘                               │
│                                                                │
│  Ideal para: tareas multidisciplinares, features completos     │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 5.2 Patrón Evaluador-Optimizador (Reflection)

Un agente genera una salida y un segundo agente (o el mismo en modo reflexión) la evalúa y critica, iterando hasta alcanzar un estándar de calidad.

```
┌────────────────────────────────────────────────────────────────┐
│             PATRÓN EVALUADOR-OPTIMIZADOR                       │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│     ┌──────────┐      ┌────────────┐                          │
│     │ GENERADOR│─────▶│ EVALUADOR  │                          │
│     │ Produce  │      │ Critica,   │                          │
│     │ output   │◀─────│ sugiere    │                          │
│     └──────────┘      │ mejoras    │                          │
│          │            └────────────┘                           │
│          │                                                     │
│          │ (Itera N veces hasta calidad aceptable)             │
│          │                                                     │
│     ┌────▼─────┐                                               │
│     │ OUTPUT   │                                               │
│     │ FINAL    │                                               │
│     └──────────┘                                               │
│                                                                │
│  Ideal para: código de alta calidad, documentación,            │
│  tasks donde los errores son costosos                          │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 5.3 Patrón de Routing (Enrutamiento)

Un agente dispatcher analiza la solicitud y la dirige al agente especializado más apropiado.

```
┌────────────────────────────────────────────────────────────────┐
│                   PATRÓN DE ROUTING                             │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│         ┌─────────────┐                                        │
│         │  SOLICITUD   │                                        │
│         └──────┬──────┘                                        │
│                │                                               │
│         ┌──────▼──────┐                                        │
│         │   ROUTER    │  ← Clasifica intención                 │
│         └──────┬──────┘                                        │
│                │                                               │
│     ┌──────────┼──────────┐                                    │
│     │          │          │                                    │
│  ┌──▼───┐  ┌──▼───┐  ┌──▼───┐                                │
│  │ Bug  │  │ New  │  │ Infra│                                 │
│  │ Fix  │  │ Feat │  │      │                                 │
│  │Agent │  │Agent │  │Agent │                                 │
│  └──────┘  └──────┘  └──────┘                                 │
│                                                                │
│  Ideal para: sistemas con diversos tipos de solicitudes        │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 5.4 Patrón de Paralelización (Scatter-Gather)

Múltiples agentes trabajan en paralelo sobre la misma tarea o sobre aspectos diferentes, y los resultados se combinan.

```
┌────────────────────────────────────────────────────────────────┐
│              PATRÓN SCATTER-GATHER                              │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│                ┌──────────┐                                    │
│                │ SCATTER  │ ← Distribuir tarea                 │
│                └────┬─────┘                                    │
│          ┌──────────┼──────────┐                               │
│          │          │          │                               │
│    ┌─────▼───┐ ┌───▼─────┐ ┌─▼───────┐                       │
│    │ Agente  │ │ Agente  │ │ Agente  │  (en paralelo)         │
│    │ enfoque │ │ enfoque │ │ enfoque │                        │
│    │   A     │ │   B     │ │   C     │                        │
│    └─────┬───┘ └───┬─────┘ └─┬───────┘                       │
│          │         │         │                                │
│          └─────────┼─────────┘                                │
│                ┌───▼─────┐                                    │
│                │ GATHER  │ ← Combinar resultados              │
│                └─────────┘                                    │
│                                                                │
│  Ideal para: generar múltiples soluciones,                     │
│  reducir tiempo de ejecución                                   │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### Comparativa de Patrones

| Patrón | Cuándo usar | Complejidad | Ejemplo |
| --- | --- | --- | --- |
| **Orquestador-Worker** | Tareas multidisciplinares | Alta | Feature completo: modelo + servicio + tests + docs |
| **Evaluador-Optimizador** | Calidad crítica | Media | Code review, documentación técnica, SQL crítico |
| **Routing** | Solicitudes diversas | Media | Helpdesk técnico, clasificador de issues |
| **Scatter-Gather** | Velocidad + diversidad | Media-Alta | Generar 3 propuestas de arquitectura en paralelo |

---

## 6. MCP — Model Context Protocol

### ¿Qué es MCP?

El **Model Context Protocol (MCP)** es un estándar abierto (creado por Anthropic, adoptado por la industria) que estandariza cómo las aplicaciones de IA se conectan a **herramientas y fuentes de datos externas**.

> 💡 **Analogía:** MCP es el **"USB-C de la IA"**. Así como USB-C te permite conectar cualquier dispositivo a cualquier puerto sin un cable diferente para cada uno, MCP permite que cualquier agente se conecte a cualquier herramienta sin integraciones custom.

### El Problema que Resuelve

```
┌────────────────────────────────────────────────────────────────────────────┐
│                  EL PROBLEMA M×N DE INTEGRACIONES                          │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ❌ SIN MCP (M×N integraciones custom)                                    │
│                                                                            │
│  ┌─────────┐     custom      ┌──────────┐                                │
│  │ Claude  │─────────────────│ GitHub   │                                │
│  │         │─────────────────│ Postgres │  3 modelos × 4 herramientas    │
│  │         │─────────────────│ Slack    │  = 12 integraciones custom     │
│  │         │─────────────────│ Jira     │                                │
│  ├─────────┤     custom      ├──────────┤  ⚠️ Cada una es diferente      │
│  │ GPT-4   │─────────────────│ GitHub   │  ⚠️ Difícil de mantener        │
│  │         │─────────────────│ Postgres │  ⚠️ No reutilizable            │
│  │         │─────────────────│ Slack    │                                │
│  │         │─────────────────│ Jira     │                                │
│  ├─────────┤     custom      ├──────────┤                                │
│  │ Gemini  │─────────────────│ GitHub   │                                │
│  │         │─────────────────│ Postgres │                                │
│  │         │─────────────────│ Slack    │                                │
│  │         │─────────────────│ Jira     │                                │
│  └─────────┘                 └──────────┘                                │
│                                                                            │
│  ✅ CON MCP (1 protocolo estándar)                                        │
│                                                                            │
│  ┌─────────┐                 ┌──────────┐                                │
│  │ Claude  │──┐              │ GitHub   │──┐                             │
│  ├─────────┤  │   ┌──────┐  ├──────────┤  │                             │
│  │ GPT-4   │──┼──▶│ MCP  │◀─┤ Postgres │──┤                             │
│  ├─────────┤  │   └──────┘  ├──────────┤  │                             │
│  │ Gemini  │──┘              │ Slack    │──┤                             │
│  └─────────┘                 │ Jira     │──┘                             │
│                              └──────────┘                                │
│                                                                            │
│  → UN protocolo para TODOS                                                │
│  → Reutilizable, mantenible, estándar                                     │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Arquitectura MCP

```
┌────────────────────────────────────────────────────────────────────────────┐
│                        ARQUITECTURA MCP                                    │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                          MCP HOST                                    │  │
│  │   (Aplicación de IA: Cursor, Claude Desktop, tu app custom)         │  │
│  │                                                                      │  │
│  │   ┌───────────────┐  ┌───────────────┐  ┌───────────────┐          │  │
│  │   │  MCP Client   │  │  MCP Client   │  │  MCP Client   │          │  │
│  │   │  (conexión 1) │  │  (conexión 2) │  │  (conexión 3) │          │  │
│  │   └───────┬───────┘  └───────┬───────┘  └───────┬───────┘          │  │
│  └───────────┼──────────────────┼──────────────────┼───────────────────┘  │
│              │                  │                  │                      │
│         ┌────▼────┐        ┌────▼────┐        ┌────▼────┐                │
│         │  MCP    │        │  MCP    │        │  MCP    │                │
│         │ Server  │        │ Server  │        │ Server  │                │
│         │         │        │         │        │         │                │
│         │ GitHub  │        │Postgres │        │ Slack   │                │
│         └─────────┘        └─────────┘        └─────────┘                │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Las 3 Primitivas de MCP

| Primitiva | Tipo | Descripción | Ejemplo |
| --- | --- | --- | --- |
| **🔧 Tools** | Ejecutable | Funciones que el modelo puede invocar para realizar acciones | `create_issue()`, `run_query()`, `send_message()` |
| **📄 Resources** | Solo lectura | Fuentes de datos que proveen contexto al modelo | Contenido de archivos, logs, respuestas de API |
| **💬 Prompts** | Plantilla | Templates reutilizables para guiar el comportamiento del modelo | System prompts predefinidos, few-shot examples |

---

## 7. A2A — Agent-to-Agent Protocol

### ¿Qué es A2A?

El **Agent-to-Agent Protocol (A2A)** es un estándar abierto (lanzado por Google, gobernado bajo la Linux Foundation) que estandariza cómo **agentes autónomos interactúan entre sí**.

> 💡 **Si MCP es el USB-C (conecta agente ↔ herramienta), A2A es el idioma compartido (conecta agente ↔ agente).**

### MCP vs A2A — Complementarios, NO competidores

```
┌────────────────────────────────────────────────────────────────────────────┐
│                     MCP + A2A = ECOSISTEMA COMPLETO                        │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌──────────────┐     A2A      ┌──────────────┐                          │
│  │   AGENTE A   │◄────────────▶│   AGENTE B   │   Agente ↔ Agente       │
│  │  (Planning)  │   protocolo  │  (Execution) │                          │
│  └──────┬───────┘              └──────┬───────┘                          │
│         │                             │                                   │
│         │ MCP                         │ MCP                               │
│         │                             │                                   │
│   ┌─────▼─────┐                ┌──────▼──────┐                           │
│   │ GitHub    │                │  Postgres   │   Agente ↔ Herramienta    │
│   │ Server   │                │  Server     │                            │
│   └───────────┘                └─────────────┘                           │
│                                                                            │
│   MCP = Cómo un agente accede a HERRAMIENTAS y DATOS                      │
│   A2A = Cómo un agente COLABORA con OTRO AGENTE                          │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Agent Cards

Los agentes en A2A se descubren mediante **Agent Cards** — documentos de metadatos (JSON) que describen las capacidades, endpoints y requisitos de autenticación de un agente.

```
┌────────────────────────────────────────────────────────────────┐
│              AGENT CARD (Ejemplo)                               │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  {                                                             │
│    "name": "code-review-agent",                                │
│    "description": "Agente especializado en                     │
│                    code review de Java/Spring Boot",           │
│    "capabilities": [                                           │
│      "security-analysis",                                      │
│      "performance-review",                                     │
│      "best-practices-check"                                    │
│    ],                                                          │
│    "endpoint": "https://agents.mycompany.com/reviewer",        │
│    "auth": {                                                   │
│      "type": "oauth2",                                         │
│      "scopes": ["read:code", "write:comments"]                 │
│    },                                                          │
│    "input_format": "code_diff",                                │
│    "output_format": "structured_review"                        │
│  }                                                             │
│                                                                │
│  → Cualquier agente puede leer esta card y saber               │
│    qué hace, cómo contactarlo y qué necesita                   │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

| Característica | MCP | A2A |
| --- | --- | --- |
| **Conecta** | Agente ↔ Herramientas/Datos | Agente ↔ Agente |
| **Analogía** | Puerto USB-C | Idioma compartido |
| **Creador** | Anthropic | Google (Linux Foundation) |
| **Descubrimiento** | El host configura los servers | Agent Cards con capabilities |
| **Resultado** | El agente tiene acceso a información | Los agentes colaboran en equipo |

---

## 8. RAG — Retrieval-Augmented Generation

### ¿Qué es RAG?

**RAG (Retrieval-Augmented Generation)** es un patrón arquitectónico que **potencia a un LLM con conocimiento externo** al recuperar información relevante de tus propios datos antes de generar una respuesta.

> 💡 **¿Por qué RAG?** Los LLMs solo saben lo que aprendieron durante su entrenamiento. RAG les permite acceder a **tus documentos, tu código, tu base de datos** en tiempo real.

### Arquitectura RAG

```
┌────────────────────────────────────────────────────────────────────────────┐
│                     ARQUITECTURA RAG COMPLETA                              │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  📥 FASE DE INGESTIÓN (offline, una vez)                                  │
│                                                                            │
│  ┌────────┐    ┌──────────┐    ┌────────────┐    ┌──────────────────┐     │
│  │ Docs   │───▶│ Chunking │───▶│ Embedding  │───▶│  Vector Store    │     │
│  │ (PDFs, │    │ (dividir │    │ (convertir │    │  (Pinecone,      │     │
│  │  code, │    │  en      │    │  a vectores│    │   Chroma,        │     │
│  │  wiki) │    │  trozos) │    │  numéricos)│    │   Weaviate)      │     │
│  └────────┘    └──────────┘    └────────────┘    └──────────────────┘     │
│                                                                            │
│  🔍 FASE DE CONSULTA (runtime, cada pregunta)                             │
│                                                                            │
│  ┌────────┐    ┌──────────┐    ┌────────────┐    ┌──────────────────┐     │
│  │Pregunta│───▶│ Embedding│───▶│ Búsqueda   │───▶│ Top-K chunks     │     │
│  │del     │    │ de la    │    │ vectorial  │    │ más relevantes   │     │
│  │usuario │    │ pregunta │    │ (similitud │    │                  │     │
│  │        │    │          │    │  coseno)   │    │                  │     │
│  └────────┘    └──────────┘    └────────────┘    └────────┬─────────┘     │
│                                                           │               │
│                                                    ┌──────▼──────┐        │
│                                                    │ Prompt =    │        │
│                                                    │ Pregunta +  │        │
│                                                    │ Contexto    │        │
│                                                    │ recuperado  │        │
│                                                    └──────┬──────┘        │
│                                                           │               │
│                                                    ┌──────▼──────┐        │
│                                                    │    LLM      │        │
│                                                    │  Genera     │        │
│                                                    │  respuesta  │        │
│                                                    │  basada en  │        │
│                                                    │  TUS datos  │        │
│                                                    └─────────────┘        │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Tipos de RAG

| Tipo | Descripción | Cuándo Usarlo |
| --- | --- | --- |
| **Standard RAG** | Retrieve → Generate | QA simple, búsqueda interna |
| **Conversational RAG** | Mantiene historial de sesión | Chatbots, soporte al cliente |
| **Agentic RAG** | El LLM decide cuándo y cómo buscar | Tareas complejas multi-paso |
| **Corrective RAG** | Auto-evalúa y corrige su retrieval | Entornos de alta precisión |
| **GraphRAG** | Usa grafos de conocimiento | Datos con relaciones complejas |

### RAG para Desarrolladores — Casos de Uso

| Caso de Uso | Descripción |
| --- | --- |
| **Chatbot sobre tu codebase** | Pregúntale a la IA sobre tu propio código y recibe respuestas con contexto real |
| **Documentación inteligente** | Busca en tus docs internos y genera respuestas contextualizadas |
| **Onboarding de devs** | Nuevos desarrolladores preguntan y reciben info del wiki del equipo |
| **Soporte técnico interno** | Busca en runbooks y genera respuestas para incidentes |

---

## 9. Metodologías de Desarrollo con IA

### 9.1 Vibe Coding

**Vibe Coding** (término acuñado por Andrej Karpathy en 2025) es un estilo de desarrollo donde el programador describe lo que quiere en lenguaje natural y la IA implementa, debuggea e itera.

```
┌────────────────────────────────────────────────────────────────┐
│                    VIBE CODING                                  │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Flujo tradicional:                                            │
│  Pensar → Diseñar → Codificar → Testear → Debuggear → Deploy  │
│                                                                │
│  Vibe coding:                                                  │
│  Describir intención → IA implementa → Tú revisas → Iteras    │
│                                                                │
│  ⚠️ EN CONTEXTO PROFESIONAL (2026):                           │
│  Vibe coding ≠ "aceptar sin revisar"                           │
│  Vibe coding = herramienta de implementación rápida             │
│                + rigor de ingeniería (tests, review, security)  │
│                                                                │
│  ✅ Bueno para: Prototipos, MVPs, exploración rápida           │
│  ⚠️ Requiere: Revisión, tests automatizados, code review      │
│  ❌ Peligroso si: Aceptas todo sin entender ni verificar       │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 9.2 Plan + Execute (Planificar y Ejecutar)

Metodología donde **primero diriges a la IA para que planifique** la solución (arquitectura, archivos a modificar, pasos), la revisas, y **luego permites la ejecución**.

```
┌────────────────────────────────────────────────────────────────┐
│               PLAN + EXECUTE                                    │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  1. 📋 PLAN (Humano dirige, IA propone)                       │
│     "Antes de escribir código, analiza el codebase y           │
│      propón un plan de implementación"                          │
│     → IA genera: archivos a crear/modificar, diseño, pasos     │
│     → Tú revisas y apruebas o ajustas                          │
│                                                                │
│  2. ⚡ EXECUTE (IA ejecuta, humano supervisa)                  │
│     "Ejecuta el plan aprobado"                                  │
│     → IA implementa archivo por archivo                        │
│     → Tú verificas cada paso                                   │
│                                                                │
│  3. ✅ VERIFY (Humano valida)                                  │
│     → Correr tests, verificar build, revisar código             │
│     → Si algo falla → volver a Plan                            │
│                                                                │
│  Ventaja: Menos re-trabajo, código más coherente,              │
│  el humano mantiene control total                               │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 9.3 Test-Driven AI Development (TDD con IA)

Combina TDD clásico con agentes de IA: **tú escribes los tests** (o defines qué testear) y **la IA escribe el código que los pasa**.

| Paso | Quién | Acción |
| --- | --- | --- |
| 1. Define test | 🧑 Humano | Escribes el test unitario que define el comportamiento esperado |
| 2. Implementa | 🤖 IA | La IA escribe el código que pasa el test |
| 3. Verifica | 🧑 Humano | Ejecutas el test, revisas la implementación |
| 4. Refactoriza | 🤖 IA + 🧑 Humano | La IA propone refactoring, tú decides |

### 9.4 Human-in-the-Loop (HITL)

Patrón donde la IA trabaja de forma autónoma pero **el humano valida decisiones de alto impacto** antes de que se ejecuten.

```
┌────────────────────────────────────────────────────────────────┐
│              HUMAN-IN-THE-LOOP (HITL)                           │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Decisiones de BAJO impacto → IA ejecuta sola                  │
│  ┌──────────────────────────────────────────────┐              │
│  │ • Formatear código                           │              │
│  │ • Generar getters/setters                    │              │
│  │ • Renombrar variables                        │              │
│  └──────────────────────────────────────────────┘              │
│                                                                │
│  Decisiones de ALTO impacto → Humano aprueba                  │
│  ┌──────────────────────────────────────────────┐              │
│  │ • Eliminar archivos    → ⚠️ "¿Confirmas?"    │              │
│  │ • Cambiar schema de DB → ⚠️ "¿Confirmas?"    │              │
│  │ • Desplegar a prod     → ⚠️ "¿Confirmas?"    │              │
│  │ • Modificar seguridad  → ⚠️ "¿Confirmas?"    │              │
│  └──────────────────────────────────────────────┘              │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 10. Context Engineering — La Evolución del Prompt Engineering

### ¿Qué es Context Engineering?

**Context Engineering** es la disciplina de diseñar, estructurar y entregar la **información correcta** al agente de IA **en el momento correcto**. Es la evolución natural del prompt engineering.

```
┌────────────────────────────────────────────────────────────────────────────┐
│          PROMPT ENGINEERING vs CONTEXT ENGINEERING                          │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  PROMPT ENGINEERING (2023-2024)     CONTEXT ENGINEERING (2025-2026)        │
│  ──────────────────────────         ─────────────────────────────          │
│  "¿Cómo formulo la pregunta?"       "¿Qué información necesita el        │
│                                      agente para tener éxito?"             │
│                                                                            │
│  Se enfoca en:                      Se enfoca en:                          │
│  • Redacción del prompt             • Arquitectura del codebase            │
│  • Clever wording                   • Documentación del proyecto           │
│  • Few-shot examples                • Specs de archivos (CLAUDE.md, etc.)  │
│  • System prompts                   • RAG + indexación del repo            │
│                                     • Historial y preferencias             │
│                                     • Constraints y reglas del equipo      │
│                                                                            │
│  Es como:                           Es como:                               │
│  "Hacer la pregunta perfecta        "Preparar todo el material de         │
│   en un examen oral"                 briefing para un consultor nuevo"     │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Técnicas de Context Engineering

| Técnica | Descripción | Ejemplo |
| --- | --- | --- |
| **Project Specs** | Archivos de configuración que el agente lee al inicio (CLAUDE.md, AGENTS.md, .cursorrules) | Definir stack, convenciones, patrones del proyecto |
| **Codebase Indexing** | El IDE indexa todo el repositorio para que el agente tenga contexto global | Cursor indexa el repo completo al abrirlo |
| **RAG sobre docs** | Retrieval automático de documentación interna | El agente busca en tu wiki antes de responder |
| **Memory Systems** | Persistir contexto entre sesiones | El agente recuerda decisiones previas |
| **Constraint Files** | Archivos que definen qué puede y qué NO puede hacer el agente | "No uses var, siempre usa tipos explícitos" |

### Ejemplo: Archivo de Context para tu Proyecto

```markdown
# AGENTS.md — Contexto del Proyecto

## Stack Tecnológico
- Java 21 con Spring Boot 3.4
- PostgreSQL 16 como base de datos principal
- Maven como gestor de dependencias
- Arquitectura Hexagonal

## Convenciones de Código
- Siempre usar record para DTOs
- Services inyectados por constructor (no @Autowired en campos)
- Excepciones custom que extienden RuntimeException
- Tests con JUnit 5 + Mockito + Testcontainers

## Estructura de Paquetes
```
com.myapp
├── domain/          ← Entidades y puertos (interfaces)
├── application/     ← Servicios y casos de uso
├── infrastructure/  ← Adaptadores (DB, APIs, etc.)
└── config/          ← Configuración Spring
```

## Reglas Estrictas
- NO usar Lombok
- NO usar @Data
- Siempre documentar endpoints con @Operation (Swagger)
- Todo endpoint debe tener test de integración
```

---

## 11. Frameworks y Herramientas para Desarrollo con Agentes

### Frameworks Principales

| Framework | Creador | Enfoque | Ideal Para |
| --- | --- | --- | --- |
| **LangChain** | LangChain Inc. | Framework general para apps con LLMs | Cadenas de prompts, integraciones |
| **LangGraph** | LangChain Inc. | Workflows agénticos como grafos cíclicos | Flujos complejos con estado, loops |
| **CrewAI** | CrewAI | Multi-agente con roles (manager-worker) | Equipos de agentes con tareas definidas |
| **AutoGen** | Microsoft | Multi-agente conversacional | Agentes que conversan para resolver problemas |
| **Semantic Kernel** | Microsoft | Orquestación IA para enterprise | Integración con ecosistema Azure/Microsoft |
| **Spring AI** | VMware/Pivotal | IA para Spring Boot | Desarrolladores Java con Spring |
| **Vertex AI ADK** | Google | Desarrollo de agentes en GCP | Agentes con integración Google Cloud |

### Ecosistema de Vector Stores (para RAG)

| Vector Store | Tipo | Destacado |
| --- | --- | --- |
| **Pinecone** | Cloud managed | Escalable, serverless, enterprise-ready |
| **Chroma** | Open-source | Ligero, ideal para desarrollo local |
| **Weaviate** | Open-source / Cloud | Búsqueda híbrida (vectorial + keyword) |
| **Milvus** | Open-source | Alto rendimiento, distribuido |
| **pgvector** | Extensión PostgreSQL | Si ya usas Postgres, no necesitas otra DB |

---

## 12. Skills, Custom Instructions y Plugins

### ¿Qué son las Skills?

Las **Skills** son **módulos de instrucciones reutilizables** que extienden las capacidades de un agente de IA para tareas especializadas. En lugar de repetir las mismas instrucciones complejas en cada conversación, encapsulas ese conocimiento en un archivo `SKILL.md` que el agente carga **bajo demanda** cuando la tarea lo requiere.

> 💡 **Analogía:** Si las Custom Instructions (`AGENTS.md`) son las **reglas generales de la empresa** que todos deben seguir siempre, las Skills son los **manuales de procedimiento especializados** que solo consultas cuando necesitas hacer esa tarea específica.

```
┌────────────────────────────────────────────────────────────────────────────┐
│              JERARQUÍA DE CONFIGURACIÓN DEL AGENTE                         │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  📋 CUSTOM INSTRUCTIONS (Siempre activas)                           │  │
│  │  AGENTS.md / CLAUDE.md / .cursorrules                               │  │
│  │  → "Usa Java 21", "Arquitectura Hexagonal", "No Lombok"             │  │
│  │  → Se cargan SIEMPRE en cada interacción                            │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  🔧 SKILLS (Bajo demanda)                                           │  │
│  │  SKILL.md + scripts/ + templates/                                    │  │
│  │  → "Cómo crear un microservicio", "Cómo hacer deploy a GCP"         │  │
│  │  → Se cargan SOLO cuando la tarea es relevante                       │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  📦 PLUGINS (Paquetes distribuibles)                                 │  │
│  │  plugin.json + skills/ + agents/ + MCP servers                       │  │
│  │  → Agrupan múltiples skills + configuración para un dominio          │  │
│  │  → Se instalan y comparten entre proyectos y equipos                 │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  🔌 MCP SERVERS (Conectividad con el mundo exterior)                 │  │
│  │  → Conexiones a GitHub, Postgres, Slack, APIs                        │  │
│  │  → Pueden usarse DENTRO de una skill                                 │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

### Comparativa: Custom Instructions vs Skills vs Plugins

| Concepto | Propósito | Momento de carga | Alcance | Ejemplo |
| --- | --- | --- | --- | --- |
| **Custom Instructions** | Reglas generales del proyecto, estilo, stack | ✅ Siempre activas | Proyecto | "Usa records para DTOs, no @Data" |
| **Skills** | Capacidades especializadas y reutilizables | 🔄 Bajo demanda | Proyecto / Portable | "Cómo crear un endpoint REST completo" |
| **Plugins** | Paquetes que agrupan skills + MCP + config | 📦 Instalable | Cross-proyecto | "Plugin de CI/CD para GCP" |
| **MCP Servers** | Conexión estandarizada a herramientas/datos | 🔌 Siempre disponible | Infraestructura | Servidor MCP para PostgreSQL |

---

### 12.1 Anatomía de una Skill

Una Skill es un **directorio** que contiene un archivo `SKILL.md` obligatorio y opcionalmente scripts, templates y recursos adicionales.

```
┌────────────────────────────────────────────────────────────────┐
│              ESTRUCTURA DE UNA SKILL                            │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│   .agents/skills/create-microservice/                          │
│   │                                                            │
│   ├── SKILL.md              ← Instrucciones principales        │
│   │   ┌─────────────────────────────────────────────┐          │
│   │   │ ---                                         │          │
│   │   │ name: create-microservice                   │          │
│   │   │ description: Crea un microservicio Spring    │          │
│   │   │              Boot con arquitectura hexagonal │          │
│   │   │ ---                                         │          │
│   │   │                                             │          │
│   │   │ ## Instrucciones                             │          │
│   │   │ 1. Crear la estructura de carpetas...       │          │
│   │   │ 2. Generar el pom.xml con dependencias...   │          │
│   │   │ 3. Implementar el domain model...           │          │
│   │   │ ...                                         │          │
│   │   └─────────────────────────────────────────────┘          │
│   │                                                            │
│   ├── scripts/              ← Scripts auxiliares (opcional)    │
│   │   └── scaffold.sh       ← Script que genera estructura    │
│   │                                                            │
│   ├── templates/            ← Plantillas de código (opcional)  │
│   │   ├── Application.java.tmpl                                │
│   │   └── pom.xml.tmpl                                        │
│   │                                                            │
│   └── examples/             ← Implementaciones de referencia   │
│       └── example-service/                                     │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

#### Estructura del archivo `SKILL.md`

```markdown
---
name: create-rest-endpoint
description: Genera un endpoint REST completo en Spring Boot
             con Controller, Service, Repository, DTOs y tests
---

## Cuándo usar esta skill
Usa esta skill cuando el usuario pida crear un nuevo endpoint,
recurso REST o CRUD en un proyecto Spring Boot.

## Instrucciones

### 1. Estructura de archivos a crear
- `src/.../controller/{Recurso}Controller.java`
- `src/.../service/{Recurso}Service.java`
- `src/.../repository/{Recurso}Repository.java`
- `src/.../dto/{Recurso}Request.java` (usar record)
- `src/.../dto/{Recurso}Response.java` (usar record)

### 2. Convenciones
- Inyección por constructor (NO @Autowired en campos)
- Validación con Jakarta Bean Validation (@Valid, @NotNull)
- ResponseEntity en todos los endpoints
- @Operation para documentación Swagger

### 3. Tests obligatorios
- Test unitario del Service con Mockito
- Test de integración del Controller con @WebMvcTest

### 4. Errores a evitar
- NO usar @Data de Lombok
- NO retornar entidades JPA directamente
- NO hacer lógica de negocio en el Controller
```

#### Cómo funciona la carga progresiva (Progressive Loading)

```
┌────────────────────────────────────────────────────────────────┐
│         PROGRESSIVE LOADING DE SKILLS                          │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  1️⃣  El agente ve todas las skills disponibles                │
│     Solo lee: name + description (YAML frontmatter)            │
│     → Peso en contexto: MÍNIMO (~50 tokens por skill)         │
│                                                                │
│  2️⃣  El usuario pide: "Crea un endpoint para Productos"       │
│                                                                │
│  3️⃣  El agente evalúa: ¿alguna skill es relevante?            │
│     → "create-rest-endpoint" → ✅ ¡Match!                     │
│                                                                │
│  4️⃣  El agente lee el SKILL.md completo                       │
│     → Ahora tiene instrucciones detalladas                     │
│     → Y las sigue paso a paso                                  │
│                                                                │
│  💡 Beneficio: NO carga todas las skills en cada interacción   │
│  Solo carga la que necesita, cuando la necesita                 │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

### 12.2 Custom Instructions — El Ecosistema por IDE

Cada herramienta tiene su propio sistema de configuración, pero el concepto es universal: **darle al agente contexto permanente sobre tu proyecto**.

```
┌────────────────────────────────────────────────────────────────────────────┐
│         ARCHIVOS DE CONFIGURACIÓN POR HERRAMIENTA                          │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  CURSOR                                                                    │
│  ──────                                                                    │
│  📁 .cursor/rules/                                                        │
│  │  ├── general.mdc        ← Reglas globales del proyecto                 │
│  │  ├── backend.mdc        ← Reglas solo para src/main/java/**            │
│  │  ├── testing.mdc        ← Reglas solo para src/test/**                 │
│  │  └── infra.mdc          ← Reglas solo para docker/k8s files            │
│  │                                                                        │
│  │  Formato: Markdown + YAML frontmatter                                  │
│  │  Features: Glob patterns, alwaysApply flag, descriptions               │
│  │  Legacy: .cursorrules (archivo único en raíz)                          │
│  │                                                                        │
│  CLAUDE CODE                                                               │
│  ──────────                                                                │
│  📄 CLAUDE.md              ← En la raíz del proyecto                      │
│  │  → System memory para Claude                                           │
│  │  → Briefing del proyecto: stack, comandos, quirks                      │
│  │                                                                        │
│  GITHUB COPILOT                                                            │
│  ──────────────                                                            │
│  📁 .github/copilot-instructions.md  ← Instrucciones del repo            │
│  │  → Reglas, convenciones, patrones del equipo                           │
│  │                                                                        │
│  GEMINI CODE ASSIST                                                        │
│  ─────────────────                                                         │
│  📁 .gemini/               ← Directorio de configuración                 │
│  │  ├── settings.json      ← Configuración del asistente                 │
│  │  └── styles.md          ← Estilos y convenciones                      │
│  📄 .aiexclude             ← Archivos que la IA NO debe leer             │
│  │                                                                        │
│  UNIVERSAL (Vendor-agnostic)                                               │
│  ────────────────────────────                                              │
│  📄 AGENTS.md              ← Estándar abierto para CUALQUIER agente       │
│  │  → Funciona con Cursor, Claude, Copilot y otros                        │
│  │  → La opción más portable y future-proof                               │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Cursor Rules en detalle (`.mdc` files)

Cursor es el IDE que más ha avanzado en el sistema de reglas contextuales:

| Campo | Descripción | Ejemplo |
| --- | --- | --- |
| **Description** | Le dice al agente cuándo aplicar la regla | "Aplicar al trabajar con servicios Spring" |
| **Globs** | Patrones de archivos donde aplica | `src/main/java/**/service/**/*.java` |
| **alwaysApply** | Si `true`, se carga en TODA interacción | `true` para reglas globales, `false` para específicas |
| **Body** | Las instrucciones en Markdown | Convenciones, patrones, restricciones |

**Ejemplo de un archivo `.cursor/rules/backend.mdc`:**

```markdown
---
description: Reglas para desarrollo backend Java con Spring Boot
globs: src/main/java/**/*.java
alwaysApply: false
---

# Reglas Backend

## Inyección de dependencias
- SIEMPRE usar inyección por constructor
- NUNCA usar @Autowired en campos
- Usar `final` en todos los campos inyectados

## DTOs
- Usar `record` de Java para todos los DTOs
- NUNCA retornar entidades JPA en endpoints REST
- Separar Request y Response DTOs

## Excepciones
- Crear excepciones custom que extiendan RuntimeException
- Usar @ControllerAdvice para manejar excepciones globalmente
- Retornar ProblemDetail (RFC 9457) en respuestas de error

## Naming
- Services: {Dominio}Service (ej: PaymentService)
- Controllers: {Dominio}Controller
- Repositories: {Dominio}Repository
```

---

### 12.3 Plugins — Agrupando Skills para Distribución

Un **Plugin** es un paquete que agrupa múltiples skills, servidores MCP y configuración bajo un mismo dominio. Es la forma de **distribuir y reutilizar** configuraciones de agentes entre proyectos y equipos.

```
┌────────────────────────────────────────────────────────────────┐
│              ESTRUCTURA DE UN PLUGIN                            │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  .agents/plugins/gcp-deployment/                               │
│  │                                                             │
│  ├── plugin.json            ← Metadatos del plugin             │
│  │   {                                                         │
│  │     "name": "gcp-deployment",                               │
│  │     "version": "1.2.0",                                     │
│  │     "description": "Skills para deploy en GCP"              │
│  │   }                                                         │
│  │                                                             │
│  ├── skills/                                                   │
│  │   ├── cloud-run-deploy/                                     │
│  │   │   └── SKILL.md       ← "Cómo desplegar a Cloud Run"    │
│  │   ├── artifact-registry/                                    │
│  │   │   └── SKILL.md       ← "Cómo publicar imágenes Docker" │
│  │   └── cloud-sql-connect/                                    │
│  │       └── SKILL.md       ← "Cómo conectar a Cloud SQL"     │
│  │                                                             │
│  └── agents/                ← Sub-agentes especializados       │
│      └── deploy-agent.md    ← Agente que orquesta el deploy    │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

### 12.4 Beneficios de implementar Skills

| Beneficio | Sin Skills | Con Skills |
| --- | --- | --- |
| **Consistencia** | Cada respuesta de la IA sigue convenciones diferentes | Todas las respuestas siguen el mismo estándar |
| **Reutilización** | Repites instrucciones extensas en cada chat | Escribes una vez, se aplica siempre que sea relevante |
| **Onboarding** | Cada dev nuevo configura su IA diferente | El repo ya incluye las skills — la IA funciona igual para todos |
| **Calidad** | La IA genera código "genérico" | La IA genera código que sigue TUS patrones y prácticas |
| **Eficiencia de contexto** | Se gastan tokens en instrucciones repetitivas | Solo se cargan las skills necesarias (progressive loading) |
| **Portabilidad** | Configuraciones atadas a un IDE/herramienta | Skills en formato abierto funcionan en cualquier agente |

---

### 12.5 Workflow Práctico: Implementar Skills en tu Proyecto

```
┌────────────────────────────────────────────────────────────────┐
│       WORKFLOW: CÓMO EMPEZAR CON SKILLS                        │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  PASO 1: Identifica patrones repetidos                         │
│  ─────────────────────────────────                              │
│  ¿Repites las mismas instrucciones a la IA?                    │
│  "Siempre crea DTOs como records, no olvides los tests,        │
│   usa @Operation para Swagger..."                               │
│  → Eso es candidato para una skill                              │
│                                                                │
│  PASO 2: Separa lo global de lo específico                     │
│  ─────────────────────────────────────────                      │
│  Global (AGENTS.md):                                            │
│  → Stack, convenciones de naming, reglas universales            │
│  Específico (Skills):                                           │
│  → "Cómo crear un microservicio", "Cómo migrar una tabla"      │
│                                                                │
│  PASO 3: Crea la estructura                                    │
│  ───────────────────────────                                    │
│  proyecto/                                                      │
│  ├── AGENTS.md              ← Reglas universales               │
│  └── .agents/                                                   │
│      ├── skills/                                                │
│      │   ├── create-endpoint/                                   │
│      │   │   └── SKILL.md                                       │
│      │   ├── database-migration/                                │
│      │   │   └── SKILL.md                                       │
│      │   └── docker-build/                                      │
│      │       └── SKILL.md                                       │
│      └── workflows/                                             │
│          └── deploy.md      ← Flujos multi-paso                │
│                                                                │
│  PASO 4: Escribe el SKILL.md                                   │
│  ────────────────────────────                                   │
│  → YAML frontmatter: name + description (conciso)              │
│  → Instrucciones: imperativas, claras, con restricciones       │
│  → Errores a evitar: lista de NO hacer                         │
│                                                                │
│  PASO 5: Versiona y comparte                                   │
│  ────────────────────────────                                   │
│  → Commits al repo: todo el equipo se beneficia                │
│  → Code review de las skills: son código, no prosa             │
│  → Itera: si la IA comete un error recurrente, agrega          │
│    una regla a la skill para prevenirlo                         │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 12.6 Cuándo crear una Skill — Regla de Decisión

```
┌────────────────────────────────────────────────────────────────┐
│         ¿DEBERÍA CREAR UNA SKILL?                               │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ¿Repito las mismas instrucciones más de 2 veces?              │
│     │                                                          │
│     ├── NO → Pregunta directa al chat, no necesitas skill      │
│     │                                                          │
│     └── SÍ                                                     │
│          │                                                     │
│          ¿Es una regla SIEMPRE activa?                         │
│          │                                                     │
│          ├── SÍ → Va en Custom Instructions (AGENTS.md)        │
│          │                                                     │
│          └── NO (solo aplica a ciertas tareas)                 │
│               │                                                │
│               ¿Podría servir en OTROS proyectos?               │
│               │                                                │
│               ├── NO → Skill en .agents/skills/                │
│               │                                                │
│               └── SÍ → Skill portable o Plugin                 │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## 13. Mejores Prácticas y Anti-Patrones

### ✅ Mejores Prácticas

| Práctica | Descripción |
| --- | --- |
| **Context over prompts** | Invierte en context engineering (project specs, indexing) antes de optimizar prompts individuales |
| **Plan before execute** | Siempre pide a la IA que planifique antes de ejecutar. Revisar un plan es 10x más rápido que rehacer código |
| **Human-in-the-loop** | Automatiza las decisiones de bajo impacto, pero SIEMPRE valida las de alto impacto |
| **Tests first** | Define comportamiento esperado con tests antes de que la IA implemente |
| **Verifica TODO** | La IA alucina. Verifica cada output contra documentación oficial y ejecución real |
| **Standards (MCP/A2A)** | Usa protocolos estándar en vez de integraciones custom — son más mantenibles y portables |
| **Skills para reutilización** | Si repites instrucciones complejas, encapsúlalas en una skill |
| **Evaluación continua** | Implementa métricas para medir la calidad del output de tus agentes |

### ❌ Anti-Patrones

| Anti-Patrón | Por qué es peligroso |
| --- | --- |
| **"One prompt to rule them all"** | Un solo agente genérico no puede ser experto en todo — usa especialización |
| **"Accept and ship"** | Aceptar código de IA sin revisión introduce bugs, vulnerabilidades y deuda técnica |
| **"No specs, just vibes"** | Sin archivos de contexto (AGENTS.md, skills), la IA inventa convenciones diferentes cada vez |
| **"Custom everything"** | Construir integraciones punto-a-punto custom cuando MCP/A2A ya existen |
| **"Agente monolítico"** | Un solo agente gigante que hace todo pierde focus y produce resultados mediocres |
| **"No observability"** | Si no puedes ver qué decidió el agente y por qué, no puedes debuggearlo ni mejorarlo |
| **"Repetir instrucciones"** | Si escribes lo mismo en cada chat, necesitas una skill — no más copypaste |

---

## 14. Ecosistemas Gemini y Claude — Guía Completa para Desarrolladores

> 💡 Esta sección cubre **exclusivamente** las capacidades de Gemini y Claude orientadas al **desarrollo de software**: modelos, CLIs, sub-agentes, herramientas, precios y mejores prácticas. No se incluye generación de imágenes.

### 14.1 Visión General — Dos Filosofías, Un Objetivo

Gemini (Google) y Claude (Anthropic) son los dos ecosistemas de IA más relevantes para desarrolladores en 2026. Aunque ambos buscan potenciar la productividad del desarrollo, lo hacen desde filosofías distintas:

```
┌────────────────────────────────────────────────────────────────────────────┐
│          GEMINI vs CLAUDE — FILOSOFÍAS DE DISEÑO                           │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌─────────────────────────────────┐  ┌─────────────────────────────────┐ │
│  │         🔵 GEMINI               │  │          🟠 CLAUDE              │ │
│  │     (Google DeepMind)           │  │       (Anthropic)               │ │
│  │                                 │  │                                 │ │
│  │  Filosofía:                     │  │  Filosofía:                     │ │
│  │  "Velocidad + Escala            │  │  "Razonamiento profundo         │ │
│  │   + Ecosistema Google"          │  │   + Fiabilidad + Seguridad"     │ │
│  │                                 │  │                                 │ │
│  │  Fortaleza:                     │  │  Fortaleza:                     │ │
│  │  • Contexto masivo (1M tokens)  │  │  • Razonamiento superior en     │ │
│  │  • Costo competitivo            │  │    código complejo              │ │
│  │  • Integración nativa con GCP   │  │  • Refactoring multi-archivo    │ │
│  │  • Multimodalidad completa      │  │  • Coherencia en contexto largo │ │
│  │  • Free tier generoso           │  │  • Sub-agentes nativos          │ │
│  │                                 │  │                                 │ │
│  │  CLI: Gemini CLI (open-source)  │  │  CLI: Claude Code               │ │
│  │  IDE: Gemini Code Assist        │  │  IDE: Cursor, Windsurf (modelo) │ │
│  │  Cloud: Vertex AI / AI Studio   │  │  Cloud: Anthropic API / AWS     │ │
│  └─────────────────────────────────┘  └─────────────────────────────────┘ │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

### 14.2 Modelos — Línea Completa

#### 🔵 Familia Gemini (Google)

Gemini organiza sus modelos en una jerarquía de **capacidad vs costo**. Todos son nativamente multimodales y soportan ventanas de contexto de hasta **1M de tokens**.

```
┌────────────────────────────────────────────────────────────────────────────┐
│              JERARQUÍA DE MODELOS GEMINI (Abril 2026)                       │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  🏆 FLAGSHIP / RAZONAMIENTO                                               │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Gemini 3.1 Pro                                                      │  │
│  │  → Razonamiento complejo, coding avanzado, tareas agénticas         │  │
│  │  → Ideal para: refactoring complejo, debugging difícil, análisis    │  │
│  │  → Contexto: 1M tokens                                              │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ⚡ BALANCEADO / DEFAULT                                                   │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Gemini 3 Flash                                                      │  │
│  │  → Balance óptimo: velocidad + inteligencia + costo                 │  │
│  │  → Ideal para: desarrollo diario, prototipos, code generation       │  │
│  │  → Output máximo: 66K tokens                                        │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  💰 WORKHORSE / BATCH                                                     │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Gemini 2.5 Pro / 2.5 Flash                                         │  │
│  │  → Producción estable, modelos maduros y bien testeados             │  │
│  │  → Ideal para: pipelines CI/CD con IA, procesamiento batch          │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  🪶 ECONÓMICO / ALTO VOLUMEN                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Gemini 2.0 Flash-Lite                                               │  │
│  │  → El más barato, para tareas simples en masa                       │  │
│  │  → Ideal para: clasificación, routing, boilerplate, validaciones    │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### 🟠 Familia Claude (Anthropic)

Claude organiza sus modelos en tres tiers que reflejan un equilibrio entre **inteligencia** y **velocidad/costo**.

```
┌────────────────────────────────────────────────────────────────────────────┐
│               JERARQUÍA DE MODELOS CLAUDE (Abril 2026)                     │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  🏆 MÁXIMA CAPACIDAD                                                      │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Claude Opus 4.6                                                     │  │
│  │  → El más inteligente: razonamiento profundo, código complejo       │  │
│  │  → Ideal para: refactoring arquitectónico, multi-file editing,      │  │
│  │    análisis cuantitativo, auditorías de seguridad                    │  │
│  │  → Soporta Extended Thinking (razonamiento paso a paso)             │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ⚡ WORKHORSE / EQUILIBRADO                                               │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Claude Sonnet 4.6                                                   │  │
│  │  → El "caballo de batalla": velocidad + inteligencia + costo        │  │
│  │  → Ideal para: día a día, code generation, chat, code review        │  │
│  │  → El modelo DEFAULT para la mayoría de desarrolladores             │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  🪶 RÁPIDO / ECONÓMICO                                                    │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Claude Haiku 4.5                                                    │  │
│  │  → El más rápido y barato del lineup                                │  │
│  │  → Ideal para: lookups rápidos, tareas simples, clasificación,      │  │
│  │    cargas de alto volumen con baja complejidad                      │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Tabla Comparativa de Modelos (Head-to-Head)

| Categoría | 🔵 Gemini | 🟠 Claude | Cuándo Elegir Cada Uno |
| --- | --- | --- | --- |
| **Flagship** | Gemini 3.1 Pro | Claude Opus 4.6 | Gemini: escala + costo · Claude: razonamiento puro |
| **Balanced** | Gemini 3 Flash | Claude Sonnet 4.6 | Gemini: velocidad + precio · Claude: calidad de código |
| **Budget** | Gemini 2.0 Flash-Lite | Claude Haiku 4.5 | Gemini: más barato del mercado · Claude: más inteligente en su tier |
| **Contexto máximo** | 1M tokens | 200K tokens (1M en Claude Code) | Gemini tiene ventaja nativa en contexto largo |
| **Multimodalidad** | Texto, código, audio, video | Texto, código, imágenes | Gemini soporta más tipos de input |

---

### 14.3 Precios API — Costo por Millón de Tokens

> ⚠️ **Nota:** Los precios son referencias de Abril 2026 y pueden cambiar. Consulta siempre la página oficial de cada proveedor.

#### 🔵 Precios Gemini API

| Modelo | Input (por 1M tokens) | Output (por 1M tokens) | Notas |
| --- | --- | --- | --- |
| **Gemini 3.1 Pro** | $2.00 (≤200K) / $4.00 (>200K) | $12.00 (≤200K) / $18.00 (>200K) | Flagship, precio escalonado por contexto |
| **Gemini 3 Flash** | $0.50 | $3.00 | Mejor relación calidad/precio |
| **Gemini 2.5 Pro** | $1.25 | $10.00 | Producción estable |
| **Gemini 2.5 Flash** | $0.30 | $2.50 | Workloads de batch |
| **Gemini 2.0 Flash-Lite** | $0.10 | $0.40 | El más económico del mercado |

**Optimizaciones de costo Gemini:**
- 🔄 **Context Caching**: Hasta 90% de descuento en inputs repetidos
- 📦 **Batch API**: 50% de descuento en procesamiento asíncrono
- 🆓 **Free Tier**: Google AI Studio ofrece un tier gratuito generoso con rate limits diarios

#### 🟠 Precios Claude API

| Modelo | Input (por 1M tokens) | Output (por 1M tokens) | Notas |
| --- | --- | --- | --- |
| **Claude Opus 4.6** | $5.00 | $25.00 | El más caro pero más inteligente |
| **Claude Sonnet 4.6** | $3.00 | $15.00 | Balance inteligencia/costo |
| **Claude Haiku 4.5** | $1.00 | $5.00 | Económico, ideal para volumen |

**Optimizaciones de costo Claude:**
- 🔄 **Prompt Caching**: Hasta 90% de descuento (cache reads = 0.1x del precio base)
- 📦 **Batch API**: 50% de descuento en workloads asíncronos
- 🔗 **Combinación Caching + Batch**: Hasta 95% de ahorro acumulado

#### 💸 Comparativa Visual de Costos

```
┌────────────────────────────────────────────────────────────────────────────┐
│          COMPARATIVA DE COSTOS (Output por 1M tokens)                      │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  Claude Opus 4.6      ████████████████████████████████████  $25.00        │
│  Claude Sonnet 4.6    ████████████████████████             $15.00         │
│  Gemini 3.1 Pro       ███████████████████                  $12.00         │
│  Gemini 2.5 Pro       █████████████████                    $10.00         │
│  Claude Haiku 4.5     ████████                             $5.00          │
│  Gemini 3 Flash       █████                                $3.00          │
│  Gemini 2.5 Flash     ████                                 $2.50          │
│  Gemini Flash-Lite    █                                    $0.40          │
│                                                                            │
│  💡 Conclusión: Gemini es consistentemente más BARATO por token           │
│     Claude justifica su precio con calidad de razonamiento superior       │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

### 14.4 Planes de Suscripción para Desarrolladores

#### 🟠 Claude — Planes de Suscripción con Claude Code

| Plan | Precio/mes | Incluye Claude Code | Ideal Para |
| --- | --- | --- | --- |
| **Claude Pro** | $20 | ✅ (uso ligero-moderado) | Desarrolladores individuales, uso diario ligero |
| **Claude Max 5x** | $100 | ✅ (uso intensivo) | Power users que exceden los límites de Pro |
| **Claude Max 20x** | $200 | ✅ (uso agéntico completo) | Uso full-time, workflows multi-agente |
| **API Pay-as-you-go** | Variable | Con API key | Automatización, workloads variables |
| **Team** | ~$100/usuario | ✅ + seguridad + auditoría | Equipos de desarrollo |

#### 🔵 Gemini — Planes y Acceso

| Canal | Precio | Incluye | Ideal Para |
| --- | --- | --- | --- |
| **Google AI Studio** | Gratuito (con límites) | API, prototipado, playground | Exploración, aprendizaje, prototipos |
| **Gemini CLI** | Gratuito (con API key) | Agente de terminal completo | Desarrollo individual diario |
| **Gemini Code Assist Individual** | Gratuito | Plugin IDE básico | Autocompletado, chat en IDE |
| **Gemini Code Assist Enterprise** | ~$54/usuario/mes | Plugin completo + codebase awareness | Equipos enterprise con GCP |
| **Vertex AI** | Pay-as-you-go | Enterprise, HIPAA/SOC 2, MLOps | Producción enterprise |

---

### 14.5 Herramientas CLI — Gemini CLI vs Claude Code

Las CLIs agénticas son la forma más potente de utilizar estos modelos para desarrollo. Ambas operan directamente en la terminal y actúan como **pares de programación autónomos**.

#### Arquitectura Comparada

```
┌────────────────────────────────────────────────────────────────────────────┐
│            GEMINI CLI vs CLAUDE CODE — ARQUITECTURA                        │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌────────────────────────────────┐  ┌────────────────────────────────┐   │
│  │       🔵 GEMINI CLI            │  │       🟠 CLAUDE CODE           │   │
│  │                                │  │                                │   │
│  │  ┌──────────────────────────┐  │  │  ┌──────────────────────────┐  │   │
│  │  │     GEMINI.md            │  │  │  │     CLAUDE.md            │  │   │
│  │  │  (Contexto del proyecto) │  │  │  │  (Contexto del proyecto) │  │   │
│  │  └────────────┬─────────────┘  │  │  └────────────┬─────────────┘  │   │
│  │               │                │  │               │                │   │
│  │  ┌────────────▼─────────────┐  │  │  ┌────────────▼─────────────┐  │   │
│  │  │    ReAct Loop            │  │  │  │    Agent Loop             │  │   │
│  │  │  (Reason → Act → Eval)  │  │  │  │  (Think → Act → Verify)  │  │   │
│  │  └────────────┬─────────────┘  │  │  └────────────┬─────────────┘  │   │
│  │               │                │  │               │                │   │
│  │  ┌────────────▼─────────────┐  │  │  ┌────────────▼─────────────┐  │   │
│  │  │  Tools Nativos:          │  │  │  │  Tools Nativos:          │  │   │
│  │  │  • grep, file read/write │  │  │  │  • read_file, write_file │  │   │
│  │  │  • shell execution       │  │  │  │  • bash, shell execution │  │   │
│  │  │  • web search/fetch      │  │  │  │  • git operations        │  │   │
│  │  │  • MCP servers           │  │  │  │  • MCP servers           │  │   │
│  │  └────────────┬─────────────┘  │  │  └────────────┬─────────────┘  │   │
│  │               │                │  │               │                │   │
│  │  ┌────────────▼─────────────┐  │  │  ┌────────────▼─────────────┐  │   │
│  │  │  Plan Mode (default ON)  │  │  │  │  Auto Mode               │  │   │
│  │  │  → Investiga antes de    │  │  │  │  → Clasifica acciones:   │  │   │
│  │  │    modificar archivos    │  │  │  │    Safe → auto-ejecuta   │  │   │
│  │  │  → ask_user para validar │  │  │  │    Risk → pide permiso   │  │   │
│  │  └──────────────────────────┘  │  │  └──────────────────────────┘  │   │
│  │                                │  │                                │   │
│  │  Modelo: Gemini 3.1 Pro        │  │  Modelo: Opus 4.6 / Sonnet 4.6│   │
│  │  Licencia: Open Source          │  │  Licencia: Propietario        │   │
│  └────────────────────────────────┘  └────────────────────────────────┘   │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Tabla Comparativa Detallada de CLIs

| Característica | 🔵 Gemini CLI | 🟠 Claude Code |
| --- | --- | --- |
| **Filosofía** | Velocidad, respuesta rápida, ecosistema Google | Razonamiento profundo, planificación estructurada |
| **Instalación** | `npm install -g @anthropic-ai/gemini-cli` (Node.js) | `curl` script / Homebrew / WinGet |
| **Modelo base** | Gemini 3.1 Pro / 3 Flash | Claude Opus 4.6 / Sonnet 4.6 |
| **Contexto** | 1M tokens | 200K tokens (extensible a 1M) |
| **Plan Mode** | ✅ Activado por defecto — investiga antes de actuar | ❌ No nativo, pero implementa via Planning Mode manual |
| **Auto Mode** | No nativo | ✅ Clasifica acciones seguras vs riesgosas automáticamente |
| **Sub-agentes** | ✅ (desde v0.36.0) | ✅ Nativo, altamente configurable |
| **MCP** | ✅ Soporte completo | ✅ Soporte completo |
| **Sandboxing** | ✅ Nativo (macOS Seatbelt, Windows, Linux bwrap) | ✅ Via permisos granulares |
| **Extensiones** | ✅ Framework de Extensions (MCP + GEMINI.md + .toml) | ✅ Custom Slash Commands + Hooks |
| **Free tier** | ✅ Generoso | ❌ Requiere suscripción o API key |
| **Mejor para** | Scripts rápidos, prototipos, workflows GCP | Refactoring complejo, tareas arquitectónicas |

---

### 14.6 Configuración de Proyecto — GEMINI.md vs CLAUDE.md

Ambas CLIs usan archivos de contexto para "recordar" las convenciones, stack y reglas de tu proyecto. Funcionan como la **"memoria persistente"** del agente.

#### Jerarquía de Carga

```
┌────────────────────────────────────────────────────────────────────────────┐
│        JERARQUÍA DE ARCHIVOS DE CONTEXTO                                   │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  🔵 GEMINI.md                            🟠 CLAUDE.md                     │
│                                                                            │
│  1. ~/.gemini/GEMINI.md     (Global)     1. ~/.claude/CLAUDE.md  (Global) │
│  2. /proyecto/GEMINI.md     (Proyecto)   2. ./CLAUDE.md          (Proyecto)│
│  3. /proyecto/sub/GEMINI.md (JIT*)       3. CLAUDE.local.md      (Local*) │
│                                                                            │
│  * JIT = Just-In-Time: se carga          * Local: NO se commitea          │
│    solo cuando un tool accede             → Para notas personales          │
│    a ese subdirectorio                    → Overrides locales              │
│                                                                            │
│  Ambos son Markdown estándar con instrucciones para el agente             │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Ejemplo Práctico: Archivo de Contexto para Java/Spring Boot

```markdown
# GEMINI.md / CLAUDE.md — Proyecto de APIs REST

## Stack Tecnológico
- Java 21 con Spring Boot 3.4
- PostgreSQL 16 + Flyway para migraciones
- Maven como build tool
- Arquitectura Hexagonal (Ports & Adapters)

## Convenciones de Código
- Usa `record` para todos los DTOs
- Inyección por constructor (NO @Autowired en campos)
- Excepciones custom que extienden RuntimeException
- Tests: JUnit 5 + Mockito + Testcontainers

## Estructura de Paquetes
com.myapp
├── domain/          ← Entidades y puertos (interfaces)
├── application/     ← Servicios y casos de uso
├── infrastructure/  ← Adaptadores (DB, APIs, messaging)
└── config/          ← Configuración Spring

## Reglas Estrictas
- NO usar Lombok
- NO usar @Data
- Documentar endpoints con @Operation (Swagger/OpenAPI)
- Todo endpoint debe tener test de integración
- Siempre validar inputs con Jakarta Validation (@Valid)

## Patrones de Respuesta
- Siempre responder usando un ResponseEntity<ApiResponse<T>>
- Manejar errores con @ControllerAdvice global
```

> 💡 **Best Practice:** Mantén tu archivo de contexto **conciso (200-300 líneas máximo)**. Si necesitas más detalle, usa imports modulares:
> - En Claude: `@docs/architecture.md` para cargar archivos adicionales
> - En Gemini: Los archivos JIT en subdirectorios se cargan automáticamente

---

### 14.7 Sub-Agentes — Implementación en Cada Ecosistema

Ambos ecosistemas implementan sub-agentes para resolver el problema del **"context rot"** — cuando una sesión larga se llena de historial y pierde efectividad.

```
┌────────────────────────────────────────────────────────────────────────────┐
│          SUB-AGENTES — EL PROBLEMA QUE RESUELVEN                           │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ❌ SIN Sub-Agentes (sesión monolítica)                                   │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Sesión principal (200K tokens)                                      │  │
│  │  ├── Tarea 1: Crear modelo ──────── contexto crece ──── ██░░░░░░   │  │
│  │  ├── Tarea 2: Crear service ─────── más historial ───── ████░░░░   │  │
│  │  ├── Tarea 3: Crear tests ──────── tool outputs ────── ██████░░    │  │
│  │  └── Tarea 4: Documentar ───────── ¡CONTEXTO LLENO! ── ████████   │  │
│  │                                                                      │  │
│  │  → Calidad DEGRADA con cada tarea ↓↓↓                              │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ✅ CON Sub-Agentes (contextos aislados)                                  │
│                                                                            │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │  Sesión principal (limpia, solo planificación)                       │  │
│  │  ├── Delega Tarea 1 → Sub-Agente A (contexto propio) → resultado   │  │
│  │  ├── Delega Tarea 2 → Sub-Agente B (contexto propio) → resultado   │  │
│  │  ├── Delega Tarea 3 → Sub-Agente C (contexto propio) → resultado   │  │
│  │  └── Integra resultados (contexto principal = limpio)               │  │
│  │                                                                      │  │
│  │  → Cada sub-agente empieza fresco, la sesión principal se mantiene  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### 🟠 Sub-Agentes en Claude Code

Claude Code implementa sub-agentes de forma **nativa y altamente configurable**:

- **Contexto aislado**: Cada sub-agente tiene su propio contexto de 200K tokens
- **Tools restrictivos**: Puedes definir qué herramientas puede usar cada sub-agente
- **Instrucciones custom**: Cada sub-agente recibe su propio system prompt
- **Agent Teams** (experimental): Múltiples sesiones de Claude Code que se coordinan y comunican directamente para tareas paralelizables

```
┌────────────────────────────────────────────────────────────────┐
│         CLAUDE CODE — SISTEMA DE SUB-AGENTES                    │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌─────────────────────────────────────────────────────┐      │
│  │  🧠 SESIÓN PRINCIPAL (Orquestador)                   │      │
│  │  "Implementa el módulo de pagos completo"           │      │
│  └──────────────┬────────────────────────────┘         │      │
│                 │                                       │      │
│     ┌───────────┼───────────┬───────────┐              │      │
│     │           │           │           │               │      │
│  ┌──▼────┐  ┌──▼────┐  ┌──▼────┐  ┌──▼────┐          │      │
│  │Sub-A  │  │Sub-B  │  │Sub-C  │  │Sub-D  │           │      │
│  │       │  │       │  │       │  │       │           │      │
│  │Modelo │  │Service│  │Tests  │  │Docs   │           │      │
│  │       │  │       │  │       │  │       │           │      │
│  │Tools: │  │Tools: │  │Tools: │  │Tools: │           │      │
│  │read   │  │read   │  │read   │  │read   │           │      │
│  │write  │  │write  │  │write  │  │write  │           │      │
│  │       │  │bash   │  │bash   │  │       │           │      │
│  │       │  │       │  │(tests)│  │       │           │      │
│  └───┬───┘  └───┬───┘  └───┬───┘  └───┬───┘           │      │
│      │          │          │          │                │      │
│      └──────────┴──────────┴──────────┘                │      │
│                     │                                  │      │
│  ┌──────────────────▼──────────────────────────┐      │      │
│  │  Orquestador: Integra outputs, valida,       │      │      │
│  │  genera resultado final coherente             │      │      │
│  └───────────────────────────────────────────────┘      │      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Extensibilidad con Slash Commands:**

Claude Code permite crear **comandos custom** que activan sub-agentes especializados:

```
# Crear: .claude/commands/review.md
---
description: "Ejecuta code review completo"
allowed_tools: [read_file, bash]
model: claude-sonnet-4.6
---
Revisa el código en el directorio actual:
1. Verifica patrones de seguridad
2. Evalúa complejidad ciclomática
3. Sugiere mejoras de rendimiento
!git diff --staged  ← Inyecta output de shell en el prompt
```

**Hooks — Automatización Determinista:**

```json
// .claude/settings.json
{
  "hooks": {
    "post-file-edit": {
      "command": "npx prettier --write $FILE && npx eslint --fix $FILE",
      "description": "Auto-format y lint después de cada edición"
    },
    "pre-commit": {
      "command": "npm test",
      "description": "Ejecutar tests antes de commitear"
    }
  }
}
```

#### 🔵 Sub-Agentes en Gemini CLI

Gemini CLI implementa sub-agentes desde la **v0.36.0** con un enfoque en **seguridad y planificación**:

- **Entornos aislados**: Cada sub-agente ejecuta en su propia sandbox
- **Historial independiente**: Sin contaminación de contexto entre tareas
- **Tools restrictivos**: Sets de herramientas específicos por sub-agente
- **Plan Mode integrado**: El orquestador planifica antes de delegar

```
┌────────────────────────────────────────────────────────────────┐
│         GEMINI CLI — SISTEMA DE SUB-AGENTES                     │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌───────────────────────────────────────────────────────┐    │
│  │  🧠 AGENTE PRINCIPAL                                   │    │
│  │  Plan Mode: ACTIVADO (investiga primero)               │    │
│  │                                                        │    │
│  │  1. Mapea dependencias del codebase                    │    │
│  │  2. Propone estrategia al developer (ask_user)         │    │
│  │  3. Developer aprueba → delega a sub-agentes           │    │
│  └──────────────┬────────────────────────────┘            │    │
│                 │                                          │    │
│     ┌───────────┼───────────┐                             │    │
│     │           │           │                              │    │
│  ┌──▼────────┐ ┌▼────────┐ ┌▼────────┐                   │    │
│  │Specialist │ │Specialist│ │Specialist│                  │    │
│  │ A         │ │ B        │ │ C        │                  │    │
│  │           │ │          │ │          │                   │    │
│  │Sandbox:   │ │Sandbox:  │ │Sandbox:  │                  │    │
│  │Aislado    │ │Aislado   │ │Aislado   │                  │    │
│  │           │ │          │ │          │                   │    │
│  │Context:   │ │Context:  │ │Context:  │                  │    │
│  │Propio     │ │Propio    │ │Propio    │                  │    │
│  └───────────┘ └──────────┘ └──────────┘                  │    │
│                                                                │
│  Diferencial: Plan Mode + ask_user aseguran que el developer  │
│  SIEMPRE valide la estrategia antes de ejecutar               │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Extensions Framework — Modularidad:**

Gemini CLI tiene un sistema de **Extensions** que empaquetan todo junto:

```
my-extension/
├── gemini-extension.json    ← Metadata, settings, API keys
├── GEMINI.md                ← Contexto adicional del extension
├── commands/
│   └── deploy.toml          ← Slash commands custom
└── mcp/
    └── config.json          ← Servidores MCP bundled
```

---

### 14.8 Integración con IDEs

#### 🔵 Gemini Code Assist (Plugin IDE)

| Característica | Detalle |
| --- | --- |
| **IDEs soportados** | VS Code, JetBrains (IntelliJ, Android Studio), Cloud Shell Editor |
| **Autocompletado** | Code completion inteligente basado en contexto local |
| **Chat** | Conversación multi-turno dentro del IDE |
| **Contexto** | 1M+ tokens de ventana de contexto para awareness del codebase |
| **Code Customization** | Enterprise puede alimentar con codebase privado |
| **Integración GCP** | Nativa: Firebase, BigQuery, Cloud Run, Apigee |
| **Seguridad Enterprise** | Data governance, IP indemnification, SOC 2 |

#### 🟠 Claude como Modelo en IDEs AI-Native

Claude **no tiene un plugin IDE propio** — en cambio, funciona como **motor** dentro de IDEs AI-native:

| IDE | Cómo usa Claude | Experiencia |
| --- | --- | --- |
| **Cursor** | Seleccionable como modelo (Opus/Sonnet) para chat, compose, agent | Experiencia más pulida, multi-file editing nativo |
| **Windsurf** | Motor para Cascade (agente autónomo) | Cascade usa Claude para razonamiento profundo |
| **GitHub Copilot** | Seleccionable como modelo alternativo | Enterprise, compliance-ready |
| **VS Code (extensions)** | Extensions de terceros que wrappean Claude API | Variable según el extension |

```
┌────────────────────────────────────────────────────────────────┐
│     ¿CÓMO ACCEDER A CADA MODELO DESDE TU IDE?                  │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  🔵 GEMINI                                                     │
│  ┌────────────────────────────────────────────────────┐       │
│  │  VS Code / JetBrains                               │       │
│  │  └─→ Instalar "Gemini Code Assist" (plugin oficial)│       │
│  │       → Chat, autocomplete, code gen integrado     │       │
│  │                                                     │       │
│  │  Terminal                                           │       │
│  │  └─→ Gemini CLI (npm install, agente completo)     │       │
│  └────────────────────────────────────────────────────┘       │
│                                                                │
│  🟠 CLAUDE                                                     │
│  ┌────────────────────────────────────────────────────┐       │
│  │  Cursor / Windsurf                                  │       │
│  │  └─→ Seleccionar Claude como modelo en settings    │       │
│  │       → Chat, Compose, Agent mode con Claude       │       │
│  │                                                     │       │
│  │  Terminal                                           │       │
│  │  └─→ Claude Code CLI (agente agéntico completo)    │       │
│  └────────────────────────────────────────────────────┘       │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

### 14.9 ¿Qué Consume Más Tokens? — Anatomía del Consumo

Entender **dónde se van tus tokens** es crítico para controlar costos y mantener la calidad del output.

```
┌────────────────────────────────────────────────────────────────────────────┐
│         ANATOMÍA DEL CONSUMO DE TOKENS EN WORKFLOWS AGÉNTICOS              │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  📥 INPUT TOKENS (lo que el modelo RECIBE)                                │
│  ──────────────────────────────────────────                                │
│                                                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │  1. System Prompt + CLAUDE.md / GEMINI.md     ██░░░░  ~10-15%      │  │
│  │  2. Tool/MCP Schema Definitions               ████░░  ~15-25%     │  │
│  │     (¡CADA servidor MCP conectado suma!)                            │  │
│  │  3. Código fuente incluido como contexto       ██████  ~20-30%     │  │
│  │  4. Historial de conversación                  ████████ ~25-40%    │  │
│  │     (¡El MÁS CARO en sesiones largas!)                             │  │
│  │  5. Tool call outputs (resultados anteriores)  ██████  ~15-25%     │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  📤 OUTPUT TOKENS (lo que el modelo GENERA)                               │
│  ──────────────────────────────────────────                                │
│                                                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐  │
│  │  1. Razonamiento / Thinking tokens              ██████  ~30-40%    │  │
│  │     (Extended Thinking en Claude Opus)                              │  │
│  │  2. Código generado                             █████  ~25-35%     │  │
│  │  3. Explicaciones y texto conversacional         ███  ~15-20%      │  │
│  │  4. Tool call requests (JSON de invocación)     ██  ~10-15%        │  │
│  └─────────────────────────────────────────────────────────────────────┘  │
│                                                                            │
│  ⚠️ EL MAYOR CONSUMIDOR: Historial + Tool Outputs en sesiones largas     │
│     → Los loops de "review and rework" consumen ~60% del total            │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Los Mayores "Vampiros" de Tokens

| Factor | Impacto | Mitigación |
| --- | --- | --- |
| **Servidores MCP no usados** | Cada MCP server cargado inyecta su schema en CADA request | Desactiva MCP servers que no necesitas para la tarea actual |
| **Historial de conversación largo** | Crece con cada interacción, se re-envía completo | Usa sub-agentes para aislar contexto · Resumen y reinicia sesiones |
| **Repo dump (todo el código)** | Anti-patrón: incluir todo el repo como contexto | Usa retrieval selectivo (solo archivos relevantes) |
| **Extended Thinking (Claude)** | Los "thinking tokens" se facturan como output | Usa Sonnet en lugar de Opus para tareas que no requieren razonamiento profundo |
| **Tool outputs verbosos** | Outputs de comandos shell largos (logs, stack traces) | Filtra y trunca outputs antes de enviarlos al modelo |

---

### 14.10 Mejores Prácticas por Ecosistema

#### Prácticas Universales (Ambos)

| Práctica | Descripción |
| --- | --- |
| **🔄 Prompt Caching** | Estructura prompts con contenido estático al inicio y variable al final — maximiza cache hits |
| **📋 Context File actualizado** | Mantén GEMINI.md/CLAUDE.md actualizado con convenciones reales del proyecto |
| **🧩 Sub-agentes para tareas complejas** | No hagas todo en una sola sesión — delega subtareas a contextos aislados |
| **📏 Mide tokens** | Usa `/cost` (Claude Code) o monitoreo en AI Studio (Gemini) para trackear consumo |
| **🎯 Retrieval selectivo** | NO hagas "repo dump" — incluye solo los archivos relevantes para la tarea |
| **⏹️ Stop sequences** | Configura stop sequences para evitar que el modelo genere output innecesario |
| **📦 Structured output** | Usa JSON mode para evitar texto conversacional — más barato y parseable |

#### 🔵 Prácticas Específicas Gemini

| Práctica | Detalle |
| --- | --- |
| **Free Tier para prototipado** | Usa Google AI Studio gratis para explorar y prototipar antes de pagar |
| **Flash como default** | Usa Gemini 3 Flash para el 80% de las tareas, Pro solo cuando sea necesario |
| **Plan Mode activo** | Deja Plan Mode activado — evita cambios "eager" no deseados |
| **Extensions modulares** | Empaqueta MCP + contexto + comandos en Extensions reutilizables |
| **Batch API para CI/CD** | Usa Batch API (50% off) para tareas de pipeline no urgentes |
| **Context Caching** | Cachea documentación y specs del proyecto que no cambian frecuentemente |
| **JIT Context** | Aprovecha que GEMINI.md en subdirectorios se carga on-demand |

#### 🟠 Prácticas Específicas Claude

| Práctica | Detalle |
| --- | --- |
| **Sonnet como default** | Usa Sonnet 4.6 para el día a día, Opus solo para razonamiento complejo |
| **CLAUDE.md conciso** | Mantén bajo 300 líneas, usa `@imports` para detalle modular |
| **Hooks para calidad** | Configura hooks post-edit para auto-format + lint automáticamente |
| **Custom Slash Commands** | Crea comandos para workflows repetitivos (/review, /test, /deploy) |
| **Max plan si uso intensivo** | Si superas límites de Pro, el plan Max 5x/20x es más económico que API directa |
| **Caching + Batch combo** | Combina Prompt Caching + Batch API para hasta 95% de ahorro |
| **Extended Thinking selectivo** | Activa Extended Thinking solo cuando la tarea lo amerita — consume tokens extra |

---

### 14.11 ¿Cada Uno Para Qué Es Mejor?

```
┌────────────────────────────────────────────────────────────────────────────┐
│          ¿CUÁNDO USAR GEMINI vs CLAUDE?                                    │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  USAR 🔵 GEMINI CUANDO...              USAR 🟠 CLAUDE CUANDO...          │
│  ─────────────────────────             ──────────────────────────          │
│                                                                            │
│  ✅ Necesitas procesar contextos       ✅ La tarea requiere razonamiento  │
│     masivos (>200K tokens)                profundo y multi-paso           │
│                                                                            │
│  ✅ El presupuesto es prioridad        ✅ Haces refactoring multi-archivo │
│     (tokens más baratos)                  complejo y arquitectónico       │
│                                                                            │
│  ✅ Trabajas con ecosistema Google     ✅ Necesitas coherencia impecable  │
│     (GCP, Firebase, BigQuery)             en código generado              │
│                                                                            │
│  ✅ Necesitas prototipar rápido        ✅ Auditorías de seguridad y       │
│     (free tier + velocidad Flash)         análisis de vulnerabilidades    │
│                                                                            │
│  ✅ Procesas video, audio o datos      ✅ El proyecto tiene convenciones  │
│     multimodales además de código         estrictas que deben respetarse  │
│                                                                            │
│  ✅ CI/CD automatizado con IA          ✅ Migraciones de framework        │
│     (Batch API + bajo costo)              (ej: Java 11 → 21)             │
│                                                                            │
│  ✅ Equipo ya usa GCP/Vertex AI        ✅ Code review exhaustivo con      │
│                                           foco en best practices          │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

#### Tabla de Decisión por Tipo de Tarea

| Tarea de Desarrollo | 🔵 Gemini | 🟠 Claude | Recomendación |
| --- | --- | --- | --- |
| **Script rápido / utilidad** | ⭐⭐⭐ | ⭐⭐ | Gemini Flash — velocidad + costo |
| **Prototipo / MVP** | ⭐⭐⭐ | ⭐⭐⭐ | Ambos excelentes. Gemini por costo, Claude por calidad |
| **Refactoring multi-archivo** | ⭐⭐ | ⭐⭐⭐ | Claude Opus — razonamiento superior |
| **Migración de framework** | ⭐⭐ | ⭐⭐⭐ | Claude — mantiene coherencia en cambios masivos |
| **Code review automatizado** | ⭐⭐⭐ | ⭐⭐⭐ | Ambos. Gemini por costo a escala |
| **Tests unitarios** | ⭐⭐⭐ | ⭐⭐⭐ | Ambos excelentes. Gemini Flash es más rápido |
| **Análisis de codebase grande** | ⭐⭐⭐ | ⭐⭐ | Gemini — contexto 1M nativo |
| **Debugging complejo** | ⭐⭐ | ⭐⭐⭐ | Claude Opus con Extended Thinking |
| **Documentación técnica** | ⭐⭐⭐ | ⭐⭐⭐ | Ambos. Claude genera prosa más clara |
| **Pipeline CI/CD con IA** | ⭐⭐⭐ | ⭐⭐ | Gemini — Batch API + integración GCP |
| **Análisis de seguridad** | ⭐⭐ | ⭐⭐⭐ | Claude — razonamiento profundo sobre patrones |

#### 🔥 El Stack Óptimo: Workflow Híbrido

La práctica profesional más común en 2026 es **usar ambos** según la tarea:

```
┌────────────────────────────────────────────────────────────────┐
│            WORKFLOW HÍBRIDO GEMINI + CLAUDE                     │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  📋 PLANIFICACIÓN Y DISEÑO                                    │
│  └─→ Claude Opus (Extended Thinking)                           │
│       "Analiza el codebase y propón la arquitectura"           │
│                                                                │
│  ⚡ IMPLEMENTACIÓN DÍA A DÍA                                  │
│  └─→ Gemini CLI (Flash) / Gemini Code Assist                  │
│       "Implementa estos endpoints según el plan"               │
│                                                                │
│  🧪 TESTING Y CALIDAD                                         │
│  └─→ Gemini Flash (generar tests) + Claude Sonnet (review)    │
│       "Genera tests → revisa calidad y edge cases"             │
│                                                                │
│  🔧 REFACTORING COMPLEJO                                      │
│  └─→ Claude Code (Opus)                                        │
│       "Migra este módulo de callbacks a reactive streams"      │
│                                                                │
│  🚀 CI/CD Y AUTOMATIZACIÓN                                    │
│  └─→ Gemini (Batch API + Flash-Lite)                           │
│       "Analiza PRs, genera changelogs, valida cobertura"       │
│                                                                │
│  💡 Resultado: Cada modelo donde brilla más                   │
│     → Optimizas calidad Y costo simultáneamente               │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

### 14.12 Resumen Ejecutivo — Cheat Sheet

```
┌────────────────────────────────────────────────────────────────────────────┐
│              CHEAT SHEET: GEMINI vs CLAUDE PARA DESARROLLADORES            │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  DIMENSIÓN          🔵 GEMINI                🟠 CLAUDE                    │
│  ─────────          ──────────               ──────────                    │
│  Modelo Default     Gemini 3 Flash           Claude Sonnet 4.6            │
│  Modelo Premium     Gemini 3.1 Pro           Claude Opus 4.6              │
│  Contexto Max       1M tokens                200K (1M en Code)            │
│  CLI                Gemini CLI (open-source)  Claude Code (propietario)   │
│  Plugin IDE         Gemini Code Assist        En Cursor/Windsurf          │
│  Config File        GEMINI.md                 CLAUDE.md                   │
│  Sub-Agentes        ✅ (v0.36.0+)            ✅ (nativo)                  │
│  MCP                ✅                        ✅                           │
│  Free Tier          ✅ (generoso)             ❌ ($20/mes mínimo)         │
│  Costo Token(out)   $0.40 - $12.00/1M        $5.00 - $25.00/1M           │
│  Fortaleza #1       Costo + Escala + GCP      Razonamiento + Código       │
│  Fortaleza #2       Contexto largo + Multi.   Sub-agentes + Hooks         │
│  Empresa detrás     Google (DeepMind)          Anthropic                   │
│                                                                            │
│  ⚡ REGLA RÁPIDA:                                                         │
│  → Gemini Flash para velocidad y volumen                                  │
│  → Claude Sonnet para calidad día a día                                   │
│  → Gemini Pro para contexto masivo + GCP                                  │
│  → Claude Opus para razonamiento profundo                                 │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

<p align="center">
    <sub>📖 Documentación mantenida y actualizada continuamente · Última actualización: Abril 2026</sub>
</p>

