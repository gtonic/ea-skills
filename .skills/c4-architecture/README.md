# C4 Architecture Skill

Generate software architecture documentation using C4 model diagrams in ASCII notation.

## Purpose

This skill helps you create professional architecture documentation using the C4 (Context, Container, Component, Code) model. It generates ASCII diagrams that visualize your system's architecture at different abstraction levels, making it easy to communicate design decisions to different audiences. It includes dedicated **C4 Dynamic Diagram** support for documenting detailed interface communication and system interactions — essential for Integration Architects and Solution Architects.

## When to Use

Use this skill when you need to:

- Create architecture diagrams for documentation
- Visualize software structure and relationships
- Document system architecture for different audiences (executives, developers, DevOps)
- Generate C4 Context, Container, Component, or Deployment diagrams
- **Document interface communication and system interactions** (C4 Dynamic Diagrams)
- **Show temporal request flows** with numbered interaction steps
- Document microservices or event-driven architectures
- **Analyze integration scenarios** (onboarding flows, order processes, data synchronization)

**Trigger phrases**: "architecture diagram", "C4 diagram", "system context", "container diagram", "component diagram", "deployment diagram", "dynamic diagram", "document architecture", "visualize architecture", "interface communication", "Schnittstellenkommunikation", "request flow", "system interaction", "sequence"

## How It Works

The skill follows a systematic workflow:

1. **Understand scope** - Determines which C4 level(s) are needed based on your audience
2. **Analyze codebase** - Explores the system to identify components, containers, and relationships
3. **Generate diagrams** - Creates ASCII C4 diagrams at appropriate abstraction levels
4. **Document** - Writes diagrams to markdown files with explanatory context

### C4 Diagram Levels

| Level | Diagram Type | Audience | Shows | When to Create |
|-------|-------------|----------|-------|----------------|
| 1 | **Context** | Everyone | System + external actors | Always (required) |
| 2 | **Container** | Technical | Apps, databases, services | Always (required) |
| 3 | **Component** | Developers | Internal components | Only if adds value |
| 4 | **Deployment** | DevOps | Infrastructure nodes | For production systems |
| - | **Dynamic** | Integration/Solution Architects | Request flows (numbered, temporal) | For interface communication & complex workflows |

**Key Insight**: "Context + Container diagrams are sufficient for most software development teams." Only create Component/Code diagrams when they genuinely add value. Use **Dynamic Diagrams** when temporal interaction sequences or detailed interface communication must be documented.

## Key Features

- **Multiple abstraction levels** - Generate Context, Container, Component, Deployment, and Dynamic diagrams
- **C4 Dynamic Diagrams** - Detailed interface communication with numbered interaction sequences
- **Audience-appropriate detail** - Automatically selects the right level of detail for your audience
- **Best practices built-in** - Follows C4 model conventions and anti-patterns to avoid
- **Microservices support** - Special handling for microservices and event-driven architectures
- **ASCII notation** - Universal, tool-independent format that renders everywhere
- **Comprehensive references** - Includes notation guide, common mistakes, and advanced patterns

## Usage Examples

### Example 1: Document a Simple Web Application

**Request**: "Create architecture diagrams for my workout tracker app"

**Output**: Generates:
- System Context diagram showing users and external systems
- Container diagram showing the Vue.js SPA, state management (Pinia), and IndexedDB

```
                         ┌──────────────────┐
                         │  ☺ User          │
                         │  [Tracks workouts│
                         │   and exercises] │
                         └────────┬─────────┘
                                  │
                        Uses ─────┘
                        [HTTPS]
                                  │
                                  ▼
                    ╔══════════════════════════╗
                    ║  <<system>>              ║
                    ║  Workout Tracker         ║
                    ║  [Vue PWA for tracking   ║
                    ║   strength & CrossFit]   ║
                    ╚═════════════╤════════════╝
                                  │
                    Persists ─────┘
                    data to [IndexedDB]
                                  │
                                  ▼
                    ┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┐
                    │  <<external system>>     │
                    │  Web Browser             │
                    │  [Stores data in         │
                    │   IndexedDB]             │
                    └ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┘
```

### Example 2: Document a Microservices Architecture

**Request**: "Create a container diagram for our e-commerce microservices"

**Output**: Generates a Container diagram showing:
- Order Service with PostgreSQL
- Inventory Service with MongoDB
- Message queues for inter-service communication

```
  ┌──────────────────────────────────────────────────────┐
  │  [E-commerce Platform]                               │
  │                                                      │
  │  ┌──────────────────┐    ┌──────────────────┐        │
  │  │  <<container>>   │    │  <<database>>    │        │
  │  │  Order Service   │───→│  Order DB        │        │
  │  │  [Spring Boot]   │    │  [PostgreSQL]    │        │
  │  │  Order processing│    │  Order data      │        │
  │  └──────────────────┘    └──────────────────┘        │
  │                                                      │
  │  ┌──────────────────┐    ┌──────────────────┐        │
  │  │  <<container>>   │    │  <<database>>    │        │
  │  │  Inventory Svc   │───→│  Inventory DB    │        │
  │  │  [Node.js]       │    │  [MongoDB]       │        │
  │  │  Stock management│    │  Stock data      │        │
  │  └──────────────────┘    └──────────────────┘        │
  └──────────────────────────────────────────────────────┘
```

### Example 3: Show a Request Flow (C4 Dynamic Diagram)

**Request**: "Diagram the user sign-in flow"

**Output**: Generates a Dynamic diagram with numbered steps:

```
  ┌──────────────┐  ┌──────────────────────────────────────────┐  ┌──────────────┐
  │ <<container>> │  │ [API Application]                        │  │ <<database>> │
  │ Single-Page  │  │                                          │  │ Database     │
  │ App          │  │  ┌───────────────┐  ┌─────────────────┐  │  │ [PostgreSQL] │
  │ [React]      │  │  │ <<component>> │  │  <<component>>  │  │  │ User         │
  │ Banking UI   │  │  │ Sign In       │  │  Security       │  │  │ credentials  │
  │              │  │  │ Controller    │  │  Service         │  │  └──────┬───────┘
  └──────┬───────┘  │  │ [Express]     │  │  [JWT]          │  │         │
         │          │  └──────┬────────┘  └────────┬────────┘  │         │
         │          └─────────┼────────────────────┼───────────┘         │
         │                    │                    │                     │
         │── 1. Submit ──────→│                    │                     │
         │   credentials      │                    │                     │
         │   [JSON/HTTPS]     │                    │                     │
         │                    │── 2. Validate ────→│                     │
         │                    │                    │── 3. Query user ──→│
         │                    │                    │   [SQL]             │
         │                    │                    │←── User data ──────│
         │                    │←── Auth result ───│                     │
         │←── JWT Token ─────│                    │                     │
```

### Example 4: Document Interface Communication (Event-Driven)

**Request**: "Show the order processing flow across our microservices"

**Output**: Generates a Dynamic diagram showing async event flow:

```
  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
  │ <<container>> │  │ <<container>> │  │ <<container>> │  │ <<container>> │
  │ Order        │  │ Inventory    │  │ Payment      │  │ Shipping     │
  │ Service      │  │ Service      │  │ Service      │  │ Service      │
  │ [Java]       │  │ [Go]         │  │ [Node.js]    │  │ [Python]     │
  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘
         │                 │                  │                  │
         │─ ─ 1. Publish order.created ─ ─ ─→│                  │
         │   [Kafka/Avro]  │                  │                  │
         │          2. Consume ←─ ─ ─ ─ ─ ─ ─┘                  │
         │          order.created              │                  │
         │                 │─ ─ 3. Publish inventory.reserved ──→│
         │                 │   [Kafka/Avro]   │                  │
         │                 │           4. Consume ←─ ─ ─ ─ ─ ─ ─┘
         │                 │           inventory.reserved         │
         │                 │                  │─ ─ 5. Publish ──→│
         │                 │                  │   payment.done    │
         │                 │                  │   [Kafka/Avro]    │
```

### Example 5: Document Production Deployment

**Request**: "Create a deployment diagram for our AWS infrastructure"

**Output**: Generates a Deployment diagram showing:
- Browser deployment node
- AWS Cloud with ECS and RDS nodes
- Infrastructure relationships

```
  ╭───────────────────────────────────────╮
  │  <<node>> Customer Browser            │
  │  [Chrome/Firefox]                     │
  │  ┌──────────────────┐                 │
  │  │  <<container>>   │                 │
  │  │  SPA [React]     │                 │
  │  └────────┬─────────┘                 │
  ╰───────────┼───────────────────────────╯
              │ API calls [HTTPS]
              ▼
  ╭───────────────────────────────────────────────────╮
  │  <<node>> AWS Cloud [us-east-1]                   │
  │  ╭─────────────────────╮  ╭─────────────────────╮│
  │  │ <<node>> ECS Fargate│  │ <<node>> RDS        ││
  │  │ ┌──────────────────┐│  │ ┌──────────────────┐││
  │  │ │ <<container>>    ││  │ │ <<database>>     │││
  │  │ │ API Service      ││─→│ │ Database         │││
  │  │ │ [Node.js]        ││  │ │ [PostgreSQL]     │││
  │  │ └──────────────────┘│  │ └──────────────────┘││
  │  ╰─────────────────────╯  ╰─────────────────────╯│
  ╰───────────────────────────────────────────────────╯
```

## Output Location

Architecture documentation is written to `docs/architecture/` with this naming convention:

- `c4-context.md` - System context diagram
- `c4-containers.md` - Container diagram
- `c4-components-{feature}.md` - Component diagrams per feature
- `c4-deployment.md` - Deployment diagram
- `c4-dynamic-{flow}.md` - Dynamic diagrams for specific flows

## Best Practices

### Essential Rules

1. **Every element must have**: Name, Type, Technology (where applicable), and Description
2. **Use unidirectional arrows** - Show call and response separately for clarity
3. **Label arrows with action verbs** - "Sends email using", "Reads from", not just "uses"
4. **Include technology labels** - "JSON/HTTPS", "JDBC", "gRPC"
5. **Stay under 20 elements per diagram** - Split complex systems into multiple diagrams

### Dynamic Diagram Best Practices

1. **Number every step** - Temporal order must be immediately visible
2. **One use case per diagram** - Don't mix multiple flows
3. **Show protocols** - Integration architects need to see REST/JSON, SOAP/XML, AMQP, gRPC, etc.
4. **Mark sync vs. async** - Solid lines for sync, dashed for async
5. **Include responses** - Show relevant return data, not just calls
6. **Max 7±2 elements** - Split into sub-flows if more elements are needed

### Clarity Guidelines

1. **Start at Level 1** - Context diagrams help frame the system scope
2. **One diagram per file** - Keep diagrams focused on a single abstraction level
3. **Meaningful names** - Use descriptive names (e.g., `Order Service` not `Svc1`)
4. **Concise descriptions** - Keep descriptions under 50 characters when possible
5. **Always include a title** - "System Context diagram for [System Name]"

## Audience-Appropriate Detail

| Audience | Recommended Diagrams |
|----------|---------------------|
| Executives | System Context only |
| Product Managers | Context + Container |
| Integration Architects | Context + Container + **Dynamic** |
| Solution Architects | Context + Container + **Dynamic** + key Components |
| Developers | All levels as needed |
| DevOps | Container + Deployment |

## References

The skill includes comprehensive reference documentation:

- **c4-syntax.md** - Complete ASCII C4 notation reference
- **common-mistakes.md** - Anti-patterns to avoid
- **advanced-patterns.md** - Microservices, event-driven, deployment, dynamic patterns

## Additional Resources

- [C4 Model](https://c4model.com/) - Official C4 model documentation
- [Structurizr](https://structurizr.com/) - C4 model tooling by Simon Brown
