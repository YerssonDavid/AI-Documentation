# 🧠 AI Documentation

> Base de conocimiento personal sobre **Inteligencia Artificial**, enfocada en el aprendizaje consciente y la utilización responsable como desarrollador de software.

---

## 📋 ¿Qué es este repositorio?

Este es mi repositorio **privado** de documentación sobre IA. Reúne todo lo que voy aprendiendo, investigando y aplicando sobre inteligencia artificial — no solo la parte técnica (qué es ML, cómo funciona un LLM), sino también **cómo usar la IA de forma responsable** para aprender sin crear dependencia.

No es una wiki genérica. Está escrito desde mi perspectiva como **desarrollador backend Java** y orientado a resolver preguntas concretas:
- ¿Cómo debería usar la IA para estudiar sin engañarme?
- ¿Qué conceptos técnicos necesito entender para integrar IA en mis proyectos?
- ¿Qué instrucciones darle a un asistente de IA para que me ayude a aprender de verdad?

---

## 📁 Estructura del Proyecto

```
AIDocumentation/
│
├── 📄 README.md                          ← Estás aquí
│
├── 🧠 Ai.md                              ← Guía principal de IA
│                                            Fundamentos, 4D Framework,
│                                            ML, Deep Learning, LLMs,
│                                            Prompt Engineering y más
│
├── ⚡ AIDev.md                            ← IA para Desarrollo de Software
│                                            Agentes, Sub-agentes, MCP, A2A,
│                                            RAG, Vibe Coding, Context
│                                            Engineering y frameworks
│
└── 📂 mi_asistant_guide/                 ← Guías de configuración de asistentes IA
    └── AsistantGeneral.md                ← System prompt personalizado para
                                            usar la IA como tutor socrático
```

---

## 📚 Contenido

### 🧠 [`Ai.md`](Ai.md) — Guía Principal (~740 líneas)

La guía central del repositorio. Cubre desde la filosofía de uso hasta los fundamentos técnicos:

| Sección | Contenido |
| --- | --- |
| **Los 4D en la IA** | Framework de uso responsable: Delegar, Descripción, Discernimiento y Diligencia. Qué confiar a la IA, cómo dirigirla, cómo evaluar sus respuestas y cómo mantener la responsabilidad sobre tu trabajo |
| **Los 4D en Aprendizaje** | Los mismos 4D aplicados al contexto educativo. Diferencia entre usar IA para que haga el trabajo por ti vs. usarla para aprender realmente |
| **5 Principios Clave** | Reglas personales: fortalece no debilites, tú al volante, entrenadora no suplente, explicabilidad total, el camino difícil vale la pena |
| **Fundamentos de IA** | Jerarquía IA → ML → DL → GenAI, tipos de IA según capacidad (ANI, AGI, ASI), tipos de aprendizaje (supervisado, no supervisado, por refuerzo) |
| **Machine Learning** | Diferencia entre programación tradicional y ML, algoritmos principales con casos de uso |
| **Deep Learning** | Redes neuronales, arquitectura Transformer, mecanismo de atención |
| **IA Generativa y LLMs** | Modalidades generativas, cómo funciona un LLM internamente, comparativa de modelos 2025-2026 |
| **Prompt Engineering** | Técnicas (Zero-Shot, Few-Shot, Chain-of-Thought, etc.) y el Framework RACE |
| **IA en el Desarrollo** | Herramientas por fase: diseño, codificación, testing, debug, code review, docs, DevOps |
| **Mejores Prácticas** | Qué hacer y qué NO hacer con IA como desarrollador |

---

### ⚡ [`AIDev.md`](AIDev.md) — IA para Desarrollo de Software (~900 líneas)

Guía práctica enfocada 100% en cómo utilizar la IA como herramienta de desarrollo:

| Sección | Contenido |
| --- | --- |
| **Asistentes de Código** | Comparativa de herramientas (Cursor, Copilot, Windsurf, Claude Code), clasificación por tipo y stack profesional 2026 |
| **Agentes de IA** | Anatomía, componentes (LLM, Tools, Memory, Planning), Agent Loop (Observe → Think → Act → Evaluate) |
| **Sub-Agentes y Multi-Agente** | Sistemas con agentes especializados (Coder, Tester, Reviewer) coordinados por un orquestador |
| **Patrones Agénticos** | Orquestador-Worker, Evaluador-Optimizador, Routing, Scatter-Gather |
| **MCP (Model Context Protocol)** | El "USB-C de la IA": cómo los agentes se conectan a herramientas/datos de forma estándar |
| **A2A (Agent-to-Agent)** | Protocolo de comunicación entre agentes, Agent Cards, comparativa con MCP |
| **RAG** | Arquitectura completa de Retrieval-Augmented Generation, tipos y casos de uso para devs |
| **Metodologías** | Vibe Coding, Plan+Execute, TDD con IA, Human-in-the-Loop |
| **Context Engineering** | La evolución del Prompt Engineering: project specs, codebase indexing, AGENTS.md |
| **Frameworks** | LangChain, LangGraph, CrewAI, Spring AI, Vertex AI ADK, vector stores |

---

### 📂 [`mi_asistant_guide/`](mi_asistant_guide/)

Contiene system prompts personalizados para configurar asistentes de IA como tutores efectivos.

#### [`AsistantGeneral.md`](mi_asistant_guide/AsistantGeneral.md)

Mi prompt base para cualquier sesión de estudio con IA. Define:

- **Método Socrático** — La IA pregunta en vez de dar respuestas directas
- **Perfil técnico** — Mi stack (Java, Spring Boot, PostgreSQL), áreas fuertes y débiles
- **Reglas estrictas** — No dar código final, siempre explicar el "por qué", no asumir conocimiento en áreas débiles
- **Orientación profesional** — La IA debe corregirme si propongo herramientas obsoletas o rutas subóptimas

---

## 🎯 Para qué me sirve esto

| Situación | Cómo uso este repo |
| --- | --- |
| Voy a estudiar un tema nuevo de IA | Leo la sección correspondiente en `Ai.md` para tener el marco mental |
| Quiero configurar un asistente IA para estudiar | Copio el prompt de `AsistantGeneral.md` como system prompt |
| Necesito recordar cómo usar IA responsablemente | Reviso los 4D y los 5 Principios |
| Quiero comparar modelos de IA | Consulto la tabla comparativa de LLMs en `Ai.md` |
| Necesito elegir una herramienta de IA para desarrollo | Reviso la comparativa de asistentes en `AIDev.md` |
| Quiero entender agentes y sub-agentes | Leo las secciones 3 y 4 de `AIDev.md` |
| Necesito entender MCP o A2A | Reviso las secciones 6 y 7 de `AIDev.md` |
| Quiero implementar RAG | Leo la sección 8 de `AIDev.md` |
| Quiero elegir una metodología de desarrollo con IA | Reviso Vibe Coding, Plan+Execute, TDD con IA en `AIDev.md` |

---

<p align="center">
    <sub>📖 Documentación personal · Última actualización: Abril 2026</sub>
</p>
