# C4 ASCII Diagram Notation Reference

Complete notation reference for C4 architecture diagrams in ASCII format.

## Table of Contents

1. [Diagram Types](#diagram-types)
2. [Element Types](#element-types)
3. [Relationship Types](#relationship-types)
4. [Boundaries](#boundaries)
5. [Deployment Nodes](#deployment-nodes)
6. [Dynamic Diagram Notation](#dynamic-diagram-notation)
7. [Layout Heuristics](#layout-heuristics)
8. [Legend](#legend)
9. [Complete Examples](#complete-examples)

## Diagram Types

| Type | Purpose | Key Characteristics |
|------|---------|---------------------|
| System Context | System in context with users and external systems | Central system highlighted with double-line box |
| Container | High-level technical building blocks | Shows apps, databases, services within boundaries |
| Component | Internal components within a container | Shows modules, classes, packages within container boundary |
| Dynamic | Request flows with numbered sequence | Numbered steps, temporal order, column-based layout |
| Deployment | Infrastructure and deployment nodes | Rounded deployment nodes containing containers |

## Element Types

### Person / Actor

```
┌──────────────────────┐
│  ☺ Name              │
│  [Role/Description]  │
└──────────────────────┘
```

External person (same box, note in description):
```
┌──────────────────────┐
│  ☺ Name              │
│  [External role]     │
└──────────────────────┘
```

### Software System

Central/scoped system (double-line border):
```
╔══════════════════════╗
║  <<system>>          ║
║  System Name         ║
║  [Short description] ║
╚══════════════════════╝
```

Internal system (single-line border):
```
┌──────────────────────┐
│  <<system>>          │
│  System Name         │
│  [Short description] │
└──────────────────────┘
```

External system (dashed border):
```
┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┐
│  <<external system>>  │
│  System Name          │
│  [Short description]  │
└ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┘
```

### Container

Standard container:
```
┌──────────────────────┐
│  <<container>>       │
│  Name                │
│  [Technology]        │
│  Description         │
└──────────────────────┘
```

Database container:
```
┌──────────────────────┐
│  <<database>>        │
│  Name                │
│  [Technology]        │
│  Description         │
└──────────────────────┘
```

Queue / Message Broker:
```
┌──────────────────────┐
│  <<queue>>           │
│  Name                │
│  [Technology]        │
│  Description         │
└──────────────────────┘
```

External container (dashed border):
```
┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┐
│  <<container>>        │
│  Name                 │
│  [Technology]         │
│  External dependency  │
└ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─┘
```

### Component

```
┌──────────────────────┐
│  <<component>>       │
│  Name                │
│  [Technology]        │
│  Description         │
└──────────────────────┘
```

Database component:
```
┌──────────────────────┐
│  <<component-db>>    │
│  Name                │
│  [Technology]        │
│  Description         │
└──────────────────────┘
```

## Relationship Types

### Synchronous Call

```
─────── Description ──────→
        [Protocol]
```

Example:
```
│────── Reads user data ──────→│
│       [REST/JSON, HTTPS]     │
```

### Asynchronous Call

```
─ ─ ─ ─ Description ─ ─ ─ ─→
        [Protocol]
```

Example:
```
│─ ─ ─  Publishes event  ─ ─ ─→│
│       [Kafka/Avro]             │
```

### Synchronous Response

```
←────── Response ─────────
        [Protocol]
```

### Asynchronous Response / Callback

```
←─ ─ ─  Response  ─ ─ ─ ─
        [Protocol]
```

### Bidirectional (use sparingly)

```
←────── Description ──────→
        [Protocol]
```

**Note:** Prefer separate unidirectional arrows showing call and response for clarity.

### Directional Hints

Use arrow characters to indicate direction:

```
Rightward:   ──────→
Leftward:    ←──────
Downward:    │
             ▼
Upward:      ▲
             │
```

## Boundaries

### System Boundary

```
┌──────────────────────────────────────┐
│  [System Name]                       │
│                                      │
│  ┌──────────────┐  ┌──────────────┐  │
│  │ Container A  │  │ Container B  │  │
│  └──────────────┘  └──────────────┘  │
└──────────────────────────────────────┘
```

### Container Boundary

```
┌──────────────────────────────────────┐
│  [Container Name]                    │
│                                      │
│  ┌──────────────┐  ┌──────────────┐  │
│  │ Component A  │  │ Component B  │  │
│  └──────────────┘  └──────────────┘  │
└──────────────────────────────────────┘
```

### Enterprise Boundary

```
╔══════════════════════════════════════╗
║  Enterprise Name                     ║
║                                      ║
║  ┌──────────────┐  ┌──────────────┐  ║
║  │ System A     │  │ System B     │  ║
║  └──────────────┘  └──────────────┘  ║
╚══════════════════════════════════════╝
```

### Trust Boundary

```
┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄
┊  Boundary Name                       ┊
┊                                      ┊
┊  ┌──────────────┐  ┌──────────────┐  ┊
┊  │ Element A    │  │ Element B    │  ┊
┊  └──────────────┘  └──────────────┘  ┊
┊                                      ┊
┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄
```

## Deployment Nodes

### Basic Deployment Node

```
╭──────────────────────────────────────╮
│  <<node>>                            │
│  Name [Type]                         │
│                                      │
│  ┌──────────────┐                    │
│  │ Container    │                    │
│  └──────────────┘                    │
╰──────────────────────────────────────╯
```

### Nested Deployment Nodes

```
╭─────────────────────────────────────────────────╮
│  <<node>> Data Center [Physical]                │
│                                                 │
│  ╭──────────────────────────────────────────╮   │
│  │  <<node>> Web Server [Ubuntu 22.04]      │   │
│  │                                          │   │
│  │  ┌──────────────────────────────────┐    │   │
│  │  │  <<container>>                   │    │   │
│  │  │  Application                     │    │   │
│  │  │  [Node.js]                       │    │   │
│  │  │  Serves API                      │    │   │
│  │  └──────────────────────────────────┘    │   │
│  ╰──────────────────────────────────────────╯   │
╰─────────────────────────────────────────────────╯
```

## Dynamic Diagram Notation

### Column-Based Layout

Dynamic diagrams use a column-based layout similar to sequence diagrams:

```
  ┌──────────┐    ┌──────────────┐    ┌──────────────┐
  │  ☺ Actor │    │ <<container>> │    │ <<database>> │
  │  [Role]  │    │  Service     │    │  Database    │
  └────┬─────┘    └──────┬───────┘    └──────┬───────┘
       │                 │                    │
       │── 1. Action ──→│                    │
       │   [Protocol]    │                    │
       │                 │── 2. Query ──────→│
       │                 │   [JDBC/SQL]       │
       │                 │                    │
       │                 │←── Result ────────│
       │←── Response ───│                    │
       │   [Protocol]    │                    │
```

### Numbered Steps (MANDATORY)

Every interaction **must** have a sequential number:

```
       │── 1. Submit request ──→│
       │                        │── 2. Validate ──→│
       │                        │←── OK ──────────│
       │                        │── 3. Persist ───→│
       │                        │←── Stored ──────│
       │←── 4. Confirmation ──│
```

### Synchronous vs. Asynchronous

Synchronous call (solid line):
```
       │────── Description ──────→│
       │       [Protocol]          │
```

Asynchronous call (dashed line):
```
       │─ ─ ─  Description  ─ ─ ─→│
       │       [Protocol]           │
```

### Self-Call

```
       │──┐ 3. Validation
       │  │    [internal]
       │←─┘
```

### Grouping: Loops

```
       ╔══[loop: for each item]════════════════════╗
       ║  │── 4. Check item ────→│                 ║
       ║  │←── Stock level ─────│                 ║
       ╚═══════════════════════════════════════════╝
```

### Grouping: Alternatives

```
       ╔══[alt: customer exists]═══════════════════╗
       ║  │── 5a. Load customer data ──→│          ║
       ╠══[else]═══════════════════════════════════╣
       ║  │── 5b. Create customer ─────→│          ║
       ╚═══════════════════════════════════════════╝
```

### Grouping: Optional

```
       ╔══[opt: has discount code]═════════════════╗
       ║  │── 6. Apply discount ──→│               ║
       ║  │←── Updated price ─────│               ║
       ╚═══════════════════════════════════════════╝
```

### System Boundaries in Dynamic Diagrams

```
       │ System A                     │ System B                    │ External
       │                              │                             │
  ┌─────────┐  ┌──────────────┐  ┌──────────┐  ┌──────────┐  ┌ ─ ─ ─ ─ ─┐
  │ Frontend │  │ API-Gateway  │  │ Backend  │  │ Database │  │ Ext. Svc  │
  └────┬─────┘  └──────┬───────┘  └────┬─────┘  └────┬─────┘  └ ─ ─┬─ ─ ─┘
       │               │               │              │              │
```

## Layout Heuristics

### General Layout

1. **Central system in the middle** - Place the system under focus at the center
2. **Actors on top or left** - Persons/roles that trigger interactions
3. **External systems on the outside** - Right or bottom edges
4. **Trust boundaries as enclosing frames** - Dashed rectangle around grouped elements
5. **Minimum 2 characters spacing** between elements
6. **Consistent box widths** for elements of the same category

### Dynamic Diagram Layout

1. **Trigger leftmost** - The initiating actor/event on the far left
2. **Left to right flow** - From trigger toward target systems
3. **Frequently interacting elements side by side** - Minimize line crossing
4. **Max 7±2 elements** per dynamic diagram - Split into sub-flows if exceeded
5. **System boundaries above columns** - Shows which elements belong to which system

### Minimizing Line Crossings

- Group strongly connected elements close together
- Place the central system in the middle of its connections
- Reorder elements to avoid crossing lines
- For dynamic diagrams, arrange participants by call order

## Legend

Always include a legend below diagrams:

### General Legend

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
║  ┄┄┄      = Trust Boundary                               ║
╚══════════════════════════════════════════════════════════╝
```

### Dynamic Diagram Legend (additional)

```
╔══════════════════════════════════════════════════════════╗
║  LEGEND (Dynamic Diagram)                                ║
╠══════════════════════════════════════════════════════════╣
║  [n]      = Step number (temporal order)                 ║
║  ───→     = Synchronous call                             ║
║  ─ ─→     = Asynchronous call                            ║
║  ←───     = Synchronous response                         ║
║  ←─ ─     = Asynchronous response / Callback             ║
║  ╔══[x]═╗ = Grouping (loop/alt/opt)                      ║
╚══════════════════════════════════════════════════════════╝
```

## Complete Examples

### C4 Context Example

```
                         ╔══════════════════════════════════════╗
                         ║  Bank                                ║
                         ║                                      ║
  ┌──────────────────┐   ║   ╔══════════════════════════╗       ║
  │  ☺ Banking       │   ║   ║  <<system>>              ║       ║
  │  Customer        │──────→║  Internet Banking System  ║       ║
  │  [Has bank       │   ║   ║  [View accounts, make    ║       ║
  │   accounts]      │   ║   ║   payments]              ║       ║
  └──────────────────┘   ║   ╚═══════╤══════════╤═══════╝       ║
                         ║           │          │               ║
                         ║  Reads/ ──┘          └── Sends       ║
                         ║  writes                  emails      ║
                         ║  [JDBC]                  [SMTP]      ║
                         ║           │          │               ║
                         ║           ▼          ▼               ║
                         ║  ┌──────────────┐ ┌──────────────┐   ║
                         ║  │ <<system>>   │ │ <<system>>   │   ║
                         ║  │ Mainframe    │ │ E-mail System│   ║
                         ║  │ [Core banking│ │ [MS Exchange]│   ║
                         ║  │  data]       │ │              │   ║
                         ║  └──────────────┘ └──────┬───────┘   ║
                         ╚══════════════════════════╧═══════════╝
                                                    │
                                          Sends ────┘
                                          emails to
                                                    │
                                                    ▼
                                       ┌──────────────────┐
                                       │  ☺ Banking       │
                                       │  Customer        │
                                       └──────────────────┘
```

### C4 Container Example

```
  ┌──────────────────┐
  │  ☺ Customer      │
  │  [Bank customer  │
  │   with accounts] │
  └────────┬─────────┘
           │
           ├─── Uses [HTTPS] ──────────────────────────────┐
           │                                                │
           ▼                                                ▼
  ┌─────────────────────────────────────────────────────────────────────┐
  │  [Internet Banking]                                                 │
  │                                                                     │
  │  ┌──────────────────┐  ┌──────────────────┐                         │
  │  │  <<container>>   │  │  <<container>>   │                         │
  │  │  Single-Page App │  │  Mobile App      │                         │
  │  │  [JS, Angular]   │  │  [C#, Xamarin]   │                         │
  │  │  Banking UI      │  │  Mobile banking  │                         │
  │  └────────┬─────────┘  └────────┬─────────┘                         │
  │           │                     │                                   │
  │           └──── Uses ───────────┘                                   │
  │                [JSON/HTTPS]                                         │
  │                     │                                               │
  │                     ▼                                               │
  │           ┌──────────────────┐         ┌──────────────────┐         │
  │           │  <<container>>   │────────→│  <<database>>    │         │
  │           │  API Application │ Reads/  │  Database        │         │
  │           │  [Java, Spring]  │ writes  │  [SQL Server]    │         │
  │           │  Banking API     │ [JDBC]  │  User data, logs │         │
  │           └────────┬─────────┘         └──────────────────┘         │
  └────────────────────┼───────────────────────────────────────────────┘
                       │
           ┌───────────┼───────────────┐
           │           │               │
           ▼           ▼               │
  ┌ ─ ─ ─ ─ ─ ─ ─┐  ┌ ─ ─ ─ ─ ─ ─ ─┐│
  │ <<external>>   │  │ <<external>>   ││
  │ Mainframe      │  │ E-mail System  ││
  │ [Core banking] │  │ [MS Exchange]  ││
  └ ─ ─ ─ ─ ─ ─ ─┘  └ ─ ─ ─ ─ ─ ─ ─┘│
  Uses [XML/HTTPS]    Sends [SMTP]      │
```

### C4 Component Example

```
  ┌──────────────────┐                   ┌ ─ ─ ─ ─ ─ ─ ─ ─┐
  │  <<container>>   │                   │  <<external>>    │
  │  Single Page App │                   │  Mainframe       │
  │  [Angular]       │                   │  [Core banking]  │
  └────────┬─────────┘                   └ ─ ─ ─ ─▲─ ─ ─ ─┘
           │                                       │
           │                                  Uses │
           │                                [XML/HTTPS]
           │                                       │
           │   ┌───────────────────────────────────┼──────────────────┐
           │   │  [API Application]                │                  │
           │   │                                   │                  │
           │   │  ┌──────────────────┐  ┌──────────┴───────────────┐  │
           ├──→│  │  <<component>>   │  │  <<component>>           │  │
           │   │  │  Sign In         │  │  Mainframe Facade        │  │
     Uses  │   │  │  Controller      │  │  [Spring Bean]           │  │
  [JSON/HTTPS] │  │  [Spring MVC]    │  │  Mainframe integration   │  │
           │   │  └────────┬─────────┘  └──────────────────────────┘  │
           │   │           │                         ▲                │
           ├──→│  ┌────────▼─────────┐               │                │
           │   │  │  <<component>>   │          Uses │                │
           │   │  │  Accounts        │               │                │
           │   │  │  Controller      ├───────────────┘                │
           │   │  │  [Spring MVC]    │                                │
           │   │  └──────────────────┘                                │
           │   │                                                      │
           │   │  ┌──────────────────┐         ┌──────────────────┐   │
           │   │  │  <<component>>   │         │  <<database>>    │   │
           │   │  │  Security        │────────→│  Database        │   │
           │   │  │  Component       │ Reads/  │  [SQL Server]    │   │
           │   │  │  [Spring Bean]   │ writes  │  User data       │   │
           │   │  └──────────────────┘ [JDBC]  └──────────────────┘   │
           │   └──────────────────────────────────────────────────────┘
```

### C4 Dynamic Example: User Sign In

```
  Title: Dynamic Diagram - User Sign In Flow

  ┌──────────────┐  ┌────────────────────────────────────────┐  ┌──────────────┐
  │ <<container>> │  │ [API Application]                      │  │ <<database>> │
  │ Single-Page  │  │                                        │  │ Database     │
  │ App          │  │ ┌───────────────┐  ┌────────────────┐  │  │ [SQL Server] │
  │ [Angular]    │  │ │<<component>>  │  │ <<component>>  │  │  │ User         │
  │ Banking UI   │  │ │Sign In Ctrl   │  │ Security Comp. │  │  │ credentials  │
  └──────┬───────┘  │ │[Spring MVC]   │  │ [Spring Bean]  │  │  └──────┬───────┘
         │          │ └──────┬────────┘  └───────┬────────┘  │         │
         │          └────────┼───────────────────┼───────────┘         │
         │                   │                   │                     │
         │── 1. Submit ─────→│                   │                     │
         │   credentials     │                   │                     │
         │   [JSON/HTTPS]    │                   │                     │
         │                   │── 2. Validate ───→│                     │
         │                   │                   │                     │
         │                   │                   │── 3. Query user ──→│
         │                   │                   │   [JDBC]            │
         │                   │                   │                     │
         │                   │                   │←── User record ────│
         │                   │←── Auth result ──│                     │
         │←── JWT token ────│                   │                     │
         │   [JSON/HTTPS]    │                   │                     │
```

### C4 Deployment Example

```
  Title: Deployment Diagram - Production

  ╭──────────────────────────────────────╮
  │  <<node>> Customer's Mobile          │
  │  [iOS/Android]                       │
  │  ┌──────────────────────────────┐    │
  │  │  <<container>> Mobile App    │    │
  │  │  [Xamarin] Mobile banking    │    │
  │  └────────────┬─────────────────┘    │
  ╰───────────────┼──────────────────────╯
                  │ API calls [HTTPS]
  ╭───────────────┼──────────────────────╮
  │  <<node>> Customer's Browser         │
  │  [Chrome/Firefox]                    │
  │  ┌──────────────────────────────┐    │
  │  │  <<container>> SPA           │    │
  │  │  [Angular] Web banking       │    │
  │  └────────────┬─────────────────┘    │
  ╰───────────────┼──────────────────────╯
                  │ API calls [HTTPS]
                  ▼
  ╭──────────────────────────────────────────────────────╮
  │  <<node>> Data Center [AWS]                          │
  │                                                      │
  │  ╭────────────────────────╮  ╭─────────────────────╮ │
  │  │ <<node>> Web Tier [EC2]│  │ <<node>> Data Tier  │ │
  │  │                        │  │ [RDS]               │ │
  │  │ ┌────────────────────┐ │  │ ┌─────────────────┐ │ │
  │  │ │ <<container>>      │ │  │ │ <<database>>    │ │ │
  │  │ │ API                │─┼─→│ │ Database        │ │ │
  │  │ │ [Spring Boot]      │ │  │ │ [PostgreSQL]    │ │ │
  │  │ │ Banking API        │ │  │ │ Banking data    │ │ │
  │  │ └────────────────────┘ │  │ └─────────────────┘ │ │
  │  ╰────────────────────────╯  ╰─────────────────────╯ │
  ╰──────────────────────────────────────────────────────╯
```
