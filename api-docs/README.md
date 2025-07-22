# Hibernate ORM API Documentation

This directory contains comprehensive OpenAPI documentation for all Hibernate ORM APIs. While Hibernate ORM is a Java Object-Relational Mapping framework (not a REST service), these OpenAPI specifications document the Java APIs in a structured, accessible format for developers.

## 📚 API Documentation Files

### 1. Core Session Management API
**File:** `hibernate-core-session-api.yaml`

Documents the fundamental Hibernate APIs for:
- **SessionFactory**: Factory for creating and managing sessions
- **Session**: Main runtime interface for persistence operations  
- **Transaction**: Transaction management and lifecycle
- **Entity Operations**: CRUD operations (Create, Read, Update, Delete)

**Key APIs Covered:**
- Session lifecycle management (open, close, flush, clear)
- Entity persistence operations (persist, merge, find, remove, refresh)
- Transaction management (begin, commit, rollback)
- SessionFactory creation and configuration

---

### 2. Query API
**File:** `hibernate-query-api.yaml`

Documents Hibernate's comprehensive query capabilities:
- **HQL Queries**: Hibernate Query Language operations
- **Criteria Queries**: Type-safe programmatic queries
- **Native Queries**: Direct SQL query support
- **Query Execution**: Various result retrieval methods
- **Parameter Binding**: Named and positional parameter handling

**Key APIs Covered:**
- Query creation (HQL, Criteria, Native SQL, Named queries)
- Parameter binding and configuration
- Result retrieval (list, single, unique, stream, scrollable)
- Query optimization and caching

---

### 3. Schema Management API  
**File:** `hibernate-schema-api.yaml`

Documents database schema management capabilities:
- **Schema Manager**: Core schema operations
- **DDL Generation**: Database schema DDL generation
- **Schema Validation**: Schema correctness validation
- **Schema Migration**: Schema evolution and updates
- **Metadata Extraction**: Database metadata inspection

**Key APIs Covered:**
- Schema creation, dropping, and migration
- DDL script generation (CREATE, DROP, UPDATE)
- Schema validation against mappings
- Database metadata extraction (tables, columns, indexes, sequences)

---

### 4. Extended Modules API
**File:** `hibernate-modules-api.yaml`

Documents specialized Hibernate modules:
- **Envers Auditing**: Entity auditing and revision tracking
- **Spatial Operations**: GIS and spatial data support
- **Vector Operations**: Vector embeddings and similarity search
- **Cache Management**: Second-level cache operations
- **Statistics**: Runtime metrics and performance monitoring

**Key APIs Covered:**
- Audit trail management and revision queries
- Spatial predicates and geometry operations
- Vector similarity search and distance calculations
- Cache eviction and statistics
- Performance metrics and monitoring

---

### 5. Tooling API
**File:** `hibernate-tooling-api.yaml`

Documents development and build-time tools:
- **Metamodel Generator**: Static metamodel generation
- **Build Plugins**: Gradle, Maven, and Ant integrations
- **Connection Pools**: HikariCP, C3P0, and Agroal configuration
- **Development Tools**: Debugging and monitoring utilities

**Key APIs Covered:**
- Annotation processing and metamodel generation
- Bytecode enhancement and schema generation
- Connection pool configuration and monitoring
- SQL logging, JFR events, and Micrometer metrics

---

## 🏗️ Architecture Overview

### Core Components
```
SessionFactory (Root)
├── Session (Persistence Context)
│   ├── Transaction (Transaction Management)
│   ├── Query (HQL/Criteria/Native SQL)
│   └── Entity Operations (CRUD)
├── Cache (Second-level Caching)
├── Statistics (Performance Metrics)
└── SchemaManager (DDL Operations)
```

### Extended Modules
```
Hibernate Modules
├── Envers (Auditing)
├── Spatial (GIS Support)
├── Vector (Embeddings)
├── JCache (Caching)
├── Micrometer (Metrics)
├── JFR (Flight Recorder)
└── Connection Pools (HikariCP/C3P0/Agroal)
```

### Development Tools
```
Tooling
├── Metamodel Generator
├── Build Plugins (Gradle/Maven/Ant)
├── Bytecode Enhancement
└── Development Utilities
```

## 🚀 Getting Started

### Basic Usage Pattern
1. **Configure SessionFactory** - Set up database connection and mappings
2. **Open Session** - Create a persistence context
3. **Begin Transaction** - Start a database transaction
4. **Perform Operations** - Execute queries and entity operations
5. **Commit/Rollback** - Complete or abort the transaction
6. **Close Session** - Release resources

### Example Workflow (Conceptual)
```
POST /session-factory                    # Create SessionFactory
POST /session-factory/{id}/session       # Open Session
POST /session/{id}/transaction           # Begin Transaction
POST /session/{id}/entity                # Persist Entity
GET  /session/{id}/entity/{type}/{id}    # Find Entity
POST /session/{id}/transaction/commit    # Commit Transaction
DELETE /session/{id}/close               # Close Session
```

## 📖 Documentation Format

These OpenAPI specifications use standard HTTP methods and REST patterns to represent Java method calls:

- **GET**: Retrieval operations (find, query, get)
- **POST**: Creation operations (persist, begin, create)
- **PUT**: Update operations (merge, update, set)
- **DELETE**: Removal operations (remove, evict, close)

### Path Structure
- `/session-factory/{id}` - SessionFactory operations
- `/session/{id}` - Session-specific operations  
- `/query/{id}` - Query-specific operations
- `/cache/{id}` - Cache operations
- `/schema-manager/{id}` - Schema operations

### Response Codes
- **200**: Successful operation
- **201**: Resource created successfully
- **204**: Operation completed (no content)
- **400**: Invalid request/parameters
- **404**: Resource not found
- **409**: Conflict (e.g., unique constraint violation)

## 🔧 Configuration Examples

### SessionFactory Configuration
```yaml
hibernateProperties:
  hibernate.dialect: "org.hibernate.dialect.PostgreSQLDialect"
  hibernate.hbm2ddl.auto: "update"
  hibernate.show_sql: "true"
  hibernate.format_sql: "true"
```

### Query Configuration
```yaml
maxResults: 10
firstResult: 0
timeout: 30000
cacheable: true
cacheRegion: "query-cache"
flushMode: "AUTO"
```

### Connection Pool Configuration (HikariCP)
```yaml
jdbcUrl: "jdbc:postgresql://localhost:5432/mydb"
username: "user"
password: "password"
maximumPoolSize: 20
connectionTimeout: 30000
```

## 🎯 Use Cases

### Common Development Scenarios
1. **Application Development**: Use Session and Query APIs
2. **Schema Management**: Use Schema Management API
3. **Performance Monitoring**: Use Statistics and Cache APIs
4. **Auditing Requirements**: Use Envers Auditing API
5. **Spatial Applications**: Use Spatial Operations API
6. **AI/ML Applications**: Use Vector Operations API
7. **Build Integration**: Use Tooling APIs

### Enterprise Features
- **Multi-tenancy**: Session-per-tenant isolation
- **Caching**: Second-level cache for performance
- **Auditing**: Complete change tracking
- **Monitoring**: Comprehensive metrics collection
- **Scalability**: Connection pooling and optimization

## 📚 Additional Resources

- [Hibernate ORM Official Documentation](https://hibernate.org/orm/documentation/)
- [Hibernate User Guide](https://docs.jboss.org/hibernate/orm/current/userguide/html_single/Hibernate_User_Guide.html)
- [Jakarta Persistence Specification](https://jakarta.ee/specifications/persistence/)
- [Hibernate Community](https://hibernate.org/community/)

## 📝 Notes

**Important**: These OpenAPI specifications document Java library APIs, not actual REST endpoints. They serve as comprehensive API documentation in a familiar format. The actual Hibernate APIs are invoked through Java method calls in your application code.

**Version**: Hibernate ORM 7.0.0
**License**: Apache-2.0
**Maintained by**: Hibernate Team