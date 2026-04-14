# 🗺️ Road Camp: De Desarrollador Backend a AI Software Engineer

> 🚀 **Misión:** Dominar la integración de Modelos de Lenguaje Grande (LLMs) en sistemas empresariales reales con **Java & Spring Boot**, priorizando mantenibilidad, escalabilidad y seguridad.

> 💡 **¿Para quién?** Arquitectos y desarrolladores backend Java que quieren construir aplicaciones inteligentes con IA — no chatbots de juguete, sino **sistemas empresariales de producción**.

---

## 📑 Índice

1. [Fase 1: Fundamentos y la Interfaz Primaria](#fase-1-fundamentos-y-la-interfaz-primaria-el-hola-mundo-cognitivo)
2. [Fase 2: El Ecosistema Java y Spring AI](#fase-2-el-ecosistema-java-y-spring-ai-el-chasis-del-vehículo)
3. [Fase 3: Function Calling / Tool Calling](#fase-3-dándole-manos-a-la-ia-function-calling--tool-calling-)
4. [Fase 4: RAG Básico — La Memoria de la Aplicación](#fase-4-rag-básico--la-memoria-de-la-aplicación)
5. [Fase 5: RAG Avanzado y Arquitectura de Datos](#fase-5-rag-avanzado-y-arquitectura-de-datos-optimizando-el-motor)
6. [Fase 6: RAG en Producción — Integración con Spring Boot](#fase-6-rag-en-producción--integración-completa-con-spring-boot)
7. [Fase 7: Agentes Autónomos y Flujos Complejos](#fase-7-agentes-autónomos-y-flujos-complejos-el-cerebro)
8. [Fase 8: LLMOps, Observabilidad y Producción](#fase-8-llmops-observabilidad-y-producción-el-mantenimiento)

---

## 🧭 Mapa de Progresión

```
┌────────────────────────────────────────────────────────────────────────────┐
│              🗺️ MAPA DE PROGRESIÓN — AI SOFTWARE ENGINEER                  │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  FASE 1          FASE 2          FASE 3          FASE 4                    │
│  Fundamentos     Spring AI       Tool Calling    RAG Básico                │
│  ┌──────┐        ┌──────┐        ┌──────┐        ┌──────┐                  │
│  │ 🧠   │───────▶│ ⚙️   │───────▶│ 🔧   │───────▶│ 📚   │                 │
│  │ HTTP │        │ Chat │        │ Func │        │ Vec  │                  │
│  │ +API │        │Client│        │ Call │        │ DB   │                  │
│  └──────┘        └──────┘        └──────┘        └──────┘                  │
│  ~1 semana       ~1 semana       ~1 semana       ~2 semanas                │
│                                                                            │
│  FASE 5          FASE 6          FASE 7          FASE 8                    │
│  RAG Avanzado     RAG+Spring     Agentes         LLMOps                    │
│  ┌──────┐        ┌──────┐        ┌──────┐        ┌──────┐                  │
│  │ 🔬   │───────▶│ 🏗️   │───────▶│ 🤖   │───────▶│ 📊   │                 │
│  │Rerank│        │ Prod │        │ ReAct│        │ Obs  │                  │
│  │Graph │        │ Arch │        │Agent │        │ Cost │                  │
│  └──────┘        └──────┘        └──────┘        └──────┘                  │
│  ~2 semanas      ~2 semanas      ~2 semanas      ~1 semana                 │
│                                                                            │
│  ─────────────────────────────────────────────────────────────             │
│  📊 Tiempo total estimado: 10–12 semanas (ritmo constante)                 │
│  🎯 Resultado: Capacidad de diseñar, construir y operar                    │
│     sistemas empresariales con IA en Spring Boot                           │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Requisitos Previos

Antes de empezar, asegúrate de tener una base sólida en:

| Requisito         | Nivel Mínimo        | ¿Por qué?                                                       |
| ----------------- | ------------------- | --------------------------------------------------------------- |
| **Java 17+**      | Intermedio-Avanzado | Records, sealed classes, HttpClient moderno                     |
| **Spring Boot 3** | Intermedio          | DI, REST, autoconfiguración, profiles                           |
| **Docker**        | Básico              | Para levantar bases de datos vectoriales y servicios auxiliares |
| **REST APIs**     | Intermedio          | Consumir y exponer APIs HTTP, manejo de JSON                    |
| **SQL / JPA**     | Básico              | Para integrar pgvector y entender la persistencia               |
| **Git**           | Básico              | Versionamiento del proyecto a lo largo del roadcamp             |

> [!TIP]
> Si alguno de estos puntos te genera dudas, **no te detengas**. La práctica del roadcamp reforzará estos conocimientos progresivamente.

---

## Fase 1: Fundamentos y la Interfaz Primaria (El "Hola Mundo" Cognitivo)

> 🎯 **Objetivo:** Entender cómo se comunica un LLM a bajo nivel, antes de usar frameworks mágicos. Es como entender SQL antes de usar Hibernate.

### 1.1 Anatomía de una Petición LLM (Tokens, Contexto y Modelos)

**Concepto:** Los LLMs no leen palabras, leen **"tokens"** (fragmentos de palabras). Tienen una **"ventana de contexto"** (cuántos tokens pueden recordar a la vez) y **no tienen estado** — son stateless, cada petición HTTP es aislada, como el protocolo HTTP mismo.

> 💡 **Analogía:** Imagina un pez dorado súper inteligente. Resuelve problemas complejos, pero su memoria dura 5 segundos. En cada interacción, debes recordarle **quién es** y **de qué estaban hablando**.

**Conceptos clave que debes dominar:**

| Concepto                | Descripción                                              | Impacto Práctico                                |
| ----------------------- | -------------------------------------------------------- | ----------------------------------------------- |
| **Token**               | Fragmento de ~4 caracteres del texto                     | Determina el **costo** de cada llamada a la API |
| **Ventana de contexto** | Máximo de tokens que el modelo puede procesar            | Limita cuánta información puedes enviar/recibir |
| **Temperature**         | Control de aleatoriedad (0 = determinista, 1 = creativo) | Afecta la **consistencia** de las respuestas    |
| **Top-p / Top-k**       | Filtro de probabilidad de tokens candidatos              | Control fino sobre la calidad de generación     |
| **Stop sequences**      | Tokens que detienen la generación                        | Evitar respuestas excesivamente largas          |

```
┌────────────────────────────────────────────────────────────────┐
│              ANATOMÍA DE UNA PETICIÓN LLM                       │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Tu Aplicación Java                                            │
│  ┌───────────────────────────────────────────────┐             │
│  │  POST /v1/chat/completions                    │             │
│  │                                               │             │
│  │  {                                            │             │
│  │    "model": "gpt-4o",                         │             │
│  │    "messages": [                              │             │
│  │      { "role": "system",   ← Instrucciones    │             │
│  │        "content": "Eres un extractor..." },   │             │
│  │      { "role": "user",     ← Input del usuario│             │
│  │        "content": "Texto a procesar..." }     │             │
│  │    ],                                         │             │
│  │    "temperature": 0.2,     ← Precisión alta   │             │
│  │    "max_tokens": 500       ← Límite de salida │             │
│  │  }                                            │             │
│  └───────────────────────────────────────────────┘             │
│                      │                                         │
│                      ▼                                         │
│  Respuesta JSON                                                │
│  ┌───────────────────────────────────────────────┐             │
│  │  {                                            │             │
│  │    "choices": [{ "message": { ... } }],       │             │
│  │    "usage": {                                 │             │
│  │      "prompt_tokens": 85,    ← Lo que enviaste│             │
│  │      "completion_tokens": 42, ← Lo que generó │             │
│  │      "total_tokens": 127     ← Lo que PAGAS   │             │
│  │    }                                          │             │
│  │  }                                            │             │
│  └───────────────────────────────────────────────┘             │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Crea un script usando `HttpClient` de Java 11+ que haga un `POST` directo a la API de OpenAI (o Groq/Gemini). Pídele que resuma un texto. Observa la respuesta JSON cruda, enfocándote en el campo `usage` (`prompt_tokens`, `completion_tokens`). Experimenta cambiando la `temperature` entre `0.0` y `1.0` y compara los resultados.

---

### 1.2 Prompt Engineering Estructural para Backend

**Concepto:** En código, **no escribes prompts como un usuario final** ("Hazme un poema"). Divides el prompt en **roles**: `System` (instrucciones del sistema/personalidad), `User` (la entrada del usuario) y aplicas técnicas como **Few-Shot Prompting** (darle ejemplos de entrada/salida esperada).

> 💡 **Analogía:** El `System Prompt` es la **descripción de cargo** en un contrato laboral. El `User Prompt` es la **tarea diaria** que le asignas.

```
┌────────────────────────────────────────────────────────────────┐
│           TÉCNICAS DE PROMPTING PARA BACKEND                   │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  🎯 ZERO-SHOT (Sin ejemplos)                                   │
│  System: "Extrae fechas del texto en formato YYYY-MM-DD"       │
│  User: "Quiero reservar 2 noches para mañana"                  │
│  → Funciona para tareas simples y claras                       │
│                                                                │
│  📝 FEW-SHOT (Con ejemplos)                                    │
│  System: "Extrae datos de facturas como JSON..."               │
│  User: "Ejemplo 1: 'Factura #123...' → {proveedor:..}"       │
│         "Ejemplo 2: 'Cobro por...' → {proveedor:..}"           │
│         "Ahora procesa: 'Recibo de pago #456...'"            │
│  → Mejor para formatos estructurados y consistentes            │
│                                                                │
│  🔗 CHAIN-OF-THOUGHT (Razonamiento paso a paso)                │
│  System: "Analiza paso a paso antes de responder."             │
│  User: "¿Este código tiene un SQL Injection?"                  │
│  → Ideal para análisis complejos y detección de errores        │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Crea un endpoint REST que reciba un texto libre (ej. "Quiero reservar 2 noches para mañana"). Usando llamadas HTTP puras, haz que el LLM actúe como un **extractor de fechas**. El `System Prompt` debe obligarlo a devolver solo formato `YYYY-MM-DD`. Implementa al menos las técnicas Zero-Shot y Few-Shot y compara los resultados.

---

## Fase 2: El Ecosistema Java y Spring AI (El Chasis del Vehículo)

> 🎯 **Objetivo:** Dejar las llamadas HTTP manuales y adoptar el estándar empresarial con Spring AI. Es la abstracción profesional para producción.

### 2.1 Abstracción de Modelos y ChatClient

**Concepto:** Spring AI abstrae las APIs de OpenAI, Google, Anthropic, etc., detrás de una **interfaz común** (`ChatClient`). Aplicamos el principio de **Inversión de Control** para cambiar de IA sin cambiar la lógica de negocio.

> 💡 **Analogía:** Es el **JDBC de la Inteligencia Artificial**. No te importa si por debajo corre MySQL o PostgreSQL, usas los mismos métodos de Java.

```
┌────────────────────────────────────────────────────────────────┐
│           SPRING AI — ABSTRACCIÓN DE MODELOS                   │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Tu Código Java (NUNCA cambia)                                 │
│  ┌────────────────────────────────────────────────┐            │
│  │  @RestController                               │            │
│  │  class ChatController {                        │            │
│  │                                                │            │
│  │    private final ChatClient chatClient;        │            │
│  │                                                │            │
│  │    String chat(@RequestBody String msg) {      │            │
│  │      return chatClient.prompt()                │            │
│  │        .user(msg)                              │            │
│  │        .call()                                 │            │
│  │        .content();                             │            │
│  │    }                                           │            │
│  │  }                                             │            │
│  └─────────────────────┬──────────────────────────┘            │
│                        │ ← Interfaz común                      │
│           ┌────────────┼────────────┐                          │
│           │            │            │                          │
│     ┌─────▼────┐ ┌─────▼────┐ ┌────▼─────┐                     │
│     │ OpenAI   │ │ Gemini   │ │ Anthropic│                     │
│     │ Starter  │ │ Starter  │ │ Starter  │                     │
│     └──────────┘ └──────────┘ └──────────┘                     │
│     Solo cambias   Solo cambias   Solo cambias                 │
│     application    application    application                  │
│     .yml           .yml           .yml                         │
│                                                                │
│  ✅ Principio: Inversión de Dependencias (DIP)                 │
│  ✅ Tu lógica de negocio NUNCA se acopla a un proveedor        │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Configura un proyecto Spring Boot con `spring-ai-openai-spring-boot-starter`. Inyecta el `ChatClient` y crea un `@RestController` `/api/chat`. Llama al endpoint, luego cambia tu `application.yml` para usar Gemini o Anthropic y **verifica que el código Java no tuvo que modificarse**.

---

### 2.2 Salidas Estructuradas (Structured Output / Converters)

**Concepto:** En Java necesitamos **Objetos** (POJOs o Records), no texto libre. Esta técnica fuerza al LLM a devolver un JSON que mapea exactamente con tus clases de Java.

> 💡 **Analogía:** Es un serializador/deserializador (como Jackson), pero que además es capaz de **"entender"** y extraer la información del desorden para armar el objeto.

```
┌────────────────────────────────────────────────────────────────┐
│        STRUCTURED OUTPUT — DEL CAOS AL OBJETO JAVA             │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Input (correo desordenado):                                   │
│  ┌──────────────────────────────────────────────┐              │
│  │ "Hola, le adjunto la factura de Acme Corp    │              │
│  │  por el servicio de hosting. El total es     │              │
│  │  $1,250.00 USD. Incluye: servidor dedicado,  │              │
│  │  SSL premium y soporte 24/7. Gracias!"       │              │
│  └──────────────────────────────────────────────┘              │
│                         │                                      │
│                    Spring AI                                   │
│                  BeanOutputConverter                           │
│                         │                                      │
│                         ▼                                      │
│  Output (Record de Java):                                      │
│  ┌──────────────────────────────────────────────┐              │
│  │ record ResumenFactura(                       │              │
│  │   String proveedor,      // "Acme Corp"      │              │
│  │   Double montoTotal,     // 1250.00          │              │
│  │   String moneda,         // "USD"            │              │
│  │   List<String> items     // ["servidor...",  │              │
│  │ ) {}                     //  "SSL", "soporte"]│             │
│  └──────────────────────────────────────────────┘              │
│                                                                │
│  ✅ Tipo-safe, validable, listo para tu lógica de negocio      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Crea un `record` en Java `ResumenFactura(String proveedor, Double montoTotal, List<String> items)`. Crea un endpoint que reciba el texto de un correo electrónico desordenado de un cobro. Usa el `BeanOutputConverter` de Spring AI para que el LLM lea el correo y devuelva directamente el objeto `ResumenFactura` instanciado en Java.

---

## Fase 3: Dándole "Manos" a la IA (Function Calling / Tool Calling) 🚨

> 🎯 **Objetivo:** Este es el **punto de inflexión** donde dejas de hacer chatbots y empiezas a hacer **sistemas inteligentes**. El LLM pasa de ser un generador de texto a un **orquestador de operaciones**.

> [!IMPORTANT]
> **Function Calling es la habilidad más crítica** de un AI Software Engineer. Sin ella, tu IA solo puede hablar. Con ella, tu IA puede **actuar** sobre sistemas reales.

### 3.1 Concepto y Registro de Funciones

**Concepto:** El LLM detecta que le falta información (ej. el clima actual, el saldo de un usuario) y en lugar de responder, te devuelve un JSON diciendo: _"Por favor, ejecuta tu método X con estos parámetros Y"_. **Tu código** ejecuta la función y le devuelve el resultado al LLM para que formule la respuesta final.

> 💡 **Analogía:** Eres el **gerente** (Java). El LLM es tu **asistente**. El asistente te dice: _"Jefe, para responderle al cliente necesito que usted entre al sistema de contabilidad y me pase el saldo de la cuenta 123"_. Tú lo haces y le devuelves el saldo para que él redacte la respuesta final.

```
┌────────────────────────────────────────────────────────────────┐
│              FLUJO DE FUNCTION CALLING                         │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  1. Usuario:  "¿Dónde está mi pedido 555?"                     │
│                     │                                          │
│  2. LLM analiza:    ▼                                          │
│     "Necesito información que no tengo.                        │
│      Veo que existe una función llamada                        │
│      'estadoPedidoFunction'. La usaré."                        │
│                     │                                          │
│  3. LLM devuelve:   ▼                                          │
│     { "function": "estadoPedido",                              │
│       "arguments": { "pedidoId": "555" } }                     │
│                     │                                          │
│  4. Spring AI       ▼     ┌────────────────────┐               │
│     intercepta ──────────▶│ Tu método Java     │               │
│     y ejecuta             │ @Bean + @Description│              │
│                           │ estadoPedido(555)  │               │
│                           └────────┬───────────┘               │
│                                    │                           │
│  5. Resultado:              "En camino — llega mañana"         │
│                                    │                           │
│  6. LLM recibe               ▼                                 │
│     el dato y formula:                                         │
│     "Su pedido #555 está en camino y                         │
│      llegará mañana. ¿Necesita algo más?"                      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

### 3.2 Múltiples Funciones y Encadenamiento

**Concepto avanzado:** Un LLM puede invocar **múltiples funciones en cadena** en una sola conversación. Puede llamar a `getUser()`, luego a `getOrders(userId)`, luego a `getShippingStatus(orderId)`, construyendo contexto progresivamente.

| Escenario                   | Functions Necesarias                                                                     | Complejidad |
| --------------------------- | ---------------------------------------------------------------------------------------- | ----------- |
| Consultar estado de pedido  | `getOrderStatus(id)`                                                                     | Baja        |
| Transferencia entre cuentas | `getBalance(from)`, `transfer(from, to, amount)`                                         | Media       |
| Análisis de servidor        | `getLogs(service)`, `getMetrics(service)`, `restart(service)`                            | Alta        |
| Reserva de viaje completa   | `searchFlights()`, `searchHotels()`, `bookFlight()`, `bookHotel()`, `sendConfirmation()` | Muy Alta    |

**💻 Ejercicio Práctico:**

Crea un método en Spring anotado con `@Bean` y `@Description("Obtiene el estado de un pedido dado su ID")` que devuelva un `String` (simulando una BD). Configura el `ChatClient` para habilitar esta función (`.functions("estadoPedidoFunction")`). Habla con la IA preguntando _"¿Dónde está mi pedido 555?"_. Observa en los logs cómo Spring intercepta, llama a tu Java de fondo y le devuelve el dato al LLM.

---

## Fase 4: RAG Básico — La Memoria de la Aplicación

> 🎯 **Objetivo:** Los LLMs no conocen tu código ni tus bases de datos privadas. Aquí le enseñamos a **buscar en tus datos** antes de responder.

> [!NOTE]
> RAG (Retrieval-Augmented Generation) es probablemente el **patrón más utilizado en producción** para aplicaciones empresariales con IA. Si solo pudieras dominar una cosa de este roadcamp, debería ser RAG.

### 4.1 Embeddings y Espacios Vectoriales

**Concepto:** Un modelo de Embedding transforma texto (una frase, un documento) en un **array de miles de números decimales** (un vector). Textos con significado similar terminan siendo vectores que están **físicamente cerca** en un espacio matemático.

> 💡 **Analogía:** Imagina una gran biblioteca donde los libros **no se ordenan alfabéticamente, sino por "temática"**. Los libros de terror están en la esquina oscura, los de romance en el centro. El embedding son las **coordenadas (X, Y, Z)** del libro en esa biblioteca.

```
┌────────────────────────────────────────────────────────────────┐
│           EMBEDDINGS — REPRESENTACIÓN VECTORIAL                 │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Texto                          Vector (simplificado)          │
│  ─────                          ───────────────────            │
│  "Me gusta el fútbol"    →     [0.82, 0.15, 0.91, ...]       │
│  "Amo el balompié"       →     [0.80, 0.17, 0.89, ...]  ← ¡Cerca!
│  "El perro ladra"        →     [0.12, 0.95, 0.03, ...]  ← Lejos
│                                                                │
│  Similitud del coseno:                                         │
│  fútbol ↔ balompié  = 0.97  ← ¡Altamente similares!          │
│  fútbol ↔ perro     = 0.15  ← Muy diferentes                 │
│                                                                │
│  📐 Aunque "fútbol" y "balompié" NO comparten palabras,        │
│     sus vectores son CASI idénticos porque significan           │
│     lo mismo. ESA es la magia de los embeddings.               │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Toma tres oraciones: _"Me gusta el fútbol"_, _"Amo el balompié"_, _"El perro ladra"_. Pásalas por la API de Embeddings de OpenAI. Escribe un método en Java que calcule la **similitud del coseno** (Cosine Similarity) entre los tres arrays. Comprueba matemáticamente que las dos primeras frases "están más cerca" aunque no comparten palabras.

---

### 4.2 Vector Databases (Bases de Datos Vectoriales)

**Concepto:** Las bases de datos relacionales no sirven para buscar por **"similitud de significado"**. Usamos **Vector Stores** (Pinecone, Milvus, o la extensión `pgvector` en PostgreSQL) para guardar y consultar rápidamente los embeddings.

> 💡 **Analogía:** Es un índice de base de datos especializado, pero en lugar de buscar coincidencias exactas (`WHERE id = 5`), busca **"vecinos más cercanos"** (`ORDER BY distance LIMIT 5`).

```
┌────────────────────────────────────────────────────────────────┐
│        BASE DE DATOS RELACIONAL vs VECTORIAL                   │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  🗃️ SQL Tradicional              📐 Vector Store              │
│  ──────────────────              ──────────────                │
│  SELECT * FROM products         SELECT * FROM embeddings       │
│  WHERE category = 'ropa'        ORDER BY cosine_distance(      │
│  AND price < 100;                 query_vector, embedding)     │
│                                  LIMIT 5;                      │
│                                                                │
│  → Coincidencia EXACTA          → Similitud SEMÁNTICA          │
│  → "ropa" debe estar literal    → "algo para el frío" →        │
│  → No entiende sinónimos          encuentra "chaqueta térmica" │
│                                                                │
│  Opciones para Spring Boot:                                    │
│  ┌──────────────────────────────────────────────────────┐      │
│  │ • PgVector (PostgreSQL)  ← Mejor para empezar        │      │
│  │ • Chroma               ← Ligero, desarrollo local    │      │
│  │ • Pinecone             ← SaaS, escalable             │      │
│  │ • Milvus               ← Enterprise, alto volumen    │      │
│  │ • Weaviate             ← GraphQL + vectores          │      │
│  │ • Redis Vector Search  ← Si ya usas Redis            │      │
│  └──────────────────────────────────────────────────────┘      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Levanta un contenedor Docker de PostgreSQL con `pgvector`. Configura `PgVectorStore` en Spring Boot. Guarda 10 descripciones de productos ficticios como embeddings en la BD. Luego, crea un endpoint de búsqueda que reciba _"algo para el frío"_ y te devuelva la descripción de _"Chaqueta térmica"_ usando búsqueda por similitud.

---

### 4.3 Chunking y RAG (Retrieval-Augmented Generation) Básico

**Concepto:** No puedes enviar un manual de 500 páginas al LLM para que te responda una pregunta (cuesta mucho dinero y se confunde). **Divides** el PDF en "chunks" (trozos), los vectorizas, buscas los trozos relevantes, y **solo esos trozos** se los pasas al LLM como contexto: _"Responde basado solo en esto..."_.

> 💡 **Analogía:** Estudiar para un examen a **libro abierto**. No te lees todo el libro en el examen. Usas el **índice** para encontrar el párrafo relevante, lo lees y redactas tu respuesta.

```
┌────────────────────────────────────────────────────────────────┐
│              FLUJO RAG COMPLETO                                │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  📥 INGESTIÓN (offline, una vez)                               │
│                                                                │
│  PDF/TXT ──▶ Chunking ──▶ Embedding ──▶ Vector Store           │
│  500 págs    Trozos de     Array de       PostgreSQL           │
│              500 tokens    1536 floats    + pgvector           │
│                                                                │
│  🔍 CONSULTA (runtime, por cada pregunta)                      │
│                                                                │
│  "¿Cuántos días     Embedding      Búsqueda       Top 3        │
│   de vacaciones ──▶ de la     ──▶ vectorial  ──▶ chunks        │
│   tengo?"          pregunta       (coseno)       relevantes    │
│                                                                │
│       ┌──────────────────────────────────────────┐             │
│       │ Prompt Enriquecido:                      │             │
│       │                                          │             │
│       │ "Basándote SOLO en el siguiente contexto:│             │
│       │  [chunk 1] [chunk 2] [chunk 3]           │             │
│       │                                          │             │
│       │  Responde: ¿Cuántos días de vacaciones   │             │
│       │  tengo?"                                 │             │
│       └─────────────────┬────────────────────────┘             │
│                         │                                      │
│                         ▼                                      │
│                    ┌─────────┐                                 │
│                    │   LLM   │ → "Según la política de la      │
│                    └─────────┘    empresa, tienes 15 días      │
│                                   hábiles de vacaciones..."    │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**Estrategias de Chunking:**

| Estrategia                 | Tamaño                          | Mejor Para               | Riesgo                     |
| -------------------------- | ------------------------------- | ------------------------ | -------------------------- |
| **Por tokens fijos**       | 500-1000 tokens                 | Documentos homogéneos    | Corta en medio de una idea |
| **Por párrafos/secciones** | Variable                        | Documentos estructurados | Chunks muy desiguales      |
| **Con overlap**            | 500 tokens + 50 de solapamiento | General (recomendado)    | Duplicación de información |
| **Semántico**              | Variable, por significado       | Documentos técnicos      | Más complejo, más lento    |

**💻 Ejercicio Práctico:**

Usa el `DocumentReader` de Spring AI para leer un archivo `.txt` con políticas de una empresa inventada. Aplica el `TokenTextSplitter` para dividirlo en fragmentos de 500 tokens. Guárdalos en tu base vectorial. Haz una consulta (_"¿Cuántos días de vacaciones tengo?"_) que pase por el `QuestionAnswerAdvisor` para darte una respuesta fundamentada en el texto.

---

## Fase 5: RAG Avanzado y Arquitectura de Datos (Optimizando el Motor)

> 🎯 **Objetivo:** El RAG básico falla en producción porque los PDFs son complejos (tablas, código, jerarquías). Aquí aprendes a hacer un RAG **robusto y preciso**.

### 5.1 Re-Ranking y Filtrado por Metadatos

**Concepto:** La búsqueda vectorial a veces trae **resultados basura**. Un **Re-ranker** (un modelo especializado) toma los resultados de la base de datos y los re-ordena basándose en qué tan bien responden realmente a la pregunta. Además, se deben usar **metadatos** (etiquetas como `tenant_id`, `fecha`) para hacer **pre-filtros híbridos** (Vectorial + SQL tradicional).

> 💡 **Analogía:** La búsqueda vectorial trae a los **10 mejores candidatos** para un puesto. El Re-ranker es la **entrevista final** donde recursos humanos descarta a los que mintieron en el currículum.

```
┌────────────────────────────────────────────────────────────────┐
│              BÚSQUEDA HÍBRIDA + RE-RANKING                     │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Query: "zapatos elegantes baratos"                            │
│                │                                               │
│                ▼                                               │
│  ┌──────────────────────────────────┐                          │
│  │ PRE-FILTRO (SQL tradicional)     │                          │
│  │ WHERE categoria = 'calzado'      │                          │
│  │ AND precio < 100                 │                          │
│  │ AND activo = true                │                          │
│  └─────────────┬────────────────────┘                          │
│                │ 150 resultados                                │
│                ▼                                               │
│  ┌──────────────────────────────────┐                          │
│  │ BÚSQUEDA VECTORIAL (semántica)   │                          │
│  │ cosine_similarity(query, docs)   │                          │
│  │ TOP 20                           │                          │
│  └─────────────┬────────────────────┘                          │
│                │ 20 candidatos                                 │
│                ▼                                               │
│  ┌──────────────────────────────────┐                          │
│  │ RE-RANKER (modelo de precisión)  │                          │
│  │ Reordena por relevancia REAL     │                          │
│  │ TOP 5                            │                          │
│  └─────────────┬────────────────────┘                          │
│                │ 5 mejores resultados                          │
│                ▼                                               │
│  → Contexto de alta calidad para el LLM                        │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Modifica el ejercicio de los productos (4.2). Agrega a cada documento el metadato `"categoría"` y `"precio"`. Implementa una consulta que busque _"zapatos elegantes"_ (búsqueda semántica) **PERO** forzando un filtro a nivel de `VectorStore` donde `precio < 100` y `categoría = "Ropa"`.

---

### 5.2 GraphRAG Básico (Knowledge Graphs)

**Concepto:** Cuando los datos tienen relaciones complejas entre sí (personas, organizaciones, eventos), la búsqueda vectorial simple no es suficiente. **GraphRAG** extrae entidades y relaciones para búsquedas de **contexto amplio** ("multi-hop") usando grafos de conocimiento.

> 💡 **Analogía:** El mapa mental de conceptos conectados. En vez de buscar "un libro en la biblioteca", trazas los caminos entre ideas: _Apple → LANZA → iPhone → COMPITE_CON → Galaxy_.

```
┌────────────────────────────────────────────────────────────────┐
│              GRAPHRAG — DATOS CONECTADOS                       │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  RAG Tradicional (Vector):     GraphRAG (Grafo):               │
│  ────────────────────────     ──────────────────               │
│  "Buscar párrafos que          "Trazar conexiones              │
│   hablen de Apple"              entre Apple, iPhone,           │
│                                  Tim Cook, iOS..."             │
│                                                                │
│      ┌──────────┐                                              │
│      │  Apple   │                                              │
│      └────┬─────┘                                              │
│           │ LANZA                                              │
│      ┌────▼─────┐     TIENE_CEO    ┌──────────┐                │
│      │ iPhone   │◄────────────────│ Tim Cook  │                │
│      └────┬─────┘                  └──────────┘                │
│           │ CORRE                                              │
│      ┌────▼─────┐     COMPITE      ┌──────────┐                │
│      │   iOS    │─────────────────▶│ Android  │                │
│      └──────────┘                  └──────────┘                │
│                                                                │
│  Query: "¿Quién lidera la empresa del iPhone?"                 │
│  → Traza: iPhone ← LANZA ← Apple → TIENE_CEO → Tim Cook        │
│  → Respuesta: "Tim Cook lidera Apple, la empresa del iPhone"   │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico (Reto):**

Levanta una BD Neo4j local. Usa un LLM para procesar 3 noticias cortas de tecnología y que devuelva POJOs que representen `Entidad`, `Relacion`, `Entidad_Destino` (ej. `Apple -> LANZA -> iPhone`). Usa Spring Data Neo4j para guardar esto en el grafo y visualízalo en la interfaz de Neo4j.

---

## Fase 6: RAG en Producción — Integración Completa con Spring Boot

> 🎯 **Objetivo:** Llevar RAG de un ejercicio local a un **sistema de producción** real con Spring Boot. Aprender la arquitectura, configuración y patrones empresariales para construir pipelines RAG robustos, escalables y mantenibles.

> [!IMPORTANT]
> Esta fase es la **unión de todo lo aprendido**. Aquí dejas de experimentar y empiezas a construir un sistema RAG que podrías desplegar en producción con confianza.

### 6.1 Arquitectura RAG Empresarial con Spring Boot

**Concepto:** Una aplicación RAG en producción no es solo un `Controller` + `VectorStore`. Es una arquitectura completa que integra ingestión de documentos, almacenamiento vectorial, cadena de recuperación, generación aumentada, caché, seguridad multi-tenant y observabilidad — todo orquestado dentro del ecosistema Spring.

```
┌────────────────────────────────────────────────────────────────────────────┐
│         ARQUITECTURA RAG EMPRESARIAL — SPRING BOOT                         │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                     🌐 CAPA DE PRESENTACIÓN                         │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────────┐  │   │
│  │  │ REST API     │  │ WebSocket    │  │ Swagger/OpenAPI          │  │   │
│  │  │ /api/chat    │  │ (streaming)  │  │ Documentación auto      │  │   │
│  │  │ /api/ingest  │  │              │  │                          │  │   │
│  │  └──────┬───────┘  └──────┬───────┘  └──────────────────────────┘  │   │
│  └─────────┼─────────────────┼────────────────────────────────────────┘   │
│            │                 │                                             │
│  ┌─────────▼─────────────────▼────────────────────────────────────────┐   │
│  │                     ⚙️ CAPA DE SERVICIO                             │   │
│  │                                                                     │   │
│  │  ┌──────────────────┐  ┌──────────────────┐  ┌─────────────────┐  │   │
│  │  │ ChatService      │  │ IngestionService │  │ SearchService   │  │   │
│  │  │                  │  │                  │  │                 │  │   │
│  │  │ • Prompt build   │  │ • Doc reading    │  │ • Hybrid search │  │   │
│  │  │ • Context enrich │  │ • Chunking       │  │ • Re-ranking    │  │   │
│  │  │ • LLM call       │  │ • Embedding      │  │ • Metadata      │  │   │
│  │  │ • Response parse │  │ • Storing         │  │   filtering    │  │   │
│  │  └──────┬───────────┘  └──────┬───────────┘  └──────┬──────────┘  │   │
│  └─────────┼─────────────────────┼─────────────────────┼─────────────┘   │
│            │                     │                     │                   │
│  ┌─────────▼─────────────────────▼─────────────────────▼─────────────┐   │
│  │                  🧠 CAPA DE IA (Spring AI)                         │   │
│  │                                                                     │   │
│  │  ┌──────────────┐  ┌───────────────┐  ┌────────────────────────┐  │   │
│  │  │ ChatClient   │  │ EmbeddingModel│  │ Advisors               │  │   │
│  │  │ (LLM calls)  │  │ (vectorizar)  │  │ • QuestionAnswerAdvisor│  │   │
│  │  │              │  │               │  │ • ChatMemoryAdvisor    │  │   │
│  │  │              │  │               │  │ • SafeGuardAdvisor     │  │   │
│  │  └──────────────┘  └───────────────┘  └────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│            │                     │                                         │
│  ┌─────────▼─────────────────────▼────────────────────────────────────┐   │
│  │                  💾 CAPA DE DATOS                                    │   │
│  │                                                                     │   │
│  │  ┌──────────────┐  ┌───────────────┐  ┌────────────────────────┐  │   │
│  │  │ PostgreSQL   │  │ Redis         │  │ Object Storage         │  │   │
│  │  │ + pgvector   │  │ (caché +      │  │ (docs originales:      │  │   │
│  │  │ (embeddings  │  │  sesiones)    │  │  S3 / GCS / MinIO)     │  │   │
│  │  │  + metadata) │  │               │  │                        │  │   │
│  │  └──────────────┘  └───────────────┘  └────────────────────────┘  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

### 6.2 Configuración del Proyecto Spring Boot + Spring AI + RAG

**Concepto:** La configuración correcta de dependencias, propiedades y beans es la base de una aplicación RAG sólida. Spring AI integra todo mediante autoconfiguración, pero para producción necesitas entender cada pieza.

**Dependencias clave en `pom.xml`:**

```xml
<!-- Spring AI BOM — Gestiona versiones de todas las dependencias de Spring AI -->
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.ai</groupId>
            <artifactId>spring-ai-bom</artifactId>
            <version>1.0.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>

<dependencies>
    <!-- Core: ChatClient + abstracción de modelos -->
    <dependency>
        <groupId>org.springframework.ai</groupId>
        <artifactId>spring-ai-openai-spring-boot-starter</artifactId>
    </dependency>

    <!-- Vector Store: PostgreSQL + pgvector -->
    <dependency>
        <groupId>org.springframework.ai</groupId>
        <artifactId>spring-ai-pgvector-store-spring-boot-starter</artifactId>
    </dependency>

    <!-- Document Readers: PDF, TIKA (múltiples formatos) -->
    <dependency>
        <groupId>org.springframework.ai</groupId>
        <artifactId>spring-ai-tika-document-reader</artifactId>
    </dependency>

    <!-- Advisors: QuestionAnswer, Memory, etc. -->
    <dependency>
        <groupId>org.springframework.ai</groupId>
        <artifactId>spring-ai-advisors</artifactId>
    </dependency>
</dependencies>
```

**Configuración en `application.yml`:**

```yaml
spring:
  ai:
    # --- Modelo de Chat (LLM principal) ---
    openai:
      api-key: ${OPENAI_API_KEY}
      chat:
        options:
          model: gpt-4o
          temperature: 0.3           # Baja para respuestas consistentes
          max-tokens: 1000
      embedding:
        options:
          model: text-embedding-3-small  # Modelo de embeddings

    # --- Vector Store (pgvector) ---
    vectorstore:
      pgvector:
        index-type: HNSW              # Índice de búsqueda rápida
        distance-type: COSINE_DISTANCE # Similitud del coseno
        dimensions: 1536               # Debe coincidir con el modelo de embedding
        schema-validation: true

  # --- Base de datos PostgreSQL ---
  datasource:
    url: jdbc:postgresql://localhost:5432/ragdb
    username: ${DB_USER}
    password: ${DB_PASSWORD}
```

> [!TIP]
> Usa **variables de entorno** (`${OPENAI_API_KEY}`) para las credenciales. Nunca hardcodees API keys en el código o en archivos YAML que se commiteen al repositorio.

---

### 6.3 Pipeline de Ingestión de Documentos

**Concepto:** La ingestión es el proceso de **preparar tus datos** para que sean consultables por RAG. Es un pipeline de 4 etapas: lectura → transformación → embedding → almacenamiento. La calidad de tu RAG depende directamente de la calidad de tu ingestión.

```java
/**
 * Servicio de ingestión de documentos para el pipeline RAG.
 * 
 * Responsabilidades:
 * - Leer documentos de múltiples formatos (PDF, TXT, DOCX, HTML)
 * - Dividirlos en chunks optimizados para búsqueda semántica
 * - Enriquecer con metadatos para filtrado posterior
 * - Almacenar embeddings en el Vector Store
 */
@Service
@Slf4j
public class DocumentIngestionService {

    private final VectorStore vectorStore;

    // --- Etapa 1: LECTURA de documentos ---
    public List<Document> readDocuments(Resource resource) {
        // TikaDocumentReader soporta: PDF, DOCX, HTML, TXT, etc.
        var reader = new TikaDocumentReader(resource);
        return reader.get();
    }

    // --- Etapa 2: CHUNKING (división inteligente) ---
    public List<Document> splitDocuments(List<Document> documents) {
        var splitter = new TokenTextSplitter(
            500,    // defaultChunkSize: tokens por chunk
            100,    // minChunkSizeChars: mínimo de caracteres
            20,     // minChunkLengthToEmbed: mínimo para vectorizar
            1000,   // maxNumChunks: máximo de chunks por documento
            true    // keepSeparator: mantener separadores
        );
        return splitter.apply(documents);
    }

    // --- Etapa 3: ENRIQUECIMIENTO con metadatos ---
    public List<Document> enrichWithMetadata(List<Document> docs, 
                                              String tenantId, 
                                              String category) {
        docs.forEach(doc -> {
            doc.getMetadata().put("tenant_id", tenantId);  // Multi-tenant
            doc.getMetadata().put("category", category);    // Clasificación
            doc.getMetadata().put("ingested_at",            // Auditoría
                Instant.now().toString());
        });
        return docs;
    }

    // --- Etapa 4: ALMACENAMIENTO en Vector Store ---
    public void storeDocuments(List<Document> documents) {
        // Spring AI automáticamente:
        // 1. Genera embeddings con el EmbeddingModel configurado
        // 2. Guarda vector + texto + metadatos en pgvector
        vectorStore.add(documents);
        log.info("Ingested {} document chunks", documents.size());
    }

    // --- Pipeline completo ---
    public void ingestDocument(Resource resource, String tenantId, 
                               String category) {
        var docs = readDocuments(resource);
        var chunks = splitDocuments(docs);
        var enriched = enrichWithMetadata(chunks, tenantId, category);
        storeDocuments(enriched);
    }
}
```

---

### 6.4 Servicio de Consulta RAG con Advisors

**Concepto:** Spring AI usa el patrón **Advisor** para inyectar comportamiento en la cadena de llamadas al LLM. El `QuestionAnswerAdvisor` implementa el flujo RAG completo: recibe la pregunta, busca en el vector store, y enriquece el prompt con el contexto antes de enviarlo al LLM. El `MessageChatMemoryAdvisor` agrega memoria conversacional.

```java
/**
 * Servicio de chat RAG que orquesta la consulta con contexto.
 * 
 * Flujo:
 * 1. Recibe la pregunta del usuario
 * 2. QuestionAnswerAdvisor busca chunks relevantes en pgvector
 * 3. Enriquece el prompt con ese contexto
 * 4. ChatMemoryAdvisor agrega el historial de conversación
 * 5. Envía al LLM y devuelve la respuesta fundamentada
 */
@Service
public class RagChatService {

    private final ChatClient chatClient;

    public RagChatService(ChatClient.Builder chatClientBuilder,
                          VectorStore vectorStore,
                          ChatMemory chatMemory) {

        this.chatClient = chatClientBuilder
            .defaultSystem("""
                Eres un asistente empresarial. Responde SOLO basándote
                en el contexto proporcionado. Si no encuentras la 
                información, di "No tengo información sobre ese tema 
                en los documentos disponibles."
                
                NUNCA inventes información. Cita las fuentes cuando 
                sea posible.
                """)
            .defaultAdvisors(
                // Advisor RAG: busca en vector store y enriquece el prompt
                new QuestionAnswerAdvisor(vectorStore, 
                    SearchRequest.builder()
                        .topK(5)                // Top 5 chunks más relevantes
                        .similarityThreshold(0.7) // Mínimo 70% de similitud
                        .build()),

                // Advisor de memoria: recuerda conversaciones previas
                new MessageChatMemoryAdvisor(chatMemory, 10) // últimos 10 msgs
            )
            .build();
    }

    /**
     * Consulta RAG simple — busca en todos los documentos.
     */
    public String chat(String userQuestion) {
        return chatClient.prompt()
            .user(userQuestion)
            .call()
            .content();
    }

    /**
     * Consulta RAG con filtro por tenant (multi-tenant).
     * Solo busca en documentos del tenant especificado.
     */
    public String chatWithTenantFilter(String userQuestion, String tenantId) {
        return chatClient.prompt()
            .user(userQuestion)
            .advisors(advisor -> advisor.param(
                QuestionAnswerAdvisor.FILTER_EXPRESSION,
                "tenant_id == '" + tenantId + "'"  // Filtro por tenant
            ))
            .call()
            .content();
    }

    /**
     * Consulta RAG con streaming — respuesta token por token.
     * Ideal para UIs que muestran la respuesta progresivamente.
     */
    public Flux<String> chatStream(String userQuestion) {
        return chatClient.prompt()
            .user(userQuestion)
            .stream()
            .content();
    }
}
```

---

### 6.5 Controller REST y Endpoint de Ingestión

```java
@RestController
@RequestMapping("/api/rag")
public class RagController {

    private final RagChatService ragChatService;
    private final DocumentIngestionService ingestionService;

    // --- Endpoint de CHAT (consulta RAG) ---
    @PostMapping("/chat")
    public ResponseEntity<ChatResponse> chat(@RequestBody ChatRequest request) {
        String answer = ragChatService.chatWithTenantFilter(
            request.question(), 
            request.tenantId()
        );
        return ResponseEntity.ok(new ChatResponse(answer));
    }

    // --- Endpoint de STREAMING (respuesta progresiva) ---
    @PostMapping(value = "/chat/stream", produces = MediaType.TEXT_EVENT_STREAM_VALUE)
    public Flux<String> chatStream(@RequestBody ChatRequest request) {
        return ragChatService.chatStream(request.question());
    }

    // --- Endpoint de INGESTIÓN (subir documentos) ---
    @PostMapping("/ingest")
    public ResponseEntity<String> ingestDocument(
            @RequestParam("file") MultipartFile file,
            @RequestParam("tenantId") String tenantId,
            @RequestParam(value = "category", defaultValue = "general") String category) {

        ingestionService.ingestDocument(
            file.getResource(), tenantId, category
        );
        return ResponseEntity.ok("Documento ingerido exitosamente");
    }

    // --- DTOs ---
    record ChatRequest(String question, String tenantId) {}
    record ChatResponse(String answer) {}
}
```

---

### 6.6 Patrones Avanzados en Producción

```
┌────────────────────────────────────────────────────────────────────────────┐
│         PATRONES RAG AVANZADOS PARA PRODUCCIÓN                             │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  🔹 MULTI-TENANCY (Aislamiento de datos por cliente)                      │
│  ──────────────────────────────────────────────────                        │
│  Cada cliente solo ve SUS documentos. Se implementa con:                  │
│  • Metadato "tenant_id" en cada documento                                 │
│  • Filter expression en cada consulta                                     │
│  • NUNCA confiar en el front — validar tenant en el backend               │
│                                                                            │
│  🔹 CACHÉ DE RESPUESTAS                                                   │
│  ──────────────────────                                                    │
│  Las llamadas al LLM son lentas (~1-5s) y costosas.                       │
│  • Cachear respuestas para preguntas frecuentes con Redis                 │
│  • TTL razonable (1h–24h dependiendo de la volatilidad)                   │
│  • Cache key = hash(pregunta + tenant + filtros)                          │
│                                                                            │
│  🔹 STREAMING RESPONSES (Server-Sent Events)                              │
│  ────────────────────────────────────────────                              │
│  En vez de esperar la respuesta completa, enviar token por token:         │
│  • Mejor UX (el usuario ve la respuesta formándose)                       │
│  • Menor Time-To-First-Byte (TTFB)                                       │
│  • Implementar con Flux<String> + SSE en Spring WebFlux                   │
│                                                                            │
│  🔹 EVALUACIÓN DE CALIDAD (RAG evaluation)                                │
│  ─────────────────────────────────────────                                 │
│  Medir la calidad de las respuestas con métricas:                         │
│  • Faithfulness: ¿la respuesta se basa en el contexto recuperado?         │
│  • Relevancy: ¿los chunks recuperados son relevantes a la pregunta?      │
│  • Hallucination rate: ¿cuántas respuestas inventan datos?               │
│  • Herramientas: RAGAS, DeepEval, o un LLM evaluador                     │
│                                                                            │
│  🔹 INGESTIÓN INCREMENTAL                                                 │
│  ────────────────────────                                                  │
│  No re-procesar todo cada vez:                                            │
│  • Guardar hash del documento para detectar cambios                       │
│  • Eliminar chunks viejos antes de re-ingerir                             │
│  • Pipeline asíncrono con @Async o Spring Batch                           │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico Integrador:**

Construye una aplicación Spring Boot completa con:
1. **Endpoint de ingestión** que acepte archivos PDF/TXT via `MultipartFile`
2. **Pipeline** de lectura → chunking → enriquecimiento → almacenamiento en pgvector
3. **Endpoint de chat RAG** que reciba preguntas y devuelva respuestas fundamentadas
4. **Filtrado multi-tenant** para que cada tenant solo consulte sus propios documentos
5. **Streaming** del response usando Server-Sent Events
6. **Tests de integración** con `@SpringBootTest` + Testcontainers para PostgreSQL/pgvector

> [!TIP]
> Usa **Docker Compose** para levantar PostgreSQL + pgvector localmente:
> ```yaml
> services:
>   postgres:
>     image: pgvector/pgvector:pg16
>     ports:
>       - "5432:5432"
>     environment:
>       POSTGRES_DB: ragdb
>       POSTGRES_USER: raguser
>       POSTGRES_PASSWORD: ragpass
> ```

---

## Fase 7: Agentes Autónomos y Flujos Complejos (El Cerebro)

> 🎯 **Objetivo:** Pasar de un sistema **reactivo** (pregunta-respuesta) a un sistema **proactivo** con capacidad de iteración autónoma.

### 7.1 Semantic Routing y Clasificación de Intenciones

**Concepto:** Antes de hacer una llamada costosa a un LLM grande o a un sistema RAG profundo, usas un **LLM pequeño y rápido** (o embeddings) para **enrutar** la petición. ¿Es charla casual? ¿Es una consulta de base de datos? ¿Es una queja?

> 💡 **Analogía:** El **menú telefónico (IVR) inteligente**. _"Para ventas pulse 1, para soporte pulse 2"_ — pero el sistema entiende lenguaje natural en vez de números.

```
┌────────────────────────────────────────────────────────────────┐
│              SEMANTIC ROUTING                                    │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Input: "Mi pedido llegó roto"                                 │
│                │                                               │
│                ▼                                               │
│  ┌──────────────────────────────┐                              │
│  │ ROUTER (modelo ligero/rápido)│                              │
│  │ gpt-4o-mini / clasificador   │                              │
│  │                               │                              │
│  │ Clasifica → Enum:             │                              │
│  │   SUPPORT | SALES | CHITCHAT  │                              │
│  └─────────────┬────────────────┘                              │
│                │                                               │
│     ┌──────────┼──────────┐                                    │
│     │          │          │                                    │
│  ┌──▼────┐ ┌──▼────┐ ┌──▼────────┐                           │
│  │SUPPORT│ │ SALES │ │ CHITCHAT  │                            │
│  │       │ │       │ │           │                            │
│  │RAG +  │ │RAG de │ │ Modelo    │                            │
│  │modelo │ │catálogo│ │ simple    │                            │
│  │potente│ │       │ │ (barato)  │                            │
│  └───────┘ └───────┘ └───────────┘                            │
│                                                                │
│  ✅ Ahorra costos: no usar GPT-4 para "Hola, ¿cómo estás?"  │
│  ✅ Mejor calidad: cada ruta usa el modelo óptimo              │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Construye una clase `RouterManager`. Ante la entrada de un usuario, usa un modelo ligero (ej. `gpt-4o-mini`) para clasificar el texto en un `Enum`: `SUPPORT`, `SALES`, `CHITCHAT`. Dependiendo del resultado, deriva la ejecución a diferentes clases de servicio en Spring.

---

### 7.2 El Patrón ReAct y Agentes

**Concepto:** Escribir un ciclo `while` donde el LLM **razona** ("Reason"), decide usar una **herramienta** ("Act"), **observa** el resultado ("Observe") y **repite** hasta lograr la tarea.

> 💡 **Analogía:** Un **detective** resolviendo un caso. Encuentra una pista (Reason), va a interrogar a alguien (Act), escucha la respuesta (Observe) y decide su siguiente movimiento.

```
┌────────────────────────────────────────────────────────────────┐
│              PATRÓN ReAct (Reason + Act)                         │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Objetivo: "El servicio de pagos está lento, arréglalo"        │
│                                                                │
│  ┌─────────────────────────────────────────────────────┐       │
│  │ Iteración 1:                                        │       │
│  │ 🧠 REASON: "Necesito ver los logs para entender     │       │
│  │             qué está pasando"                        │       │
│  │ 🔧 ACT:    getLogs("payment-service")                │       │
│  │ 👁️ OBSERVE: "ERROR: Connection pool exhausted..."    │       │
│  └─────────────────────────────────────────────────────┘       │
│                         │                                      │
│  ┌─────────────────────────────────────────────────────┐       │
│  │ Iteración 2:                                        │       │
│  │ 🧠 REASON: "El pool de conexiones está agotado.     │       │
│  │             Reiniciar debería liberarlo"             │       │
│  │ 🔧 ACT:    restartService("payment-service")        │       │
│  │ 👁️ OBSERVE: "Service restarted. Status: HEALTHY"    │       │
│  └─────────────────────────────────────────────────────┘       │
│                         │                                      │
│  ┌─────────────────────────────────────────────────────┐       │
│  │ Iteración 3:                                        │       │
│  │ 🧠 REASON: "Servicio reiniciado. Verifico si        │       │
│  │             funciona correctamente ahora"           │       │
│  │ 🔧 ACT:    getLogs("payment-service")                │       │
│  │ 👁️ OBSERVE: "INFO: Processing payments normally"    │       │
│  └─────────────────────────────────────────────────────┘       │
│                         │                                      │
│  📝 REPORTE FINAL:                                             │
│  "El servicio de pagos tenía un pool de conexiones             │
│   agotado (Connection pool exhausted). Se reinició             │
│   el servicio exitosamente y ahora procesa pagos               │
│   con normalidad."                                             │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Crea un **"Agente Analista de Servidores"**. Dale dos herramientas (Function Calling): `getLogs(serviceName)` y `restartService(serviceName)`. Pídele: _"El servicio de pagos está lento, arréglalo"_. El sistema debe, autónomamente: 1) Llamar a ver logs. 2) Analizar el texto devuelto. 3) Decidir llamar a reiniciar el servicio. 4) Redactarte un reporte de lo que hizo.

---

### 7.3 Orquestación Multi-Agente

**Concepto:** Para tareas complejas, un solo agente no es suficiente. Se crea un **orquestador** que delega subtareas a agentes especializados, cada uno con su propio contexto, herramientas y modelo.

| Patrón                    | Descripción                                   | Cuándo Usarlo                    |
| ------------------------- | --------------------------------------------- | -------------------------------- |
| **Orquestador-Worker**    | Un agente manager descompone y delega         | Features completos, pipelines    |
| **Evaluador-Optimizador** | Un agente genera, otro evalúa y critica       | Code review, documentación       |
| **Routing**               | Un dispatcher enruta al especialista correcto | Helpdesk, clasificador de issues |
| **Scatter-Gather**        | Varios agentes en paralelo, se combinan       | Generar múltiples propuestas     |

**💻 Ejercicio Práctico:**

Diseña un sistema con 2 agentes: un **Agente Coder** que genera código y un **Agente Reviewer** que lo evalúa. El orquestador envía un requerimiento al Coder, pasa el resultado al Reviewer, y si el Reviewer encuentra problemas, devuelve feedback al Coder para que itere.

---

## Fase 8: LLMOps, Observabilidad y Producción (El Mantenimiento)

> 🎯 **Objetivo:** En producción, la IA es costosa, propensa a alucinaciones y estresante para la infraestructura. Aquí aprendes a **monitorear, proteger y optimizar** tu sistema.

### 8.1 Tracing y Observabilidad

**Concepto:** Necesitas ver **visualmente** cuánto tardó la consulta a la BD vectorial, cuánto tardó la red, y cuántos tokens generó el LLM por cada endpoint consumido.

> 💡 **Analogía:** Las **cámaras de seguridad** y el **libro de contabilidad** de una fábrica. Si algo sale mal, puedes rastrear exactamente dónde y cuándo ocurrió.

```
┌────────────────────────────────────────────────────────────────┐
│         OBSERVABILIDAD DE UN SISTEMA AI                          │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  📊 MÉTRICAS (¿Qué está pasando?)                              │
│  • Tokens consumidos por endpoint/minuto                       │
│  • Latencia P50/P95/P99 de llamadas al LLM                    │
│  • Hit rate de la caché de respuestas                          │
│  • Tasa de alucinaciones detectadas                            │
│                                                                │
│  🔍 TRACES (¿Por qué está lento?)                              │
│  ┌─────── Request: POST /api/rag/chat ─────────────────┐      │
│  │                                                      │      │
│  │ ├─ Controller         [2ms]                          │      │
│  │ ├─ VectorStore.search [45ms] ⬅ búsqueda vectorial  │      │
│  │ ├─ Re-ranker          [120ms] ⬅ re-ordenamiento    │      │
│  │ ├─ Prompt.build       [3ms]                          │      │
│  │ ├─ LLM.call           [1850ms] ⬅ generación IA    │      │
│  │ │  └─ tokens: 450 prompt + 230 completion            │      │
│  │ └─ Response.parse     [5ms]                          │      │
│  │                                                      │      │
│  │ Total: 2025ms | Cost: $0.0045                       │      │
│  └──────────────────────────────────────────────────────┘      │
│                                                                │
│  📋 LOGS ESTRUCTURADOS                                         │
│  • Pregunta del usuario (sanitizada)                           │
│  • Chunks recuperados y su score de similitud                  │
│  • Prompt final enviado al LLM (para debug)                    │
│  • Respuesta completa y tiempo de generación                   │
│                                                                │
│  Stack: Spring Boot Actuator + Micrometer + OpenTelemetry      │
│         + Zipkin/Jaeger (traces) + Prometheus/Grafana (métricas)│
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Integra **Micrometer** y la dependencia de **Spring Boot Actuator** en tu proyecto Spring AI. Configura **OpenTelemetry** localmente con Zipkin. Realiza llamadas a tus endpoints y observa en la UI los Spans de cuánto tiempo tomó exactamente la generación del LLM y cuántos tokens reportó como métrica.

---

### 8.2 Rate Limiting, Costos y Seguridad (Guardrails)

**Concepto:** Evitar que un ataque DDoS (o un usuario abusivo) dispare tu factura de OpenAI a miles de dólares. Implementar **cortafuegos temáticos** para que el bot de tu banco no dé recetas de cocina.

> 💡 **Analogía:** Poner un **límite de presupuesto diario** a la tarjeta corporativa de los empleados, y además poner un guardia que verifica que solo se compren suministros de oficina — no yates.

```
┌────────────────────────────────────────────────────────────────┐
│              GUARDRAILS DE SEGURIDAD                             │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  Pregunta del usuario                                          │
│         │                                                      │
│         ▼                                                      │
│  ┌──────────────────────────────┐                              │
│  │ 🛡️ GUARDRAIL 1: Rate Limiter │                              │
│  │ ¿Excedió 5 req/min?          │                              │
│  │ → SÍ: HTTP 429 Too Many      │                              │
│  │ → NO: continuar               │                              │
│  └──────────────┬───────────────┘                              │
│                 ▼                                               │
│  ┌──────────────────────────────┐                              │
│  │ 🛡️ GUARDRAIL 2: Content Filter│                             │
│  │ ¿Contiene Prompt Injection?   │                              │
│  │ ¿Pide algo fuera de alcance?  │                              │
│  │ → SÍ: Bloquear + log          │                              │
│  │ → NO: continuar                │                              │
│  └──────────────┬───────────────┘                              │
│                 ▼                                               │
│  ┌──────────────────────────────┐                              │
│  │ 🛡️ GUARDRAIL 3: Token Budget │                              │
│  │ ¿Este request consumiría     │                              │
│  │  más de X tokens máximo?      │                              │
│  │ → SÍ: Reducir/rechazar        │                              │
│  │ → NO: continuar                │                              │
│  └──────────────┬───────────────┘                              │
│                 ▼                                               │
│         🤖 Procesamiento LLM                                   │
│                 │                                               │
│                 ▼                                               │
│  ┌──────────────────────────────┐                              │
│  │ 🛡️ GUARDRAIL 4: Output Filter│                              │
│  │ ¿La respuesta contiene datos  │                              │
│  │  sensibles? (PII, passwords)  │                              │
│  │ → SÍ: Sanitizar antes de      │                              │
│  │        devolver al usuario     │                              │
│  └──────────────────────────────┘                              │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

**💻 Ejercicio Práctico:**

Implementa la librería **Resilience4j** en tu servicio que llama al LLM. Configura un `RateLimiter` que solo permita 5 peticiones por minuto por usuario. Además, antes de mandar la petición del usuario al LLM, pásala por una función ligera que valide si contiene **Prompt Injection** (intentos de saltarse las reglas) y la bloquee si es maliciosa.

---

### 8.3 Gestión de Costos

**Concepto:** Las APIs de LLM cobran **por token**. Sin control, un sistema con muchos usuarios puede generar facturas de miles de dólares.

| Estrategia                    | Impacto en Costos | Implementación                                            |
| ----------------------------- | ----------------- | --------------------------------------------------------- |
| **Caché de respuestas**       | -50% a -80%       | Redis + TTL por tipo de consulta                          |
| **Routing de modelos**        | -40% a -60%       | Modelo barato para tareas simples, potente para complejas |
| **Chunking optimizado**       | -20% a -30%       | Menos chunks innecesarios = menos tokens                  |
| **Max tokens por request**    | Predecible        | Limitar `max_tokens` en la configuración                  |
| **Rate limiting por usuario** | Protección        | Resilience4j o Spring Cloud Gateway                       |
| **Monitoreo de uso**          | Visibilidad       | Dashboard de tokens consumidos por endpoint               |

---

## 📋 Checklist de Progresión

> Usa este checklist para trackear tu avance a lo largo del roadcamp:

| Fase  | Hito                                                                        | Estado |
| ----- | --------------------------------------------------------------------------- | ------ |
| **1** | Hice una petición HTTP cruda a la API de un LLM                             | ⬜      |
| **1** | Entiendo qué son tokens, temperature y system prompts                       | ⬜      |
| **2** | Configuré Spring AI con ChatClient y cambié de proveedor sin cambiar código | ⬜      |
| **2** | Usé BeanOutputConverter para obtener POJOs del LLM                          | ⬜      |
| **3** | Implementé Function Calling y el LLM invocó mi código Java                  | ⬜      |
| **4** | Calculé similitud del coseno entre embeddings                               | ⬜      |
| **4** | Configuré pgvector + Spring AI y hice búsqueda semántica                    | ⬜      |
| **4** | Implementé RAG básico: chunking → vectorización → consulta con contexto     | ⬜      |
| **5** | Implementé filtrado por metadatos y re-ranking                              | ⬜      |
| **5** | Experimenté con GraphRAG y Neo4j                                            | ⬜      |
| **6** | Construí un pipeline de ingestión completo en Spring Boot                   | ⬜      |
| **6** | Implementé RAG multi-tenant con Advisors de Spring AI                       | ⬜      |
| **6** | Agregué streaming (SSE) a mi endpoint de chat                               | ⬜      |
| **7** | Construí un Semantic Router que clasifica intenciones                       | ⬜      |
| **7** | Implementé un agente ReAct con múltiples herramientas                       | ⬜      |
| **8** | Integré observabilidad (Micrometer + Actuator + tracing)                    | ⬜      |
| **8** | Implementé Rate Limiting y detección de Prompt Injection                    | ⬜      |

---

## 📚 Recursos Recomendados

| Recurso                 | Tipo                  | URL                                                                  |
| ----------------------- | --------------------- | -------------------------------------------------------------------- |
| **Spring AI Reference** | Documentación Oficial | [docs.spring.io/spring-ai](https://docs.spring.io/spring-ai)         |
| **LangChain4j**         | Framework Alternativo | [langchain4j.dev](https://langchain4j.dev)                           |
| **OpenAI API Docs**     | API Reference         | [platform.openai.com/docs](https://platform.openai.com/docs)         |
| **pgvector**            | Extensión PostgreSQL  | [github.com/pgvector/pgvector](https://github.com/pgvector/pgvector) |
| **RAG Best Practices**  | Guía de Patrones      | Documentación interna de este repositorio (AIDev.md)                 |

---

<p align="center">
    <sub>🗺️ Road Camp mantenido y actualizado continuamente · Última actualización: Abril 2026</sub>
</p>