# Common C4 Model Mistakes to Avoid

This guide documents frequent anti-patterns and errors when creating C4 architecture diagrams, with examples of what to do instead.

## Abstraction Level Mistakes

### 1. Confusing Containers and Components

**The Problem:**
Containers are **deployable units** (applications, services, databases). Components are **non-deployable elements inside a container** (modules, classes, packages).

**WRONG - Java class shown as container:**

```
  ┌──────────────────────────────────────────────────┐
  │  [WRONG: Classes as Containers]                  │
  │                                                  │
  │  ┌──────────────────┐    ┌──────────────────┐    │
  │  │  <<container>>   │───→│  <<container>>   │    │
  │  │  UserController  │    │  UserService     │    │
  │  │  [Java Class]    │    │  [Java Class]    │    │
  │  └──────────────────┘    └────────┬─────────┘    │
  │                                   │              │
  │                          Queries ─┘              │
  │                          [JDBC]                  │
  │                                   │              │
  │                                   ▼              │
  │                          ┌──────────────────┐    │
  │                          │  <<database>>    │    │
  │                          │  Database        │    │
  │                          │  [PostgreSQL]    │    │
  │                          └──────────────────┘    │
  └──────────────────────────────────────────────────┘
```

**CORRECT - Classes as components inside a container:**

```
  ┌──────────────────────────────────────────────────────────┐
  │  [User API Service]                                      │
  │                                                          │
  │  ┌──────────────────┐  ┌──────────────────┐              │
  │  │  <<component>>   │  │  <<component>>   │              │
  │  │  UserController  │─→│  UserService     │              │
  │  │  [Spring MVC]    │  │  [Spring Bean]   │              │
  │  │  REST endpoints  │  │  Business logic  │              │
  │  └──────────────────┘  └────────┬─────────┘              │
  │                                 │                        │
  │                        Uses ────┘                        │
  │                                 │                        │
  │                                 ▼                        │
  │                        ┌──────────────────┐              │
  │                        │  <<component>>   │              │
  │                        │  UserRepository  │              │
  │                        │  [JPA]           │              │
  │                        │  Data access     │              │
  │                        └────────┬─────────┘              │
  └─────────────────────────────────┼────────────────────────┘
                                    │
                           Queries ─┘
                           [JDBC]
                                    │
                                    ▼
                           ┌──────────────────┐
                           │  <<database>>    │
                           │  Database        │
                           │  [PostgreSQL]    │
                           │  User data       │
                           └──────────────────┘
```

### 2. Adding Undefined Abstraction Levels

**The Problem:**
C4 defines exactly four levels. Don't invent "subcomponents", "modules", or other arbitrary levels.

**Wrong:**
- Level 3.5: "Subcomponents"
- Level 2.5: "Microservice groups"
- Custom levels like "packages" or "modules"

**Correct:**
Stick to Person, Software System, Container, Component. If you need more detail, you're at Level 4 (Code) which should use UML class diagrams.

### 3. Vague Subsystems

**The Problem:**
"Subsystem" is ambiguous. Is it a system, container, or component?

**Wrong:**
```
  ┌──────────────────┐
  │  Subsystem        │   ← What is this? System? Container? Component?
  │  Order Subsystem  │
  │  Handles orders   │
  └──────────────────┘
```

**Correct - Be specific:**
```
  ┌──────────────────┐    ┌──────────────────┐    ┌──────────────────┐
  │  <<system>>      │ OR │  <<container>>   │ OR │  <<component>>   │
  │  Order System    │    │  Order Service   │    │  Order Processor │
  │  [Handles order  │    │  [Java]          │    │  [Spring Bean]   │
  │   lifecycle]     │    │  Order processing│    │  Order business  │
  └──────────────────┘    │  API             │    │  logic           │
                          └──────────────────┘    └──────────────────┘
```

## Shared Libraries Mistake

**The Problem:**
Modeling a shared library as a container implies it's an independently running service. Libraries are copied into applications, not deployed separately.

**WRONG - Library as separate container:**

```
  ┌──────────────────┐    ┌──────────────────┐
  │  <<container>>   │    │  <<container>>   │
  │  Service A       │    │  Service B       │
  │  [Java]          │    │  [Java]          │
  └────────┬─────────┘    └────────┬─────────┘
           │                       │
           └───── Uses ────────────┘
                   │
                   ▼
           ┌──────────────────┐
           │  <<container>>   │    ← WRONG: Library is not a deployed service
           │  Shared Utils    │
           │  Library         │
           │  [Java]          │
           │  Common utils    │
           └──────────────────┘
```

**CORRECT - Show library within each service (or omit entirely):**

```
  ┌──────────────────────────────┐    ┌──────────────────────────────┐
  │  [Service A]                 │    │  [Service B]                 │
  │                              │    │                              │
  │  ┌──────────────────┐       │    │  ┌──────────────────┐       │
  │  │  <<component>>   │       │    │  │  <<component>>   │       │
  │  │  Controller      │       │    │  │  Controller      │       │
  │  │  [Spring MVC]    │       │    │  │  [Spring MVC]    │       │
  │  └──────────────────┘       │    │  └──────────────────┘       │
  │                              │    │                              │
  │  ┌──────────────────┐       │    │  ┌──────────────────┐       │
  │  │  <<component>>   │       │    │  │  <<component>>   │       │
  │  │  Shared Utils    │       │    │  │  Shared Utils    │       │
  │  │  [Java Library]  │       │    │  │  [Java Library]  │       │
  │  │  Bundled copy    │       │    │  │  Bundled copy    │       │
  │  └──────────────────┘       │    │  └──────────────────┘       │
  └──────────────────────────────┘    └──────────────────────────────┘
```

Or simply omit the library from architecture diagrams since it's an implementation detail.

## Message Broker Mistakes

### Single Message Bus Anti-Pattern

**The Problem:**
Showing Kafka/RabbitMQ as a single container creates a misleading "hub and spoke" diagram that hides actual data flows.

**WRONG - Central message bus:**

```
  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
  │ <<container>> │  │ <<container>> │  │ <<container>> │
  │ Order        │  │ Inventory    │  │ Payment      │
  │ Service      │  │ Service      │  │ Service      │
  │ [Java]       │  │ [Java]       │  │ [Java]       │
  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘
         │                 │                  │
         └──── Pub/Sub ────┼──── Pub/Sub ─────┘
                           │
                           ▼
                  ┌──────────────────┐
                  │  <<queue>>       │    ← WRONG: Single "Kafka" box
                  │  Kafka           │      hides actual data flows
                  │  [Event Stream]  │
                  │  Message bus     │
                  └──────────────────┘
```

**CORRECT - Individual topics:**

```
  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
  │ <<container>> │  │ <<container>> │  │ <<container>> │
  │ Order        │  │ Inventory    │  │ Payment      │
  │ Service      │  │ Service      │  │ Service      │
  │ [Java]       │  │ [Java]       │  │ [Java]       │
  └──┬───────────┘  └──┬───────┬───┘  └──┬───────────┘
     │                 │       │         │
     │ Publishes       │       │         │ Consumes
     │ [Avro]     Consumes  Publishes    │ [Avro]
     │            [Avro]    [Avro]       │
     ▼                 │       ▼         │
  ┌──────────────────┐ │  ┌──────────────┴───┐
  │  <<queue>>       │ │  │  <<queue>>       │
  │  order.created   │←┘  │  stock.reserved  │
  │  [Kafka]         │    │  [Kafka]         │
  │  New orders      │    │  Stock events    │
  └──────────────────┘    └──────────────────┘

  ┌──────────────────┐
  │  <<queue>>       │
  │  payment.complete│  ← Payment Service publishes,
  │  [Kafka]         │    Order Service consumes
  │  Payment events  │
  └──────────────────┘
```

**Alternative - Topics on relationship labels:**

```
  ┌──────────────┐         ┌──────────────┐         ┌──────────────┐
  │ <<container>> │         │ <<container>> │         │ <<container>> │
  │ Order        │─ ─ ─ ─→│ Inventory    │─ ─ ─ ─→│ Payment      │
  │ Service      │ order.  │ Service      │ stock.  │ Service      │
  │ [Java]       │ created │ [Java]       │reserved │ [Java]       │
  └──────────────┘ [Kafka] └──────────────┘ [Kafka] └──────┬───────┘
         ▲                                                  │
         │                                                  │
         └─ ─ ─ ─ ─  payment.complete [Kafka] ─ ─ ─ ─ ─ ─ ┘
```

## External Systems Mistakes

### Showing Internal Details of External Systems

**The Problem:**
You don't control external systems. Showing their internals creates coupling and becomes stale quickly.

**WRONG - External system internals:**

```
  ┌──────────────────┐
  │ <<container>>    │
  │ My App           │
  │ [Node.js]        │
  └────────┬─────────┘
           │
           │ Charges cards [REST]
           │
           ▼
  ┌──────────────────────────────────────────┐
  │  [Stripe]                                │    ← WRONG: Showing internals
  │                                          │      of external system
  │  ┌──────────────┐  ┌──────────────────┐  │
  │  │ Stripe API   │→ │ Payment Worker   │  │
  │  │ [Ruby]       │  │ [Java]           │  │
  │  └──────────────┘  └────────┬─────────┘  │
  │                             │             │
  │                             ▼             │
  │                    ┌──────────────────┐   │
  │                    │ Payment DB       │   │
  │                    │ [MySQL]          │   │
  │                    └──────────────────┘   │
  └──────────────────────────────────────────┘
```

**CORRECT - External system as black box:**

```
  ┌──────────────────┐         ┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┐
  │  <<container>>   │         │  <<external system>>  │
  │  My App          │────────→│  Stripe               │
  │  [Node.js]       │         │  [Payment processing  │
  │  E-commerce      │ Processes│   platform]           │
  │  backend         │ payments └ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┘
  └──────────────────┘ [REST API]
```

## Dynamic Diagram Mistakes

### Missing Step Numbers

**The Problem:**
Dynamic diagrams **require** numbered steps to show temporal order. Without numbers, the diagram is just a static relationship diagram.

**WRONG:**

```
  ┌──────────┐    ┌──────────┐    ┌──────────┐
  │ Client   │───→│ API      │───→│ Database │
  └──────────┘    └──────────┘    └──────────┘
       No step numbers — this is just a Container diagram!
```

**CORRECT:**

```
  ┌──────────┐    ┌──────────┐    ┌──────────┐
  │ Client   │    │ API      │    │ Database │
  └────┬─────┘    └────┬─────┘    └────┬─────┘
       │               │               │
       │── 1. Request →│               │
       │  [REST/JSON]  │               │
       │               │── 2. Query ──→│
       │               │  [SQL]        │
       │               │←── Data ─────│
       │←── 3. Result │               │
       │  [JSON]       │               │
```

### Mixing Abstraction Levels

**The Problem:**
All elements in a Dynamic Diagram must be at the same C4 abstraction level.

**WRONG - Mixing systems with components:**

```
  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
  │ <<system>>   │    │ <<component>> │    │ <<system>>   │
  │ Frontend     │───→│ AuthService  │───→│ Database     │
  └──────────────┘    └──────────────┘    └──────────────┘
       System!            Component!          System!
```

**CORRECT - All at container level:**

```
  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
  │ <<container>> │    │ <<container>> │    │ <<database>> │
  │ Frontend     │    │ Auth Service │    │ User DB      │
  │ [React]      │    │ [Node.js]    │    │ [PostgreSQL] │
  └──────┬───────┘    └──────┬───────┘    └──────┬───────┘
         │                   │                    │
         │── 1. Login ──────→│                    │
         │  [REST/JSON]      │                    │
         │                   │── 2. Verify ──────→│
         │                   │  [SQL]              │
         │                   │←── User record ────│
         │←── 3. JWT Token ─│                    │
```

### Too Many Elements

**The Problem:**
More than 7-9 elements makes the diagram unreadable.

**Solution:**
- Split into multiple dynamic diagrams (one per sub-flow)
- Move to a higher abstraction level (systems instead of containers)
- Focus on the critical path, document edge cases separately

## General Diagram Mistakes

### Missing Technology Labels

**WRONG:**
```
       │── Sends data ──→│
```

**CORRECT:**
```
       │── Sends order data ──→│
       │   [REST/JSON, HTTPS]  │
```

### Bidirectional Arrows

**WRONG:**
```
       │←── Uses ────→│    ← Ambiguous: who calls whom?
```

**CORRECT - Separate call and response:**
```
       │── 1. Request ───→│
       │   [REST/JSON]     │
       │←── Response ─────│
```

### Missing Descriptions on Elements

**WRONG:**
```
  ┌──────────────────┐
  │  API              │    ← What technology? What does it do?
  └──────────────────┘
```

**CORRECT:**
```
  ┌──────────────────┐
  │  <<container>>   │
  │  Order API       │
  │  [Spring Boot]   │
  │  REST API for    │
  │  order processing│
  └──────────────────┘
```
