---
description: Design comprehensive database schemas and implement robust ETL pipelines with advanced data processing, transformation capabilities, and performance optimization. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
  - vscodeAPI
---

**🤖 CHATMODE ACTIVATION:** This prompt automatically activates the `data-engineer` chatmode.
**📋 CHATMODE CONTEXT:** The activated chatmode will read copilot.instructions.md and adapt to project requirements.
**🔄 GITHUB COPILOT INTEGRATION:** All tasks will be managed through GitHub Copilot Chat workflows.

# Database Design and ETL Implementation

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Database Schema Design
- **Data Modeling Excellence**: Design normalized database schemas with proper entity relationships, constraints, and business rule enforcement
- **Performance Optimization**: Implement indexing strategies, query optimization, and database-specific performance enhancements
- **Scalability Planning**: Design schemas that support horizontal and vertical scaling with partitioning and sharding strategies
- **Compliance Integration**: Incorporate industry-specific compliance requirements including audit trails, data retention, and privacy controls

### Advanced ETL Pipeline Implementation
- **Data Extraction Strategies**: Implement robust data extraction from multiple sources including databases, APIs, files, and real-time streams
- **Transformation Processing**: Design efficient data transformation pipelines with validation, cleansing, enrichment, and business rule application
- **Load Optimization**: Implement high-performance data loading with bulk operations, upsert patterns, and error handling
- **Pipeline Orchestration**: Create automated ETL workflows with scheduling, monitoring, and failure recovery mechanisms

### Data Quality and Governance
- **Data Validation Framework**: Implement comprehensive data quality checks with validation rules and anomaly detection
- **Error Handling and Recovery**: Design robust error handling with data quarantine, retry mechanisms, and manual intervention workflows
- **Audit and Lineage Tracking**: Create complete data lineage tracking with audit trails and change history management
- **Performance Monitoring**: Implement comprehensive monitoring for ETL performance, data quality metrics, and system health

### Technology Stack Integration
- **Database Technology Adaptation**: Optimize for specific database systems with vendor-specific features and best practices
- **Framework Integration**: Integrate with backend frameworks and ORM technologies for seamless application development
- **Cloud and On-Premise Support**: Design solutions that work across cloud platforms and on-premise infrastructure
- **Real-time and Batch Processing**: Implement both real-time streaming and batch processing capabilities based on business requirements

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Requirements Analysis and Technology Selection
```
1. Read copilot.instructions.md to extract:
   - Database technology preferences and constraints
   - Business domain data modeling requirements
   - Performance and scalability expectations
   - Compliance and regulatory requirements

2. Data Architecture Assessment:
   - Analyze data volume and growth projections
   - Evaluate query patterns and access requirements
   - Assess integration and ETL complexity needs
   - Review real-time vs batch processing requirements
```

### 2. Database Schema Design and Optimization
```
1. Conceptual Data Modeling:
   - Identify business entities and their relationships
   - Define business rules and data constraints
   - Map entity relationships and cardinalities
   - Plan data lifecycle and retention strategies

2. Physical Database Design:
   - Design normalized schema with proper indexing
   - Implement partitioning and sharding strategies
   - Configure performance optimization settings
   - Set up backup and recovery procedures
```

### 3. ETL Pipeline Architecture and Implementation
```
1. Data Source Analysis and Integration:
   - Identify all data sources and formats
   - Design data extraction strategies and scheduling
   - Implement source system connectivity and authentication
   - Plan incremental vs full data extraction patterns

2. Transformation Logic Design:
   - Design data transformation rules and business logic
   - Implement data validation and quality checks
   - Create error handling and data quarantine processes
   - Set up data enrichment and aggregation workflows
```

### 4. Data Quality and Monitoring Implementation
```
1. Quality Assurance Framework:
   - Implement data validation rules and quality metrics
   - Create anomaly detection and alerting systems
   - Design data profiling and quality reporting
   - Set up manual data quality review processes

2. Performance and Monitoring:
   - Implement ETL performance monitoring and alerting
   - Create data lineage tracking and audit trails
   - Set up system health monitoring and diagnostics
   - Design capacity planning and scaling procedures
```

### 5. Testing, Deployment, and Maintenance
```
1. Testing Strategy Implementation:
   - Create unit tests for transformation logic
   - Implement integration tests for end-to-end data flows
   - Set up performance testing for ETL pipelines
   - Create data quality validation testing

2. Deployment and Operations:
   - Set up automated deployment and configuration management
   - Implement backup and disaster recovery procedures
   - Create maintenance and optimization workflows
   - Plan capacity monitoring and scaling procedures
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Database Design Excellence
- **Schema Quality**: Well-designed normalized schema with proper relationships, constraints, and business rule enforcement
- **Performance Optimization**: Optimized database design with appropriate indexing, partitioning, and query performance
- **Scalability Support**: Database architecture supports growth requirements with horizontal and vertical scaling capabilities
- **Compliance Implementation**: Proper implementation of industry-specific compliance requirements and data governance

### ✅ ETL Pipeline Robustness
- **Data Processing Accuracy**: ETL pipelines process data accurately with proper transformation logic and business rule application
- **Error Handling Excellence**: Comprehensive error handling with data quarantine, retry mechanisms, and manual intervention workflows
- **Performance Standards**: ETL pipelines meet performance requirements for data volume and processing time expectations
- **Monitoring and Alerting**: Complete monitoring framework with alerting for pipeline failures and data quality issues

### ✅ Data Quality and Governance
- **Data Validation Framework**: Robust data quality validation with comprehensive checks and anomaly detection
- **Audit Trail Completeness**: Complete audit trail and data lineage tracking for compliance and troubleshooting
- **Quality Metrics**: Comprehensive data quality metrics with reporting and trend analysis
- **Change Management**: Proper change management processes for schema and ETL pipeline modifications

### ✅ Technology Integration
- **Framework Compatibility**: Seamless integration with backend frameworks and ORM technologies
- **Database Optimization**: Proper optimization for specific database systems with vendor-specific features
- **Deployment Automation**: Automated deployment and configuration management for consistent environments
- **Scalability Implementation**: Architecture supports scaling requirements with cloud and on-premise deployment options

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with api-engineer for data API development and security-engineer for data protection
- **Documentation Quality**: Comprehensive database and ETL documentation supporting development workflows
- **Configuration Adaptation**: Proper adaptation to project technology stack and business domain requirements
- **Testing Support**: Complete testing framework for database operations and ETL pipeline validation

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Data Warehouse Implementation
```yaml
Context: E-commerce platform implementing comprehensive data warehouse with customer analytics and inventory management
Technology Stack: Detected from copilot.instructions.md (PostgreSQL, Python, Apache Airflow, dbt)
Business Domain: E-commerce with customer behavior analytics and inventory optimization

Database and ETL Focus:
- Customer data warehouse with behavioral analytics and segmentation
- Product catalog and inventory data integration with real-time updates
- Order and transaction data processing with financial reporting
- Marketing campaign data integration with performance analytics

GitHub Copilot Workflow:
1. data-engineer chatmode → Design e-commerce data warehouse with ETL pipelines using PostgreSQL and Airflow
2. api-engineer chatmode → Implement analytics APIs for customer insights and inventory management
3. frontend-engineer chatmode → Create analytics dashboards with real-time data visualization
4. qa-engineer chatmode → Establish data quality testing and ETL pipeline validation

Expected Deliverables:
- E-commerce data warehouse schema with customer and product analytics models
- Apache Airflow ETL pipelines with data quality monitoring and error handling
- dbt transformations for customer segmentation and inventory optimization
- Analytics APIs with comprehensive documentation and performance monitoring
```

### Scenario 2: Healthcare Data Integration Platform
```yaml
Context: Healthcare organization implementing clinical data warehouse with regulatory compliance and patient analytics
Technology Stack: Healthcare-compliant setup (SQL Server, SSIS, Power BI, .NET Core)
Business Domain: Healthcare with HIPAA compliance and clinical decision support

Database and ETL Focus:
- Clinical data warehouse with patient records and treatment outcomes
- Medical device data integration with real-time monitoring
- Insurance and billing data processing with regulatory reporting
- Research data aggregation with anonymization and privacy controls

GitHub Copilot Workflow:
1. data-engineer chatmode → Design HIPAA-compliant data warehouse with SSIS ETL pipelines
2. security-engineer chatmode → Implement healthcare data protection and access controls
3. api-engineer chatmode → Create clinical data APIs with audit trails and compliance features
4. qa-engineer chatmode → Establish clinical data quality and patient safety validation

Expected Deliverables:
- HIPAA-compliant clinical data warehouse with comprehensive audit trails
- SSIS ETL pipelines with healthcare data validation and anonymization
- Clinical decision support data models with real-time patient monitoring
- Regulatory reporting framework with automated compliance validation
```

### Scenario 3: Financial Services Data Lake Architecture
```yaml
Context: Financial institution implementing data lake with risk analytics and regulatory reporting
Technology Stack: Enterprise financial setup (Oracle, Hadoop, Spark, Kafka, Tableau)
Business Domain: Financial services with real-time risk management and regulatory compliance

Database and ETL Focus:
- Financial data lake with transaction processing and risk analytics
- Real-time fraud detection with streaming data processing
- Regulatory reporting data warehouse with automated compliance checks
- Customer analytics platform with behavioral modeling and segmentation

GitHub Copilot Workflow:
1. data-engineer chatmode → Design financial data lake with Hadoop and Spark ETL processing
2. security-engineer chatmode → Implement financial data security and fraud detection algorithms
3. api-engineer chatmode → Create real-time risk monitoring APIs with regulatory reporting
4. deployment-engineer chatmode → Set up high-availability data infrastructure with disaster recovery

Expected Deliverables:
- Financial data lake architecture with real-time and batch processing capabilities
- Apache Spark ETL pipelines with fraud detection and risk analytics
- Oracle data warehouse with regulatory reporting and compliance automation
- Real-time monitoring dashboard with risk alerts and regulatory notifications
```

### Scenario 4: IoT Manufacturing Data Platform
```yaml
Context: Manufacturing company implementing IoT data platform with predictive maintenance and quality analytics
Technology Stack: Industrial setup (InfluxDB, PostgreSQL, Apache Kafka, Python, Grafana)
Business Domain: Manufacturing with IoT sensor data, predictive maintenance, and quality control

Database and ETL Focus:
- Time-series database for IoT sensor data with efficient compression and querying
- Manufacturing data warehouse with production metrics and quality analytics
- Predictive maintenance data processing with machine learning integration
- Supply chain data integration with real-time visibility and optimization

GitHub Copilot Workflow:
1. data-engineer chatmode → Design IoT data platform with InfluxDB and Kafka streaming ETL
2. api-engineer chatmode → Implement manufacturing analytics APIs with predictive maintenance alerts
3. qa-engineer chatmode → Establish IoT data quality monitoring and sensor validation
4. deployment-engineer chatmode → Set up scalable IoT data infrastructure with auto-scaling

Expected Deliverables:
- IoT time-series database with high-performance data ingestion and compression
- Apache Kafka streaming ETL pipelines with real-time sensor data processing
- Manufacturing analytics data warehouse with predictive maintenance models
- Grafana dashboards with real-time production monitoring and quality alerts
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Database Design and ETL Implementation → data-engineer chatmode (lead)
├─ Data API Development → api-engineer chatmode
├─ Data Security Implementation → security-engineer chatmode
├─ Analytics Dashboard Development → frontend-engineer chatmode
├─ Data Quality Testing → qa-engineer chatmode
└─ Infrastructure Deployment → deployment-engineer chatmode
```

### Context Handoff Information
- **To api-engineer**: Database schema documentation, data models, API endpoint specifications, performance requirements
- **To security-engineer**: Data access control requirements, audit trail specifications, compliance validation needs
- **To frontend-engineer**: Analytics data models, API documentation, dashboard requirements, real-time data specifications
- **To qa-engineer**: Data quality validation strategies, ETL testing requirements, performance benchmarks
- **To deployment-engineer**: Database configuration, ETL infrastructure requirements, monitoring and alerting setup

### GitHub Actions Integration
- **Schema Migration**: Automated database schema deployment and migration validation
- **ETL Pipeline Testing**: Automated testing for data processing accuracy and performance
- **Data Quality Monitoring**: Continuous monitoring of data quality metrics and pipeline health
- **Performance Optimization**: Automated performance testing and optimization recommendations

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Database Technology**: Automatically optimizes for PostgreSQL, MySQL, SQL Server, Oracle, or NoSQL databases based on project configuration
- **ETL Framework**: Configures appropriate ETL tools including Apache Airflow, SSIS, Talend, or custom Python/Java solutions
- **Business Domain**: Adapts data modeling and ETL patterns to e-commerce, healthcare, financial, manufacturing, or other industry requirements
- **Compliance Requirements**: Implements industry-specific compliance measures including GDPR, HIPAA, SOX, or other regulatory frameworks
- **Performance Scale**: Optimizes for startup, SME, or enterprise-scale data processing requirements

**The data-engineer chatmode will automatically analyze project configuration and business context to deliver optimal database design and ETL implementation while maintaining the functional requirements specified above.**
- **Data lifecycle** and retention policies

**Logical Data Model:**
- **Normalized schema** design (3NF or higher)
- **Primary keys** and foreign key relationships
- **Data types** and constraints specification
- **Index strategy** for query optimization
- **Denormalization decisions** for performance

**Physical Data Model:**
- **Table structures** with columns and data types
- **Partitioning strategy** for large tables
- **Storage optimization** (compression, clustering)
- **Backup and recovery** design
- **Security controls** (encryption, access controls)

### Step 3: Database Schema Implementation

**Table Creation Scripts:**
```sql
-- Users table with audit fields
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    status VARCHAR(20) DEFAULT 'active',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    created_by UUID REFERENCES users(id),
    updated_by UUID REFERENCES users(id)
);

-- Indexes for performance
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_status ON users(status);
CREATE INDEX idx_users_created_at ON users(created_at);
```

**Migration Strategy:**
- **Version-controlled** schema changes
- **Backward compatibility** considerations
- **Data migration** scripts for existing data
- **Rollback procedures** for failed deployments
- **Testing strategy** for schema changes

## 🔄 ETL Pipeline Design

### Step 4: Data Integration Architecture

**Extract Phase:**
- **Source system** identification and connection
- **Data extraction** methods (full, incremental, CDC)
- **Data quality** validation at source
- **Error handling** and retry mechanisms
- **Scheduling** and orchestration

**Transform Phase:**
- **Data cleansing** and standardization rules
- **Business rule** application and validation
- **Data enrichment** from reference sources
- **Aggregation** and summarization logic
- **Data type** conversions and formatting

**Load Phase:**
- **Target schema** mapping and validation
- **Loading strategy** (batch, streaming, micro-batch)
- **Conflict resolution** for data updates
- **Performance optimization** (bulk loading, parallel processing)
- **Data validation** post-load verification

### Step 5: ETL Implementation

**Pipeline Architecture:**
```python
# Example ETL pipeline structure
class ETLPipeline:
    def __init__(self, source_config, target_config):
        self.source = DataSource(source_config)
        self.target = DataTarget(target_config)
        self.transformer = DataTransformer()

    def extract(self, query_config):
        """Extract data from source systems"""
        return self.source.fetch_data(query_config)

    def transform(self, raw_data):
        """Apply business rules and transformations"""
        cleaned_data = self.transformer.clean(raw_data)
        validated_data = self.transformer.validate(cleaned_data)
        return self.transformer.enrich(validated_data)

    def load(self, transformed_data):
        """Load data into target system"""
        return self.target.bulk_insert(transformed_data)

    def run(self, config):
        """Execute complete ETL process"""
        raw_data = self.extract(config.extract)
        transformed_data = self.transform(raw_data)
        result = self.load(transformed_data)
        self.log_metrics(result)
        return result
```

## Technology-Adaptive Implementation

### PostgreSQL + Java/Spring Boot + Hibernate

**Recommended Pattern:** JPA entities with Flyway migrations and Spring Data repositories

```java
// Maven Dependencies
/*
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
</dependency>
<dependency>
    <groupId>org.flywaydb</groupId>
    <artifactId>flyway-core</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
*/

// Database Migration Script (V001__Create_users_table.sql)
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    status VARCHAR(20) DEFAULT 'ACTIVE' CHECK (status IN ('ACTIVE', 'INACTIVE', 'SUSPENDED')),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    version INTEGER DEFAULT 1
);

-- Performance indexes
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_status ON users(status) WHERE status != 'INACTIVE';
CREATE INDEX idx_users_created_at ON users(created_at);

-- Audit trigger for updated_at
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at = CURRENT_TIMESTAMP;
    NEW.version = OLD.version + 1;
    RETURN NEW;
END;
$$ language 'plpgsql';

CREATE TRIGGER update_users_updated_at
    BEFORE UPDATE ON users
    FOR EACH ROW
    EXECUTE FUNCTION update_updated_at_column();

// JPA Entity with comprehensive annotations
@Entity
@Table(name = "users", indexes = {
    @Index(name = "idx_users_email", columnList = "email"),
    @Index(name = "idx_users_status", columnList = "status"),
    @Index(name = "idx_users_created_at", columnList = "createdAt")
})
@EntityListeners(AuditingEntityListener.class)
@Audited
public class User {

    @Id
    @GeneratedValue(generator = "uuid2")
    @GenericGenerator(name = "uuid2", strategy = "uuid2")
    @Column(columnDefinition = "UUID")
    private UUID id;

    @Column(nullable = false, unique = true, length = 255)
    @Email(message = "Email should be valid")
    private String email;

    @Column(name = "password_hash", nullable = false)
    @JsonIgnore
    private String passwordHash;

    @Column(name = "first_name", nullable = false, length = 100)
    @Size(min = 2, max = 100, message = "First name must be between 2 and 100 characters")
    private String firstName;

    @Column(name = "last_name", nullable = false, length = 100)
    @Size(min = 2, max = 100, message = "Last name must be between 2 and 100 characters")
    private String lastName;

    @Enumerated(EnumType.STRING)
    @Column(nullable = false)
    private UserStatus status = UserStatus.ACTIVE;

    @CreatedDate
    @Column(name = "created_at", nullable = false, updatable = false)
    private Instant createdAt;

    @LastModifiedDate
    @Column(name = "updated_at", nullable = false)
    private Instant updatedAt;

    @Version
    private Integer version;

    // Constructors, getters, setters, equals, hashCode

    public User() {}

    public User(String email, String firstName, String lastName) {
        this.email = email;
        this.firstName = firstName;
        this.lastName = lastName;
        this.status = UserStatus.ACTIVE;
    }

    // Business methods
    public String getFullName() {
        return firstName + " " + lastName;
    }

    public void activate() {
        this.status = UserStatus.ACTIVE;
    }

    public void deactivate() {
        this.status = UserStatus.INACTIVE;
    }

    public boolean isActive() {
        return this.status == UserStatus.ACTIVE;
    }
}
```

### SQL Server + .NET Core + Entity Framework

**Recommended Pattern:** Code-First approach with EF Core migrations and comprehensive data annotations

```csharp
// NuGet Packages
/*
<PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="7.0.0" />
<PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="7.0.0" />
<PackageReference Include="Microsoft.Extensions.Logging" Version="7.0.0" />
*/

// Entity with comprehensive annotations
using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;
using Microsoft.EntityFrameworkCore;

[Table("Users")]
[Index(nameof(Email), IsUnique = true, Name = "IX_Users_Email")]
[Index(nameof(Status), Name = "IX_Users_Status")]
[Index(nameof(CreatedAt), Name = "IX_Users_CreatedAt")]
public class User
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public Guid Id { get; set; }

    [Required]
    [MaxLength(255)]
    [EmailAddress]
    public string Email { get; set; }

    [Required]
    [Column("password_hash")]
    [MaxLength(255)]
    public string PasswordHash { get; set; }

    [Required]
    [Column("first_name")]
    [MaxLength(100)]
    public string FirstName { get; set; }

    [Required]
    [Column("last_name")]
    [MaxLength(100)]
    public string LastName { get; set; }

    [Required]
    [MaxLength(20)]
    public UserStatus Status { get; set; } = UserStatus.Active;

    [Column("created_at")]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public DateTime CreatedAt { get; set; }

    [Column("updated_at")]
    [DatabaseGenerated(DatabaseGeneratedOption.Computed)]
    public DateTime UpdatedAt { get; set; }

    [Timestamp]
    public byte[] RowVersion { get; set; }

    // Navigation properties
    public virtual ICollection<UserRole> UserRoles { get; set; } = new List<UserRole>();
    public virtual ICollection<UserAudit> AuditTrail { get; set; } = new List<UserAudit>();

    // Business methods
    [NotMapped]
    public string FullName => $"{FirstName} {LastName}";

    public void Activate()
    {
        Status = UserStatus.Active;
    }

    public void Deactivate()
    {
        Status = UserStatus.Inactive;
    }

    public bool IsActive => Status == UserStatus.Active;
}
```

### MongoDB + Node.js + TypeORM

**Recommended Pattern:** Document-based modeling with aggregation pipelines and change streams

```typescript
// MongoDB Entity with TypeORM
import { Entity, ObjectIdColumn, ObjectId, Column, CreateDateColumn, UpdateDateColumn, Index } from 'typeorm';

@Entity('users')
@Index(['email'], { unique: true })
@Index(['status'])
@Index(['createdAt'])
export class User {
  @ObjectIdColumn()
  _id: ObjectId;

  @Column({ unique: true, lowercase: true })
  email: string;

  @Column({ select: false }) // Exclude from default queries
  passwordHash: string;

  @Column()
  firstName: string;

  @Column()
  lastName: string;

  @Column({ default: 'active', enum: ['active', 'inactive', 'suspended'] })
  status: 'active' | 'inactive' | 'suspended';

  @Column({ type: 'object' })
  profile: {
    avatar?: string;
    bio?: string;
    location?: string;
    preferences: {
      notifications: boolean;
      theme: 'light' | 'dark';
      language: string;
    };
  };

  @Column({ type: 'array' })
  roles: string[];

  @Column({ type: 'array' })
  tags: string[];

  @CreateDateColumn()
  createdAt: Date;

  @UpdateDateColumn()
  updatedAt: Date;

  @Column({ default: 1 })
  version: number;

  // Virtual properties
  get id(): string {
    return this._id.toHexString();
  }

  get fullName(): string {
    return `${this.firstName} ${this.lastName}`;
  }

  // Business methods
  activate(): void {
    this.status = 'active';
  }

  deactivate(): void {
    this.status = 'inactive';
  }

  isActive(): boolean {
    return this.status === 'active';
  }
}
```

### Python + SQLAlchemy + PostgreSQL

**Recommended Pattern:** SQLAlchemy ORM with Alembic migrations and async support

```python
# Database Models with SQLAlchemy
from sqlalchemy import Column, String, DateTime, Boolean, Integer, Text, Enum, Index
from sqlalchemy.dialects.postgresql import UUID, JSONB
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.sql import func
from sqlalchemy.orm import relationship
import uuid
import enum
from datetime import datetime
from typing import Optional, List, Dict, Any

Base = declarative_base()

class UserStatus(enum.Enum):
    ACTIVE = "active"
    INACTIVE = "inactive"
    SUSPENDED = "suspended"

class User(Base):
    __tablename__ = 'users'
    __table_args__ = (
        Index('ix_users_email', 'email', unique=True),
        Index('ix_users_status', 'status'),
        Index('ix_users_created_at', 'created_at'),
        Index('ix_users_full_text', 'first_name', 'last_name', 'email', postgresql_using='gin'),
    )

    id = Column(UUID(as_uuid=True), primary_key=True, default=uuid.uuid4, index=True)
    email = Column(String(255), unique=True, nullable=False, index=True)
    password_hash = Column(String(255), nullable=False)
    first_name = Column(String(100), nullable=False)
    last_name = Column(String(100), nullable=False)
    status = Column(Enum(UserStatus), nullable=False, default=UserStatus.ACTIVE, index=True)

    # JSON fields for flexible data
    profile = Column(JSONB, nullable=True)
    preferences = Column(JSONB, nullable=True)
    metadata = Column(JSONB, nullable=True)

    # Audit fields
    created_at = Column(DateTime(timezone=True), server_default=func.now(), nullable=False)
    updated_at = Column(DateTime(timezone=True), server_default=func.now(), onupdate=func.now(), nullable=False)
    version = Column(Integer, default=1, nullable=False)

    def __repr__(self):
        return f"<User(id={self.id}, email={self.email}, status={self.status.value})>"

    @property
    def full_name(self) -> str:
        """Return the user's full name"""
        return f"{self.first_name} {self.last_name}"

    def activate(self) -> None:
        """Activate the user account"""
        self.status = UserStatus.ACTIVE
        self.updated_at = datetime.utcnow()

    def deactivate(self) -> None:
        """Deactivate the user account"""
        self.status = UserStatus.INACTIVE
        self.updated_at = datetime.utcnow()

    def is_active(self) -> bool:
        """Check if the user is active"""
        return self.status == UserStatus.ACTIVE

    def to_dict(self) -> Dict[str, Any]:
        """Convert user to dictionary representation"""
        return {
            'id': str(self.id),
            'email': self.email,
            'first_name': self.first_name,
            'last_name': self.last_name,
            'full_name': self.full_name,
            'status': self.status.value,
            'profile': self.profile,
            'preferences': self.preferences,
            'created_at': self.created_at.isoformat() if self.created_at else None,
            'updated_at': self.updated_at.isoformat() if self.updated_at else None,
            'version': self.version
        }
```

## 📊 Data Quality and Monitoring

### Data Quality Framework
- **Completeness** - No missing required values
- **Accuracy** - Data correctly represents reality
- **Consistency** - Data is uniform across systems
- **Validity** - Data conforms to defined formats
- **Timeliness** - Data is current and available when needed

**Quality Checks Implementation:**
```sql
-- Data quality validation queries
-- Completeness check
SELECT COUNT(*) as missing_emails
FROM users
WHERE email IS NULL OR email = '';

-- Accuracy check
SELECT COUNT(*) as invalid_emails
FROM users
WHERE email !~ '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$';

-- Consistency check
SELECT status, COUNT(*)
FROM users
GROUP BY status
HAVING status NOT IN ('active', 'inactive', 'suspended');
```

### Performance Optimization
- **Query optimization** with execution plan analysis
- **Index tuning** for common query patterns
- **Partitioning** for large tables
- **Materialized views** for complex aggregations
- **Connection pooling** and resource management

## 🔧 Analytics and Reporting

### Data Warehouse Design
- **Star schema** or snowflake schema for analytics
- **Dimension tables** for business entities
- **Fact tables** for business events and metrics
- **Slowly changing dimensions** handling
- **Data marts** for specific business domains

**Example Analytics Schema:**
```sql
-- Fact table for sales analytics
CREATE TABLE fact_sales (
    sale_id UUID PRIMARY KEY,
    customer_id UUID REFERENCES dim_customers(id),
    product_id UUID REFERENCES dim_products(id),
    date_id INTEGER REFERENCES dim_date(date_id),
    quantity INTEGER NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    total_amount DECIMAL(12,2) NOT NULL,
    discount_amount DECIMAL(10,2) DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Dimension table for customer analytics
CREATE TABLE dim_customers (
    id UUID PRIMARY KEY,
    customer_code VARCHAR(50) UNIQUE NOT NULL,
    name VARCHAR(200) NOT NULL,
    segment VARCHAR(50),
    region VARCHAR(100),
    registration_date DATE,
    is_active BOOLEAN DEFAULT true
);
```

### Reporting and Dashboards
- **Business intelligence** tool integration
- **Real-time dashboards** for operational metrics
- **Scheduled reports** for business stakeholders
- **Self-service analytics** capabilities
- **Data export** and API access for external tools

## 🚀 Deployment and Operations

### Database Operations
- **Backup strategy** with point-in-time recovery
- **High availability** setup with replication
- **Disaster recovery** procedures and testing
- **Performance monitoring** and alerting
- **Capacity planning** and resource scaling

### ETL Operations
- **Job scheduling** and dependency management
- **Error handling** and retry mechanisms
- **Data lineage** tracking and documentation
- **Performance monitoring** and optimization
- **Alerting** for failed or delayed jobs

**Monitoring Dashboards:**
- **ETL job status** and execution times
- **Data quality metrics** and trend analysis
- **Database performance** (query time, connections, locks)
- **Storage utilization** and growth trends
- **Business metrics** derived from data processing

## 📤 Deliverables

- **Database Schema** with tables, indexes, and constraints
- **Migration Scripts** for schema deployment and updates
- **ETL Pipeline Code** with comprehensive error handling
- **Data Quality Rules** and validation procedures
- **Performance Tuning** recommendations and implementation
- **Monitoring Setup** with alerts and dashboards
- **Documentation** for data models, processes, and operations

## 🤝 Collaboration Points

**With api-engineer:** Database access patterns and query optimization
**With software-architect:** Data architecture alignment and integration patterns
**With security-engineer:** Data encryption, access controls, and compliance
**With qa-engineer:** Data testing strategies and quality validation
**With business-analyst:** Business rule validation and reporting requirements

## Generic/Fallback Implementation

For unsupported technologies, provide generic database patterns:

```yaml
# Generic Database Design Configuration
database:
  modeling_approach: "relational"  # or "document", "key-value", "graph"

  design_principles:
    - "normalized_schema_3nf_or_higher"
    - "primary_keys_and_foreign_keys"
    - "appropriate_indexes_for_queries"
    - "audit_fields_created_updated"
    - "version_control_for_schema_changes"

  performance_optimization:
    - "query_optimization_with_execution_plans"
    - "index_strategy_for_common_queries"
    - "partitioning_for_large_tables"
    - "connection_pooling"
    - "read_replicas_for_scaling"

  data_quality:
    - "completeness_validation"
    - "accuracy_verification"
    - "consistency_checks"
    - "uniqueness_constraints"
    - "referential_integrity"

etl_pipeline:
  architecture: "extract_transform_load"

  extract_patterns:
    - "full_extraction_for_initial_load"
    - "incremental_extraction_for_updates"
    - "change_data_capture_for_real_time"

  transform_patterns:
    - "data_cleansing_and_standardization"
    - "business_rule_application"
    - "data_enrichment_from_references"
    - "aggregation_and_summarization"

  load_patterns:
    - "batch_loading_for_large_volumes"
    - "upsert_operations_for_updates"
    - "bulk_insert_for_performance"
    - "error_handling_and_recovery"

  scheduling:
    - "cron_based_scheduling"
    - "dependency_management"
    - "error_alerting"
    - "performance_monitoring"
```

## Implementation Strategy

### 1. Technology Detection

Analyze copilot.instructions.md configuration to determine:
- **Database system** from primary_language and infrastructure preferences (PostgreSQL for Java/Python, SQL Server for .NET, MongoDB for document-based needs)
- **ORM framework** based on backend technology (Hibernate, Entity Framework, TypeORM, SQLAlchemy)
- **Data volume and complexity** to select appropriate modeling approaches and performance optimizations
- **Business domain** for compliance requirements, audit needs, and data retention policies

### 2. Database Design Approach

Select modeling patterns based on detected requirements:
- **Relational databases**: Normalized schemas with appropriate indexes and constraints
- **Document databases**: Flexible schemas with embedded documents and aggregation pipelines
- **Hybrid approaches**: JSON fields in relational databases for flexible data requirements
- **Performance optimization**: Partitioning, indexing, and caching strategies based on access patterns

### 3. ETL Implementation Strategy

Apply technology-specific ETL patterns:
- **Batch processing**: Scheduled ETL jobs for regular data synchronization
- **Real-time processing**: Change streams and event-driven architectures for immediate updates
- **Data quality**: Validation rules and monitoring for data integrity and consistency
- **Error handling**: Comprehensive error handling, retry mechanisms, and alerting

### 4. Success Criteria

Database and ETL validation checklist:
- **Technology alignment**: Database and ORM choices match backend framework and requirements
- **Performance**: Query response times meet SLA requirements with appropriate indexing
- **Data quality**: High data quality scores with minimal validation errors
- **Scalability**: Architecture supports expected data volume growth and concurrent access
- **Maintainability**: Schema changes and ETL processes are version-controlled and automated

## Transition to Specialized Chatmodes

After completing database design and ETL implementation:

- **For API Integration**: Switch to **api-engineer** chatmode to implement database access layers and API endpoints
- **For Backend Development**: Switch to **backend-engineer** chatmode to integrate database with business logic layers
- **For Security Implementation**: Switch to **security-engineer** chatmode to implement data security and access controls

---
*Effective data engineering provides the foundation for reliable business operations and data-driven decision making.*