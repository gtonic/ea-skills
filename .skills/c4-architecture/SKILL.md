---
name: c4-architecture
description: "Generate architecture documentation using C4 model ASCII diagrams including C4 Dynamic Diagrams for detailed interface communication. Use when asked to create architecture diagrams, document system architecture, visualize software structure, create C4 diagrams, describe interface communication, show request flows, or generate context/container/component/deployment/dynamic diagrams. Triggers include 'architecture diagram', 'C4 diagram', 'system context', 'container diagram', 'component diagram', 'deployment diagram', 'dynamic diagram', 'interface communication', 'Schnittstellenkommunikation', 'request flow', 'sequence', 'interaction', 'document architecture', 'visualize architecture'. Target audience: Integration Architects, Solution Architects."
---

# C4 Architecture Documentation

Generate software architecture documentation using C4 model diagrams in ASCII notation.

## Workflow

1. **Understand scope** - Determine which C4 level(s) are needed based on audience
2. **Analyze codebase** - Explore the system to identify components, containers, and relationships
3. **Generate diagrams** - Create ASCII C4 diagrams at appropriate abstraction levels
4. **Document** - Write diagrams to markdown files with explanatory context

## C4 Diagram Levels

Select the appropriate level based on the documentation need:

| Level | Diagram Type | Audience | Shows | When to Create |
|-------|-------------|----------|-------|----------------|
| 1 | **Context** | Everyone | System + external actors | Always (required) |
| 2 | **Container** | Technical | Apps, databases, services | Always (required) |
| 3 | **Component** | Developers | Internal components | Only if adds value |
| 4 | **Deployment** | DevOps | Infrastructure nodes | For production systems |
| - | **Dynamic** | Integration/Solution Architects | Request flows (numbered, temporal) | For interface communication & complex workflows |

**Key Insight:** "Context + Container diagrams are sufficient for most software development teams." Only create Component/Code diagrams when they genuinely add value. Use Dynamic diagrams when **temporal interaction sequences** or **detailed interface communication** must be documented.

---

## ASCII Notation Reference

### Element Types

```
Akteur (Person):         ┌──────────────────────┐
                         │  ☺ Name              │
                         │  [Rolle/Beschreibung]│
                         └──────────────────────┘

Zentrales System:        ╔══════════════════════╗
                         ║  <<system>>          ║
                         ║  Systemname          ║
                         ║  [Kurzbeschreibung]  ║
                         ╚══════════════════════╝

Internes System:         ┌──────────────────────┐
                         │  <<system>>          │
                         │  Systemname          │
                         │  [Beschreibung]      │
                         └──────────────────────┘

Externes System:         ┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┐
                         │  <<external system>>  │
                         │  Systemname           │
                         │  [Beschreibung]       │
                         └ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┘

Container:               ┌──────────────────────┐
                         │  <<container>>       │
                         │  Name                │
                         │  [Technologie]       │
                         │  Beschreibung        │
                         └──────────────────────┘

Container (Datenbank):   ┌──────────────────────┐
                         │  <<database>>        │
                         │  Name                │
                         │  [Technologie]       │
                         │  Beschreibung        │
                         └──────────────────────┘

Container (Queue):       ┌──────────────────────┐
                         │  <<queue>>           │
                         │  Name                │
                         │  [Technologie]       │
                         │  Beschreibung        │
                         └──────────────────────┘

Component:               ┌──────────────────────┐
                         │  <<component>>       │
                         │  Name                │
                         │  [Technologie]       │
                         │  Beschreibung        │
                         └──────────────────────┘
```

### Relationships

```
Synchron:                ────── Beschreibung ──────→
                                [Protokoll]

Asynchron:               ─ ─ ─  Beschreibung  ─ ─ ─→
                                [Protokoll]

Bidirektional:           ←───── Beschreibung ─────→
                                [Protokoll]

Synchrone Antwort:       ←───── Antwort ──────────
                                [Protokoll]

Asynchrone Antwort:      ←─ ─ ─ Antwort ─ ─ ─ ─ ─
                                [Protokoll]
```

### Boundaries

```
System Boundary:         ┌─────────────────────────────┐
                         │  [System Name]               │
                         │  ┌────────┐  ┌────────┐     │
                         │  │ Elem A │  │ Elem B │     │
                         │  └────────┘  └────────┘     │
                         └─────────────────────────────┘

Trust Boundary:          ┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄
                         ┊  Boundary Name              ┊
                         ┊  ...Elemente...              ┊
                         ┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄

Enterprise Boundary:     ╔═════════════════════════════╗
                         ║  Enterprise Name             ║
                         ║  ┌────────┐  ┌────────┐     ║
                         ║  │ Sys A  │  │ Sys B  │     ║
                         ║  └────────┘  └────────┘     ║
                         ╚═════════════════════════════╝
```

### Deployment Nodes

```
Deployment Node:         ╭─────────────────────────────╮
                         │  <<node>>                    │
                         │  Name [Type]                 │
                         │  ┌────────┐  ┌────────┐     │
                         │  │ Cont A │  │ Cont B │     │
                         │  └────────┘  └────────┘     │
                         ╰─────────────────────────────╯
```

---

## Quick Start Examples

### System Context (Level 1)

```
                              ┌──────────────────┐
                              │  ☺ User          │
                              │  [Tracks workouts│
                              │   and exercises] │
                              └────────┬─────────┘
                                       │
                            Uses ──────┘
                            [HTTPS]
                                       │
                                       ▼
                         ╔══════════════════════════╗
                         ║  <<system>>              ║
                         ║  Workout Tracker         ║
                         ║  [Vue PWA for tracking   ║
                         ║   strength & CrossFit    ║
                         ║   workouts]              ║
                         ╚════════════╤═════════════╝
                                      │
                        Persists ─────┘
                        data to
                        [IndexedDB]
                                      │
                                      ▼
                         ┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┐
                         │  <<external system>>     │
                         │  Web Browser             │
                         │  [Stores data in         │
                         │   IndexedDB]             │
                         └ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┘
```

### Container Diagram (Level 2)

```
              ┌──────────────────┐
              │  ☺ User          │
              │  [Tracks         │
              │   workouts]      │
              └────────┬─────────┘
                       │
             Uses ─────┘
             [HTTPS]
                       │
                       ▼
  ┌─────────────────────────────────────────────────┐
  │  [Workout Tracker PWA]                          │
  │                                                 │
  │  ┌──────────────────┐   ┌──────────────────┐   │
  │  │  <<container>>   │   │  <<container>>   │   │
  │  │  SPA             │──→│  State Mgmt      │   │
  │  │  [Vue 3, TS]     │   │  [Pinia]         │   │
  │  │  Single-page app │   │  App state       │   │
  │  └──────────────────┘   └────────┬─────────┘   │
  │                                  │              │
  │                        Persists ─┘              │
  │                        [Dexie ORM]              │
  │                                  │              │
  │                                  ▼              │
  │                         ┌──────────────────┐    │
  │                         │  <<database>>    │    │
  │                         │  IndexedDB       │    │
  │                         │  [Dexie]         │    │
  │                         │  Local workout   │    │
  │                         │  storage         │    │
  │                         └──────────────────┘    │
  └─────────────────────────────────────────────────┘
```

### Component Diagram (Level 3)

```
  ┌──────────────────┐
  │  <<container>>   │
  │  Views           │
  │  [Vue Router]    │
  └────────┬─────────┘
           │
     Uses ─┘
           │
           ▼
  ┌───────────────────────────────────────────────┐
  │  [Workout Feature]                            │
  │                                               │
  │  ┌──────────────────┐  ┌──────────────────┐  │
  │  │  <<component>>   │  │  <<component>>   │  │
  │  │  useWorkout      │─→│  useTimer        │  │
  │  │  [Composable]    │  │  [Composable]    │  │
  │  │  Workout exec.   │  │  Timer state     │  │
  │  │  state           │  │  machine         │  │
  │  └────────┬─────────┘  └──────────────────┘  │
  │           │                                   │
  │  Saves ───┘                                   │
  │  to                                           │
  │           │                                   │
  │           ▼                                   │
  │  ┌──────────────────┐                         │
  │  │  <<component>>   │                         │
  │  │  WorkoutRepo     │                         │
  │  │  [Dexie]         │                         │
  │  │  Workout persist.│                         │
  │  └──────────────────┘                         │
  └───────────────────────────────────────────────┘
```

### Deployment Diagram

```
  ╭───────────────────────────────────────╮
  │  <<node>> Customer Browser            │
  │  [Chrome/Firefox]                     │
  │                                       │
  │  ┌──────────────────┐                 │
  │  │  <<container>>   │                 │
  │  │  SPA             │                 │
  │  │  [React]         │                 │
  │  │  Web application │                 │
  │  └────────┬─────────┘                 │
  ╰───────────┼───────────────────────────╯
              │
    API calls ┘
    [HTTPS]
              │
              ▼
  ╭───────────────────────────────────────────────────╮
  │  <<node>> AWS Cloud [us-east-1]                   │
  │                                                   │
  │  ╭─────────────────────╮  ╭─────────────────────╮│
  │  │ <<node>> ECS Cluster│  │ <<node>> RDS        ││
  │  │ [Fargate]           │  │ [db.r5.large]       ││
  │  │                     │  │                     ││
  │  │ ┌──────────────────┐│  │ ┌──────────────────┐││
  │  │ │ <<container>>    ││  │ │ <<database>>     │││
  │  │ │ API Service      ││─→│ │ Database         │││
  │  │ │ [Node.js]        ││  │ │ [PostgreSQL]     │││
  │  │ │ REST API         ││  │ │ Application data │││
  │  │ └──────────────────┘│  │ └──────────────────┘││
  │  ╰─────────────────────╯  ╰─────────────────────╯│
  ╰───────────────────────────────────────────────────╯
```

---

## C4 Dynamic Diagram (Interface Communication)

### Purpose

C4 Dynamic Diagrams show the **runtime interactions** between elements (persons, systems,
containers, components) for a specific use case or business process. Interactions are
**numbered** to visualize temporal sequence — similar to UML Sequence Diagrams, but in
C4 style and at the desired abstraction level.

### Target Audience

- **Integration Architects**: Interface communication, protocols, data flows between systems
- **Solution Architects**: End-to-end flow of a use case across system boundaries

### When to Use

Use Dynamic Diagrams when:
- The **temporal sequence** of interactions between systems or components must be described
- **Interface communication** needs detailed documentation (which system calls what, when?)
- A specific **use case / business process** across multiple systems must be visualized
- **Integration scenarios** are analyzed or documented (e.g., onboarding flow, order process, data synchronization)
- The question is: "How do the systems communicate?" (not just "with whom?")

### Abstraction Levels

| Level | Elements | Typical Use |
|-------|----------|-------------|
| **System Context** | Persons ↔ Systems | Overview: Which systems participate in a process? |
| **Container** | Containers within systems (Web-App, API, DB, Queue) | Detail: How do calls flow within and between systems? |
| **Component** | Components within a container (Controller, Service, Repository) | Fine detail: How is a call processed within a container? |

### Interactive Dialog

When creating a Dynamic Diagram, follow this structured process:

#### Step 1: Identify Use Case / Scenario

Ask:
- Which use case or business process should be depicted?
  (e.g., "User signs in", "Order is placed", "Master data is synchronized")
- What is the **triggering event** (trigger)? (e.g., user action, timer, incoming message)
- What is the **expected outcome** at the end of the flow?

#### Step 2: Determine Abstraction Level

Ask:
- At which level should the diagram be created?
  - **System Context**: Interactions between whole systems (overview)
  - **Container**: Interactions between containers like web-app, API, database (recommended for interface documentation)
  - **Component**: Interactions between components within a container (fine detail)

If a C4 System Context Diagram has already been created in the conversation, reference
the identified systems and suggest the Container level as the next detail step.

#### Step 3: Identify Participating Elements

Ask (adapted to chosen level):

Collect elements in a table:

```
| # | Element         | Type                 | Belongs to     | Description              |
|---|-----------------|----------------------|----------------|--------------------------|
| 1 | Sachbearbeiter  | Actor                | —              | Triggers the process     |
| 2 | Web-Frontend    | Container (SPA)      | Portal-System  | Angular-based UI         |
| 3 | API-Gateway     | Container (Service)  | Portal-System  | Kong Gateway, Routing    |
| 4 | Fachservice     | Container (Service)  | Backend-System | Spring Boot REST-API     |
| 5 | PostgreSQL      | Container (Database) | Backend-System | Business data            |
| 6 | SAP ERP         | External System      | —              | Financial accounting     |
```

Confirm the table with the user before proceeding.

#### Step 4: Capture Interaction Steps

Ask:
- Describe the flow step by step:
  - Who calls whom?
  - What is transmitted/requested?
  - Which protocol/technology is used? (REST/JSON, gRPC, AMQP, SQL, JDBC, GraphQL, SOAP, SFTP, ...)
  - Is the call synchronous or asynchronous?
  - Is there a response/return? (e.g., "returns order confirmation")

Collect steps in a numbered table:

```
| Step | From           | To             | Action                       | Protocol   | Sync/Async | Response                |
|------|----------------|----------------|------------------------------|------------|------------|-------------------------|
| 1    | Sachbearbeiter | Web-Frontend   | Opens order form             | HTTPS      | Sync       | —                       |
| 2    | Web-Frontend   | API-Gateway    | POST /api/orders             | REST/JSON  | Sync       | 202 Accepted            |
| 3    | API-Gateway    | Fachservice    | Forward POST /orders         | REST/JSON  | Sync       | 202 Accepted            |
| 4    | Fachservice    | PostgreSQL     | INSERT INTO orders           | JDBC/SQL   | Sync       | OK                      |
| 5    | Fachservice    | SAP ERP        | Create booking               | SOAP/XML   | Async      | —                       |
| 6    | SAP ERP        | Fachservice    | Booking confirmation (CB)    | REST/JSON  | Async      | Booking number          |
| 7    | Fachservice    | PostgreSQL     | UPDATE orders SET status=... | JDBC/SQL   | Sync       | OK                      |
```

Confirm with user before proceeding.

#### Step 5: Error Cases and Alternative Paths (optional)

Ask:
- Are there error cases to be shown? (e.g., "What happens if SAP is unreachable?")
- Are there alternative paths? (e.g., "If customer already exists, step X is skipped")

If yes, capture as additional steps with marking (e.g., "5a" for alternative to step 5).

#### Step 6: Generate Diagram

### Dynamic Diagram Notation

```
Participating elements as columns (similar to Sequence Diagram):

  ┌──────────┐    ┌──────────────┐    ┌ ─ ─ ─ ─ ─ ─┐
  │  ☺ Name  │    │ <<container>> │   │ <<external>> │
  │  [Rolle] │    │  Servicename  │   │  Systemname  │
  └────┬─────┘    └──────┬────────┘   └ ─ ─ ─┬─ ─ ─ ┘
       │                 │                     │
       │                 │                     │

Synchronous call (numbered):
       │── 1. Description ──→│
       │       [Protocol]     │
       │←── Response ────────│

Asynchronous call (numbered):
       │─ ─ 2. Description ─ ─→│
       │        [Protocol]       │

Asynchronous response:
       │←─ ─ ─ Response ─ ─ ─ ─│

Self-call:
       │──┐ 3. Validation
       │  │    [internal]
       │←─┘

Grouping (optional, for loops/conditions):
       ╔══[loop: for each item]════════════════════╗
       ║  │── 4. Check item ──→│                   ║
       ║  │←── Stock level ───│                   ║
       ╚═══════════════════════════════════════════╝

       ╔══[alt: customer exists]═══════════════════╗
       ║  │── 5a. Load customer data ──→│          ║
       ╠══[else]═══════════════════════════════════╣
       ║  │── 5b. Create customer ─────→│          ║
       ╚═══════════════════════════════════════════╝
```

### System Boundaries in Dynamic Diagrams

```
       │ Portal-System                │ Backend-System              │ External
       │                              │                             │
  ┌─────────┐  ┌──────────────┐  ┌──────────┐  ┌──────────┐  ┌ ─ ─ ─ ─ ─┐
  │ Web-     │  │ API-Gateway  │  │ Fach-    │  │ Postgres │  │  SAP ERP  │
  │ Frontend │  │              │  │ service  │  │          │  │           │
  └────┬─────┘  └──────┬───────┘  └────┬─────┘  └────┬─────┘  └ ─ ─┬─ ─ ─┘
       │               │               │              │              │
```

### Dynamic Diagram Example: User Sign In Flow

```
  ┌──────────────┐  ┌──────────────────────────────────────────┐  ┌──────────────┐
  │ <<container>> │  │ [API Application]                        │  │ <<database>> │
  │ Single-Page  │  │                                          │  │ Database     │
  │ App          │  │  ┌───────────────┐  ┌─────────────────┐  │  │ [PostgreSQL] │
  │ [Angular]    │  │  │ <<component>> │  │  <<component>>  │  │  │ User         │
  │ Banking UI   │  │  │ Sign In       │  │  Security       │  │  │ credentials  │
  │              │  │  │ Controller    │  │  Service         │  │  │              │
  └──────┬───────┘  │  │ [Spring MVC]  │  │  [JWT]          │  │  └──────┬───────┘
         │          │  └──────┬────────┘  └────────┬────────┘  │         │
         │          └─────────┼────────────────────┼───────────┘         │
         │                    │                    │                     │
         │── 1. Submit ──────→│                    │                     │
         │   credentials      │                    │                     │
         │   [JSON/HTTPS]     │                    │                     │
         │                    │── 2. Validate ────→│                     │
         │                    │                    │                     │
         │                    │                    │── 3. Query user ──→│
         │                    │                    │   [JDBC]            │
         │                    │                    │                     │
         │                    │                    │←── User data ──────│
         │                    │←── Auth result ───│                     │
         │←── JWT Token ─────│                    │                     │
         │   [JSON/HTTPS]     │                    │                     │
```

### Dynamic Diagram Example: Order Processing (Event-Driven)

```
  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
  │ <<container>> │  │ <<container>> │  │ <<container>> │  │ <<container>> │
  │ Order        │  │ Inventory    │  │ Payment      │  │ Shipping     │
  │ Service      │  │ Service      │  │ Service      │  │ Service      │
  │ [Java]       │  │ [Go]         │  │ [Node.js]    │  │ [Python]     │
  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘
         │                 │                  │                  │
         │─ ─ 1. Publish ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─→
         │   order.created                    │                  │
         │   [Kafka/Avro]  │                  │                  │
         │                 │                  │                  │
         │          2. Consume ←─ ─ ─ ─ ─ ─ ─┘                  │
         │          order.created              │                  │
         │          [Kafka/Avro]               │                  │
         │                 │                  │                  │
         │                 │─ ─ 3. Publish ─ ─ ─ ─ ─ ─ ─ ─ ─ ─→│
         │                 │   inventory.reserved                │
         │                 │   [Kafka/Avro]   │                  │
         │                 │                  │                  │
         │                 │           4. Consume ←─ ─ ─ ─ ─ ─ ─┘
         │                 │           inventory.reserved         │
         │                 │           [Kafka/Avro]               │
         │                 │                  │                  │
         │                 │                  │─ ─ 5. Publish ─→│
         │                 │                  │   payment.done   │
         │                 │                  │   [Kafka/Avro]   │
         │                 │                  │                  │
         │                 │                  │           6. Consume
         │                 │                  │           payment.done
         │                 │                  │           [Kafka/Avro]
```

### Dynamic Diagram Example: OAuth2 Authorization Code Flow

```
  ┌──────────────┐  ┌──────────────┐  ┌ ─ ─ ─ ─ ─ ─ ─┐  ┌──────────────┐
  │ <<container>> │  │ <<container>> │  │ <<external>>  │  │ <<database>> │
  │ SPA          │  │ API          │  │ Auth0          │  │ User DB      │
  │ [React]      │  │ [Node.js]    │  │ [AuthZ Server] │  │ [PostgreSQL] │
  └──────┬───────┘  └──────┬───────┘  └ ─ ─ ─┬─ ─ ─ ─┘  └──────┬───────┘
         │                 │                  │                   │
         │── 1. Redirect ─ ─ ─ ─ ─ ─ ─ ─ ─→│                   │
         │   to /authorize                    │                   │
         │                 │                  │                   │
         │←─ 2. Redirect ─ ─ ─ ─ ─ ─ ─ ─ ─│                   │
         │   with auth code                   │                   │
         │                 │                  │                   │
         │── 3. Exchange code ──→│            │                   │
         │   for tokens          │            │                   │
         │   [HTTPS]             │            │                   │
         │                       │── 4. POST ─ ─ ─ ─ ─ ─ ─ ─ ─→│
         │                       │   /oauth/token                │
         │                       │   [HTTPS]  │                   │
         │                       │            │                   │
         │                       │←─ tokens ─ ─ ─ ─ ─ ─ ─ ─ ─ ─│
         │                       │            │                   │
         │←── 5. Access + ──────│            │                   │
         │   refresh tokens      │            │                   │
         │                 │                  │                   │
         │── 6. API request ────→│            │                   │
         │   with access token   │            │                   │
         │   [HTTPS]             │            │                   │
         │                       │── 7. Fetch ──────────────────→│
         │                       │   user data                    │
         │                       │   [SQL]    │                   │
         │                       │            │                   │
         │                       │←── user data ─────────────────│
         │←── response ─────────│            │                   │
```

---

## Heuristics (MUST)

### General Rules

1. **Every element must have**: Name, Type, Technology (where applicable), and Description
2. **Use unidirectional arrows** - Bidirectional arrows create ambiguity; show call and response separately
3. **Label arrows with action verbs** - "Sends email using", "Reads from", not just "uses"
4. **Include technology labels** - "JSON/HTTPS", "JDBC", "gRPC"
5. **Stay under 20 elements per diagram** - Split complex systems into multiple diagrams

### Dynamic Diagram Rules

1. **Numbering is mandatory**: Every interaction step **must** have a sequential number showing temporal order.
2. **One use case per diagram**: A Dynamic Diagram describes **exactly one** use case or business process.
3. **Protocol mandatory**: Every call **must** specify the protocol/technology used.
4. **Sync/Async marking**: Synchronous calls as solid arrows (`───`), asynchronous as dashed arrows (`─ ─ ─`).
5. **Direction mandatory**: Every arrow **must** have a clear direction.
6. **Responses explicit**: If a call has a relevant response (data, confirmation), show it as a return arrow.
7. **Consistent abstraction level**: All elements **must** be at the same C4 abstraction level.
8. **Trigger recognizable**: The triggering actor/event must be clearly recognizable (leftmost position).
9. **Layout**: Elements from left (trigger) to right (target systems). Frequently interacting elements side by side.
10. **Compactness**: Maximum 7±2 elements per diagram. With more elements, switch to a higher abstraction level or split the use case.

### Clarity Guidelines

1. **Start at Level 1** - Context diagrams help frame system scope
2. **One diagram per file** - Keep diagrams focused on a single abstraction level
3. **Meaningful names** - Use descriptive names (e.g., "Order Service" not "Svc1")
4. **Concise descriptions** - Keep descriptions under 50 characters when possible
5. **Always include a title** - "System Context diagram for [System Name]"

### What to Avoid

See [references/common-mistakes.md](references/common-mistakes.md) for detailed anti-patterns:
- Confusing containers (deployable) vs components (non-deployable)
- Modeling shared libraries as containers
- Showing message brokers as single containers instead of individual topics
- Adding undefined abstraction levels like "subcomponents"
- Removing type labels to "simplify" diagrams

---

## Legend

Always add a legend below every diagram:

```
╔══════════════════════════════════════════════════════════╗
║  LEGEND                                                  ║
╠══════════════════════════════════════════════════════════╣
║  ☺        = Actor / Person                               ║
║  ╔═╗      = Central System (scope)                       ║
║  ┌─┐      = Internal Element (System/Container/Comp.)    ║
║  ┌ ┐      = External System                              ║
║  ───→     = Synchronous call                             ║
║  ─ ─→     = Asynchronous call                            ║
║  ←───     = Synchronous response                         ║
║  ←─ ─     = Asynchronous response / Callback             ║
║  [n]      = Step number (temporal order)                  ║
║  ╔══[x]═╗ = Grouping (loop/alt/opt)                      ║
║  ┄┄┄     = Trust Boundary                                ║
╚══════════════════════════════════════════════════════════╝
```

---

## Microservices Guidelines

### Single Team Ownership

Model each microservice as a **container** within a single system:

```
  ┌──────────────────┐
  │  ☺ Customer      │
  │  [Online shopper]│
  └────────┬─────────┘
           │
  Uses ────┘
  [HTTPS]
           │
           ▼
  ┌──────────────────────────────────────────────────────────────────────┐
  │  [E-commerce Platform]                                              │
  │                                                                     │
  │  ┌──────────────────┐                                               │
  │  │  <<container>>   │                                               │
  │  │  API Gateway     │                                               │
  │  │  [Kong]          │                                               │
  │  │  Routing, auth,  │                                               │
  │  │  rate limiting   │                                               │
  │  └────┬──────┬──────┘                                               │
  │       │      │      ──────────────────────────────────────          │
  │       │      │      │                    │                │         │
  │       ▼      ▼      ▼                    │                │         │
  │  ┌──────────┐ ┌──────────┐ ┌──────────┐  │                │         │
  │  │ Order    │ │ Product  │ │ User     │  │                │         │
  │  │ Service  │ │ Service  │ │ Service  │  │                │         │
  │  │ [Node.js]│ │ [Go]     │ │ [Java]   │  │                │         │
  │  └────┬─────┘ └────┬─────┘ └──┬───┬──┘  │                │         │
  │       │            │          │   │      │                │         │
  │       ▼            ▼          ▼   ▼      │                │         │
  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐     │         │
  │  │<<database>>││<<database>>││<<database>>││<<database>>│  │         │
  │  │ Order DB │ │ Product  │ │ User DB  │ │ Cache    │     │         │
  │  │[Postgres]│ │ DB       │ │[Postgres]│ │ [Redis]  │     │         │
  │  └──────────┘ │[MongoDB] │ └──────────┘ │ Sessions │     │         │
  │               └──────────┘              └──────────┘     │         │
  └──────────────────────────────────────────────────────────────────────┘
```

### Multi-Team Ownership

Promote microservices to **software systems** when owned by separate teams:

```
  ┌──────────────────┐                      ┌──────────────────┐
  │  ☺ Customer      │                      │  ☺ Admin         │
  │  [Online shopper]│                      │  [Store manager] │
  └────────┬─────────┘                      └────────┬─────────┘
           │                                         │
           ├──── Places orders ─────→ ╔══════════════╧══════════╗
           │                          ║  <<system>>             ║
           │                          ║  Order System           ║
           │                          ║  [Team Alpha]           ║
           │                          ╚═══════╤═════════════════╝
           │                                  │
           │                    Checks stock ─┘    Processes payment ─┐
           │                                  │                       │
           │                                  ▼                       ▼
           │                    ┌──────────────────┐  ┌ ─ ─ ─ ─ ─ ─ ─ ─┐
           │                    │  <<system>>      │  │ <<external>>     │
           │                    │  Inventory System│  │ Stripe           │
           │                    │  [Team Beta]     │  │ [Payment proc.]  │
           │                    └──────────────────┘  └ ─ ─ ─ ─ ─ ─ ─ ─┘
           │
           └──── Browses products ──→ ┌──────────────────┐
                                      │  <<system>>      │
                                      │  Product System  │
                                      │  [Team Beta]     │
                                      └──────────────────┘
```

### Event-Driven Architecture

Show individual topics/queues as containers, NOT a single "Kafka" box:

```
  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
  │ <<container>> │  │ <<container>> │  │ <<container>> │
  │ Order        │  │ Inventory    │  │ Payment      │
  │ Service      │  │ Service      │  │ Service      │
  │ [Java]       │  │ [Java]       │  │ [Java]       │
  └──┬───────┬───┘  └──┬───────┬───┘  └──┬───────────┘
     │       │         │       │         │
     │       │         ▲       │         ▲
     │    Publishes    │    Publishes    │
     │    [Avro]       │    [Avro]       │
     │       │     Consumes    │     Consumes
     │       │     [Avro]      │     [Avro]
     │       ▼         │       ▼         │
     │  ┌──────────────┴──┐  ┌┴──────────────┐
     │  │  <<queue>>      │  │  <<queue>>     │
     │  │  order.created  │  │  stock.reserved│
     │  │  [Kafka]        │  │  [Kafka]       │
     │  └─────────────────┘  └────────────────┘
     │
     │  Consumes payment.complete [Avro]
     │         │
     │         ▼
     │  ┌─────────────────┐
     │  │  <<queue>>      │
     │  │  payment.       │
     │  │  complete       │
     │  │  [Kafka]        │
     │  └─────────────────┘
     │         ▲
     │         │ Publishes [Avro]
     │         │
     └─────────┘ (from Payment Service)
```

---

## Cross-References Between Diagram Types

- **After Context Diagram**: "In the System Context diagram we identified systems X, Y, Z.
  Shall I create a Dynamic Diagram showing how these systems interact for a specific use case?"
- **Dynamic → ADR**: When complex integration patterns are identified in a Dynamic Diagram
  (e.g., Orchestration vs. Choreography), suggest an ADR for the pattern decision.
- **Dynamic → NFR**: From the Dynamic Diagram, derive performance requirements
  (e.g., "Step 3→4 must complete in < 100ms").

---

## Output Location

Write architecture documentation to `docs/architecture/` with this naming convention:

- `c4-context.md` - System context diagram
- `c4-containers.md` - Container diagram
- `c4-components-{feature}.md` - Component diagrams per feature
- `c4-deployment.md` - Deployment diagram
- `c4-dynamic-{flow}.md` - Dynamic diagrams for specific flows

## Audience-Appropriate Detail

| Audience | Recommended Diagrams |
|----------|---------------------|
| Executives | System Context only |
| Product Managers | Context + Container |
| Integration Architects | Context + Container + Dynamic |
| Solution Architects | Context + Container + Dynamic + key Components |
| Developers | All levels as needed |
| DevOps | Container + Deployment |

## References

- [references/c4-syntax.md](references/c4-syntax.md) - Complete ASCII C4 notation reference
- [references/common-mistakes.md](references/common-mistakes.md) - Anti-patterns to avoid
- [references/advanced-patterns.md](references/advanced-patterns.md) - Microservices, event-driven, deployment, dynamic patterns
