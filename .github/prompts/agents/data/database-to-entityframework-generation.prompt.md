---
description: Generate comprehensive Entity Framework Core models, contexts, repositories, and API endpoints from existing database schemas with advanced relationship mapping, stored procedure integration, and performance optimization. Adapts to project specifications defined in copilot.instructions.md.
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

# Entity Framework Code Generation from Database Schema

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Entity Framework Model Generation
- **Database Schema Analysis**: Analyze existing database schemas to extract table structures, relationships, constraints, and metadata
- **Entity Model Generation**: Generate Entity Framework Core models with proper annotations, validation attributes, and navigation properties
- **DbContext Configuration**: Create comprehensive DbContext with proper configuration, connection management, and relationship mapping
- **Performance Optimization**: Implement lazy loading, eager loading, and query optimization patterns for Entity Framework

### Advanced Relationship and Constraint Mapping
- **Relationship Configuration**: Map one-to-one, one-to-many, and many-to-many relationships with proper foreign key configuration
- **Complex Type Mapping**: Handle complex database types, custom value converters, and domain-specific type mappings
- **Constraint Implementation**: Implement database constraints, check constraints, and business rule validation in Entity Framework
- **Index and Performance Configuration**: Configure indexes, query filters, and performance optimization attributes

### Repository Pattern and Data Access Layer
- **Repository Interface Generation**: Create generic and specific repository interfaces with proper CRUD operations and query methods
- **Service Layer Implementation**: Generate service layer with business logic, transaction management, and error handling
- **Unit of Work Pattern**: Implement Unit of Work pattern for transaction coordination and change tracking
- **Dependency Injection Setup**: Configure dependency injection for repositories, services, and DbContext management

### API Integration and CRUD Operations
- **Controller Generation**: Generate ASP.NET Core controllers with proper HTTP methods and status code handling
- **DTO and Mapping Configuration**: Create Data Transfer Objects with AutoMapper configuration for entity-DTO mapping
- **API Documentation**: Generate OpenAPI/Swagger documentation with proper model documentation and examples
- **Validation and Error Handling**: Implement comprehensive validation, error handling, and API response formatting

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Database Schema Analysis and Discovery
```
1. Read copilot.instructions.md to extract:
   - .NET Core version and Entity Framework preferences
   - Database system and connection configuration
   - Business domain and data modeling requirements
   - Performance and scalability expectations

2. Database Structure Analysis:
   - Connect to database and extract table schemas
   - Analyze relationships, foreign keys, and constraints
   - Identify stored procedures, functions, and views
   - Review indexes, triggers, and database-specific features
```

### 2. Entity Framework Model Generation
```
1. Entity Class Generation:
   - Generate entity classes with proper property types and annotations
   - Configure navigation properties for relationships
   - Implement validation attributes and data annotations
   - Add audit properties and soft delete patterns where needed

2. DbContext Configuration:
   - Create DbContext with proper entity configuration
   - Configure relationships using Fluent API
   - Set up connection strings and database provider configuration
   - Implement change tracking and audit trail functionality
```

### 3. Repository and Service Layer Implementation
```
1. Repository Pattern Implementation:
   - Generate generic repository interface with common CRUD operations
   - Create specific repository interfaces for complex entity operations
   - Implement concrete repository classes with Entity Framework integration
   - Add query optimization and performance monitoring

2. Service Layer Design:
   - Create service interfaces with business logic operations
   - Implement service classes with transaction management
   - Add error handling and logging integration
   - Configure dependency injection and lifetime management
```

### 4. API Controller and DTO Generation
```
1. Controller Generation:
   - Generate ASP.NET Core controllers with proper routing
   - Implement CRUD endpoints with proper HTTP methods
   - Add validation, error handling, and status code management
   - Configure authorization and security attributes

2. DTO and Mapping Configuration:
   - Create request and response DTOs for API operations
   - Configure AutoMapper profiles for entity-DTO mapping
   - Implement validation attributes and business rule checking
   - Add pagination and filtering support for list operations
```

### 5. Testing, Documentation, and Optimization
```
1. Testing Framework Generation:
   - Create unit tests for repository and service layers
   - Generate integration tests for API controllers
   - Add database seeding and test data management
   - Implement performance testing for Entity Framework queries

2. Documentation and Optimization:
   - Generate comprehensive API documentation with Swagger
   - Create database migration scripts and version management
   - Implement performance monitoring and query optimization
   - Add logging and diagnostics for debugging and monitoring
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Entity Framework Model Quality
- **Accurate Mapping**: Entity models accurately reflect database schema with proper type mapping and constraints
- **Relationship Configuration**: All database relationships properly configured with navigation properties and foreign keys
- **Performance Optimization**: Entity Framework configured with appropriate lazy loading, change tracking, and query optimization
- **Validation Implementation**: Comprehensive validation attributes and business rule enforcement in entity models

### ✅ Data Access Layer Excellence
- **Repository Pattern**: Clean repository pattern implementation with proper separation of concerns and testability
- **Service Layer Design**: Well-designed service layer with business logic encapsulation and transaction management
- **Error Handling**: Comprehensive error handling with proper exception management and logging
- **Unit of Work**: Proper Unit of Work implementation for transaction coordination and data consistency

### ✅ API Integration Standards
- **Controller Quality**: Well-designed ASP.NET Core controllers with proper HTTP methods and status codes
- **DTO Implementation**: Efficient DTO classes with proper validation and mapping configuration
- **Documentation Completeness**: Comprehensive API documentation with Swagger integration and examples
- **Security Implementation**: Proper authorization and authentication integration in API controllers

### ✅ Performance and Scalability
- **Query Optimization**: Optimized Entity Framework queries with proper includes and projections
- **Database Performance**: Appropriate indexes and query patterns for optimal database performance
- **Memory Management**: Efficient memory usage with proper disposal and change tracking configuration
- **Connection Management**: Proper connection pooling and resource management for scalability

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with api-engineer for API development and security-engineer for data protection
- **Code Generation Quality**: Generated code follows .NET best practices and Entity Framework conventions
- **Configuration Adaptation**: Proper adaptation to project technology stack and business domain requirements
- **Testing Support**: Complete testing framework for Entity Framework operations and API validation

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: E-commerce Database to Entity Framework
```yaml
Context: E-commerce platform with complex product catalog, inventory, and order management database
Technology Stack: Detected from copilot.instructions.md (.NET 8, Entity Framework Core, SQL Server, AutoMapper)
Business Domain: E-commerce with product variants, inventory tracking, and order processing

Entity Framework Generation Focus:
- Product catalog with categories, variants, and pricing relationships
- Customer management with addresses and order history
- Order processing with line items and payment integration
- Inventory tracking with stock movements and supplier relationships

GitHub Copilot Workflow:
1. data-engineer chatmode → Generate comprehensive Entity Framework models from e-commerce database schema
2. api-engineer chatmode → Create RESTful API controllers with proper CRUD operations and validation
3. security-engineer chatmode → Implement data access security and audit trails for financial data
4. qa-engineer chatmode → Generate comprehensive testing for Entity Framework operations and API endpoints

Expected Deliverables:
- Complete Entity Framework models with e-commerce relationship mapping
- Repository and service layers with business logic and transaction management
- ASP.NET Core API controllers with comprehensive CRUD operations
- AutoMapper configuration and DTO classes for API integration
```

### Scenario 2: Healthcare Database Entity Framework Generation
```yaml
Context: Healthcare management system with patient records, clinical workflows, and regulatory compliance
Technology Stack: Healthcare-compliant setup (.NET Core, Entity Framework, PostgreSQL, FluentValidation)
Business Domain: Healthcare with HIPAA compliance and clinical data management

Entity Framework Generation Focus:
- Patient medical records with clinical data relationships
- Provider and appointment management with scheduling constraints
- Medical billing and insurance processing with audit requirements
- Clinical decision support with treatment protocols and outcomes

GitHub Copilot Workflow:
1. data-engineer chatmode → Generate HIPAA-compliant Entity Framework models with audit trails
2. security-engineer chatmode → Implement healthcare data protection and access controls
3. api-engineer chatmode → Create clinical workflow APIs with regulatory compliance features
4. qa-engineer chatmode → Establish patient safety and data integrity validation

Expected Deliverables:
- HIPAA-compliant Entity Framework models with comprehensive audit trails
- Clinical workflow repository and service layers with regulatory compliance
- Healthcare API controllers with patient data protection and access controls
- Comprehensive validation framework for clinical data integrity
```

### Scenario 3: Financial Services Entity Framework Architecture
```yaml
Context: Financial institution with transaction processing, account management, and regulatory reporting
Technology Stack: Enterprise financial setup (.NET Framework, Entity Framework, Oracle, Enterprise Library)
Business Domain: Financial services with real-time transaction processing and compliance

Entity Framework Generation Focus:
- Account management with complex financial product relationships
- Transaction processing with real-time fraud detection integration
- Customer onboarding with KYC and compliance validation
- Regulatory reporting with automated compliance checks

GitHub Copilot Workflow:
1. data-engineer chatmode → Generate financial Entity Framework models with Oracle optimization
2. security-engineer chatmode → Implement financial security controls and fraud detection
3. api-engineer chatmode → Create real-time transaction processing APIs
4. deployment-engineer chatmode → Set up high-availability Entity Framework configuration

Expected Deliverables:
- Financial services Entity Framework models with transaction integrity
- Oracle-optimized DbContext with performance tuning and connection pooling
- Real-time transaction API controllers with fraud detection integration
- Regulatory reporting services with automated compliance validation
```

### Scenario 4: Manufacturing ERP Entity Framework Integration
```yaml
Context: Manufacturing company with ERP system integration and production management
Technology Stack: Industrial setup (.NET Core, Entity Framework, MySQL, Hangfire)
Business Domain: Manufacturing with production planning, quality control, and supply chain management

Entity Framework Generation Focus:
- Production planning with work orders and resource scheduling
- Quality control with inspection processes and compliance tracking
- Supply chain management with supplier relationships and procurement
- Equipment maintenance with predictive maintenance and asset tracking

GitHub Copilot Workflow:
1. data-engineer chatmode → Generate manufacturing Entity Framework models with MySQL optimization
2. api-engineer chatmode → Create production management APIs with real-time monitoring
3. qa-engineer chatmode → Implement quality control validation and testing frameworks
4. deployment-engineer chatmode → Set up scalable Entity Framework infrastructure

Expected Deliverables:
- Manufacturing Entity Framework models with production workflow relationships
- MySQL-optimized DbContext with performance tuning for high-volume operations
- Production management API controllers with real-time monitoring and alerts
- Quality control services with automated inspection and compliance validation
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Entity Framework Generation → data-engineer chatmode (lead)
├─ API Controller Development → api-engineer chatmode
├─ Data Security Implementation → security-engineer chatmode
├─ Frontend Integration → frontend-engineer chatmode
├─ Testing Strategy → qa-engineer chatmode
└─ Infrastructure Configuration → deployment-engineer chatmode
```

### Context Handoff Information
- **To api-engineer**: Entity Framework models, repository interfaces, DTO specifications, API endpoint requirements
- **To security-engineer**: Data access control requirements, audit trail specifications, compliance validation needs
- **To frontend-engineer**: API endpoint documentation, data models, integration patterns, validation requirements
- **To qa-engineer**: Testing strategies, Entity Framework testing patterns, performance benchmarks
- **To deployment-engineer**: DbContext configuration, connection strings, performance tuning, deployment requirements

### GitHub Actions Integration
- **Code Generation**: Automated Entity Framework model generation from database schema changes
- **Migration Management**: Automated database migration generation and deployment
- **Testing Integration**: Automated testing for Entity Framework operations and API endpoints
- **Performance Monitoring**: Continuous monitoring of Entity Framework query performance and optimization

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **.NET Framework Version**: Automatically configures Entity Framework version and features based on .NET version specification
- **Database System**: Optimizes Entity Framework configuration for SQL Server, PostgreSQL, MySQL, or Oracle databases
- **Business Domain**: Adapts entity modeling and validation patterns to industry-specific requirements and compliance needs
- **Performance Requirements**: Configures Entity Framework performance optimizations based on scale and performance expectations
- **Security Standards**: Implements appropriate data access security measures and audit trail requirements

**The data-engineer chatmode will automatically analyze project configuration and database schema to deliver optimal Entity Framework code generation while maintaining the functional requirements specified above.**
SELECT
    t.TABLE_SCHEMA,
    t.TABLE_NAME,
    t.TABLE_TYPE,
    t.ENGINE,
    t.TABLE_COMMENT
FROM INFORMATION_SCHEMA.TABLES t
WHERE t.TABLE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys')
ORDER BY t.TABLE_SCHEMA, t.TABLE_NAME;

-- Analyze column structure
SELECT
    c.TABLE_SCHEMA,
    c.TABLE_NAME,
    c.COLUMN_NAME,
    c.DATA_TYPE,
    c.IS_NULLABLE,
    c.COLUMN_DEFAULT,
    c.CHARACTER_MAXIMUM_LENGTH,
    c.NUMERIC_PRECISION,
    c.NUMERIC_SCALE,
    c.COLUMN_KEY,
    c.EXTRA,
    c.COLUMN_COMMENT
FROM INFORMATION_SCHEMA.COLUMNS c
WHERE c.TABLE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys')
ORDER BY c.TABLE_SCHEMA, c.TABLE_NAME, c.ORDINAL_POSITION;

-- Analyze foreign key relationships
SELECT
    kcu.CONSTRAINT_NAME,
    kcu.TABLE_SCHEMA,
    kcu.TABLE_NAME,
    kcu.COLUMN_NAME,
    kcu.REFERENCED_TABLE_SCHEMA,
    kcu.REFERENCED_TABLE_NAME,
    kcu.REFERENCED_COLUMN_NAME,
    rc.UPDATE_RULE,
    rc.DELETE_RULE
FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE kcu
JOIN INFORMATION_SCHEMA.REFERENTIAL_CONSTRAINTS rc
    ON kcu.CONSTRAINT_NAME = rc.CONSTRAINT_NAME
WHERE kcu.TABLE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys')
    AND kcu.REFERENCED_TABLE_NAME IS NOT NULL;

-- Analyze indexes
SELECT
    s.TABLE_SCHEMA,
    s.TABLE_NAME,
    s.INDEX_NAME,
    s.COLUMN_NAME,
    s.SEQ_IN_INDEX,
    s.NON_UNIQUE,
    s.INDEX_TYPE
FROM INFORMATION_SCHEMA.STATISTICS s
WHERE s.TABLE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys')
ORDER BY s.TABLE_SCHEMA, s.TABLE_NAME, s.INDEX_NAME, s.SEQ_IN_INDEX;
```

#### 1.2 Stored Procedures and Functions Discovery
```sql
-- List stored procedures
SELECT
    ROUTINE_SCHEMA,
    ROUTINE_NAME,
    ROUTINE_TYPE,
    DATA_TYPE,
    ROUTINE_DEFINITION,
    CREATED,
    LAST_ALTERED,
    ROUTINE_COMMENT
FROM INFORMATION_SCHEMA.ROUTINES
WHERE ROUTINE_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys')
ORDER BY ROUTINE_SCHEMA, ROUTINE_TYPE, ROUTINE_NAME;

-- List stored procedure parameters
SELECT
    SPECIFIC_SCHEMA,
    SPECIFIC_NAME,
    PARAMETER_NAME,
    ORDINAL_POSITION,
    PARAMETER_MODE,
    DATA_TYPE,
    CHARACTER_MAXIMUM_LENGTH,
    NUMERIC_PRECISION,
    NUMERIC_SCALE
FROM INFORMATION_SCHEMA.PARAMETERS
WHERE SPECIFIC_SCHEMA NOT IN ('information_schema', 'mysql', 'performance_schema', 'sys')
ORDER BY SPECIFIC_SCHEMA, SPECIFIC_NAME, ORDINAL_POSITION;
```

#### 1.3 Entity Framework Scaffolding Setup
```bash
# Install Entity Framework Core tools
dotnet tool install --global dotnet-ef
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet add package Microsoft.EntityFrameworkCore.Design

# Scaffold database (reverse engineering)
dotnet ef dbcontext scaffold "Server=localhost;Database=YourDatabase;Trusted_Connection=true;" Microsoft.EntityFrameworkCore.SqlServer \
    --output-dir Models \
    --context-dir Data \
    --context YourDbContext \
    --data-annotations \
    --force
```

### Phase 2: Entity Models Generation and Enhancement

#### 2.1 Enhanced Entity Models
```csharp
// Models/User.cs - Enhanced scaffolded entity
using System.ComponentModel.DataAnnotations;
using System.ComponentModel.DataAnnotations.Schema;
using Microsoft.EntityFrameworkCore;

namespace YourProject.Models.Entities
{
    [Table("Users")]
    [Index(nameof(Username), IsUnique = true, Name = "IX_Users_Username")]
    [Index(nameof(Email), IsUnique = true, Name = "IX_Users_Email")]
    [Index(nameof(CreatedAt), Name = "IX_Users_CreatedAt")]
    public partial class User : IEntity, IAuditable
    {
        public User()
        {
            UserRoles = new HashSet<UserRole>();
            UserSessions = new HashSet<UserSession>();
            CreatedPosts = new HashSet<Post>();
            Comments = new HashSet<Comment>();
        }

        [Key]
        [Column("Id")]
        public long Id { get; set; }

        [Required]
        [Column("Username")]
        [StringLength(30)]
        [RegularExpression(@"^[a-zA-Z0-9_-]+$",
            ErrorMessage = "Username can only contain letters, numbers, underscore, and dash")]
        public string Username { get; set; } = null!;

        [Required]
        [Column("Email")]
        [StringLength(255)]
        [EmailAddress]
        public string Email { get; set; } = null!;

        [Required]
        [Column("PasswordHash")]
        [StringLength(255)]
        public string PasswordHash { get; set; } = null!;

        [Column("FirstName")]
        [StringLength(50)]
        public string? FirstName { get; set; }

        [Column("LastName")]
        [StringLength(50)]
        public string? LastName { get; set; }

        [Column("Bio")]
        [StringLength(500)]
        public string? Bio { get; set; }

        [Column("Avatar")]
        [StringLength(500)]
        [Url]
        public string? Avatar { get; set; }

        [Column("Location")]
        [StringLength(100)]
        public string? Location { get; set; }

        [Column("IsActive")]
        public bool IsActive { get; set; } = true;

        [Column("IsEmailVerified")]
        public bool IsEmailVerified { get; set; } = false;

        [Column("LastLoginAt", TypeName = "datetime2")]
        public DateTime? LastLoginAt { get; set; }

        [Required]
        [Column("CreatedAt", TypeName = "datetime2")]
        public DateTime CreatedAt { get; set; }

        [Required]
        [Column("UpdatedAt", TypeName = "datetime2")]
        public DateTime UpdatedAt { get; set; }

        [Column("CreatedBy")]
        public long? CreatedBy { get; set; }

        [Column("UpdatedBy")]
        public long? UpdatedBy { get; set; }

        [Timestamp]
        [Column("RowVersion")]
        public byte[]? RowVersion { get; set; }

        // Navigation properties
        [InverseProperty(nameof(UserRole.User))]
        public virtual ICollection<UserRole> UserRoles { get; set; }

        [InverseProperty(nameof(UserSession.User))]
        public virtual ICollection<UserSession> UserSessions { get; set; }

        [InverseProperty(nameof(Post.Author))]
        public virtual ICollection<Post> CreatedPosts { get; set; }

        [InverseProperty(nameof(Comment.Author))]
        public virtual ICollection<Comment> Comments { get; set; }

        [ForeignKey(nameof(CreatedBy))]
        [InverseProperty(nameof(User.CreatedPosts))]
        public virtual User? CreatedByUser { get; set; }

        [ForeignKey(nameof(UpdatedBy))]
        [InverseProperty(nameof(User.CreatedPosts))]
        public virtual User? UpdatedByUser { get; set; }

        // Computed properties
        [NotMapped]
        public string FullName => $"{FirstName} {LastName}".Trim();

        [NotMapped]
        public bool IsOnline => LastLoginAt.HasValue &&
            LastLoginAt.Value.AddMinutes(30) > DateTime.UtcNow;

        [NotMapped]
        public IEnumerable<string> RoleNames => UserRoles.Select(ur => ur.Role.Name);
    }

    [Table("Roles")]
    [Index(nameof(Name), IsUnique = true, Name = "IX_Roles_Name")]
    public partial class Role : IEntity
    {
        public Role()
        {
            UserRoles = new HashSet<UserRole>();
            RolePermissions = new HashSet<RolePermission>();
        }

        [Key]
        [Column("Id")]
        public int Id { get; set; }

        [Required]
        [Column("Name")]
        [StringLength(50)]
        public string Name { get; set; } = null!;

        [Column("Description")]
        [StringLength(200)]
        public string? Description { get; set; }

        [Column("IsActive")]
        public bool IsActive { get; set; } = true;

        [Required]
        [Column("CreatedAt", TypeName = "datetime2")]
        public DateTime CreatedAt { get; set; }

        [Required]
        [Column("UpdatedAt", TypeName = "datetime2")]
        public DateTime UpdatedAt { get; set; }

        // Navigation properties
        [InverseProperty(nameof(UserRole.Role))]
        public virtual ICollection<UserRole> UserRoles { get; set; }

        [InverseProperty(nameof(RolePermission.Role))]
        public virtual ICollection<RolePermission> RolePermissions { get; set; }
    }

    [Table("UserRoles")]
    [Index(nameof(UserId), nameof(RoleId), IsUnique = true, Name = "IX_UserRoles_UserId_RoleId")]
    public partial class UserRole : IEntity, IAuditable
    {
        [Key]
        [Column("Id")]
        public long Id { get; set; }

        [Column("UserId")]
        public long UserId { get; set; }

        [Column("RoleId")]
        public int RoleId { get; set; }

        [Required]
        [Column("CreatedAt", TypeName = "datetime2")]
        public DateTime CreatedAt { get; set; }

        [Required]
        [Column("UpdatedAt", TypeName = "datetime2")]
        public DateTime UpdatedAt { get; set; }

        [Column("CreatedBy")]
        public long? CreatedBy { get; set; }

        [Column("UpdatedBy")]
        public long? UpdatedBy { get; set; }

        // Navigation properties
        [ForeignKey(nameof(UserId))]
        [InverseProperty("UserRoles")]
        public virtual User User { get; set; } = null!;

        [ForeignKey(nameof(RoleId))]
        [InverseProperty("UserRoles")]
        public virtual Role Role { get; set; } = null!;

        [ForeignKey(nameof(CreatedBy))]
        public virtual User? CreatedByUser { get; set; }

        [ForeignKey(nameof(UpdatedBy))]
        public virtual User? UpdatedByUser { get; set; }
    }
}

// Base interfaces for entities
namespace YourProject.Models.Entities
{
    public interface IEntity
    {
        // Marker interface for entities
    }

    public interface IAuditable
    {
        DateTime CreatedAt { get; set; }
        DateTime UpdatedAt { get; set; }
        long? CreatedBy { get; set; }
        long? UpdatedBy { get; set; }
    }

    public interface ISoftDeletable
    {
        bool IsDeleted { get; set; }
        DateTime? DeletedAt { get; set; }
        long? DeletedBy { get; set; }
    }
}
```

#### 2.2 Enhanced DbContext with Stored Procedures
```csharp
// Data/YourDbContext.cs - Enhanced DbContext
using Microsoft.EntityFrameworkCore;
using YourProject.Models.Entities;
using YourProject.Models.StoredProcedures;

namespace YourProject.Data
{
    public partial class YourDbContext : DbContext
    {
        public YourDbContext(DbContextOptions<YourDbContext> options) : base(options) { }

        // DbSets for entities
        public virtual DbSet<User> Users { get; set; } = null!;
        public virtual DbSet<Role> Roles { get; set; } = null!;
        public virtual DbSet<UserRole> UserRoles { get; set; } = null!;
        public virtual DbSet<Post> Posts { get; set; } = null!;
        public virtual DbSet<Comment> Comments { get; set; } = null!;

        // DbSets for stored procedure results
        public virtual DbSet<UserStatistics> UserStatistics { get; set; } = null!;
        public virtual DbSet<UserActivitySummary> UserActivitySummaries { get; set; } = null!;
        public virtual DbSet<PopularPost> PopularPosts { get; set; } = null!;

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            // Configure entity relationships
            ConfigureUserEntity(modelBuilder);
            ConfigureRoleEntity(modelBuilder);
            ConfigureUserRoleEntity(modelBuilder);
            ConfigurePostEntity(modelBuilder);
            ConfigureCommentEntity(modelBuilder);

            // Configure stored procedure result types
            ConfigureStoredProcedureEntities(modelBuilder);

            // Configure global query filters
            ConfigureGlobalQueryFilters(modelBuilder);

            // Configure value converters
            ConfigureValueConverters(modelBuilder);

            OnModelCreatingPartial(modelBuilder);
        }

        private void ConfigureUserEntity(ModelBuilder modelBuilder)
        {
            modelBuilder.Entity<User>(entity =>
            {
                // Configure properties
                entity.Property(e => e.CreatedAt)
                    .HasDefaultValueSql("GETUTCDATE()");

                entity.Property(e => e.UpdatedAt)
                    .HasDefaultValueSql("GETUTCDATE()");

                entity.Property(e => e.RowVersion)
                    .IsRowVersion();

                // Configure relationships
                entity.HasMany(u => u.UserRoles)
                    .WithOne(ur => ur.User)
                    .HasForeignKey(ur => ur.UserId)
                    .OnDelete(DeleteBehavior.Cascade);

                entity.HasMany(u => u.CreatedPosts)
                    .WithOne(p => p.Author)
                    .HasForeignKey(p => p.AuthorId)
                    .OnDelete(DeleteBehavior.Restrict);

                entity.HasMany(u => u.Comments)
                    .WithOne(c => c.Author)
                    .HasForeignKey(c => c.AuthorId)
                    .OnDelete(DeleteBehavior.Restrict);

                // Configure check constraints
                entity.HasCheckConstraint("CK_Users_Username_Length",
                    "LEN([Username]) >= 3");

                entity.HasCheckConstraint("CK_Users_Email_Format",
                    "[Email] LIKE '%_@_%.__%'");
            });
        }

        private void ConfigureStoredProcedureEntities(ModelBuilder modelBuilder)
        {
            // Configure keyless entities for stored procedure results
            modelBuilder.Entity<UserStatistics>(entity =>
            {
                entity.HasNoKey();
                entity.ToView("UserStatistics"); // Maps to view or stored procedure result
            });

            modelBuilder.Entity<UserActivitySummary>(entity =>
            {
                entity.HasNoKey();
                entity.ToView("UserActivitySummaries");
            });

            modelBuilder.Entity<PopularPost>(entity =>
            {
                entity.HasNoKey();
                entity.ToView("PopularPosts");
            });
        }

        private void ConfigureGlobalQueryFilters(ModelBuilder modelBuilder)
        {
            // Global query filters for soft delete
            modelBuilder.Entity<User>()
                .HasQueryFilter(u => u.IsActive);

            modelBuilder.Entity<Role>()
                .HasQueryFilter(r => r.IsActive);
        }

        private void ConfigureValueConverters(ModelBuilder modelBuilder)
        {
            // Configure value converters for enums, JSON, etc.
            // Example: JSON converter for complex types
            /*
            modelBuilder.Entity<User>()
                .Property(u => u.Preferences)
                .HasConversion(
                    v => JsonSerializer.Serialize(v),
                    v => JsonSerializer.Deserialize<UserPreferences>(v)
                );
            */
        }

        partial void OnModelCreatingPartial(ModelBuilder modelBuilder);

        // Stored procedure methods
        public async Task<List<UserStatistics>> GetUserStatisticsAsync(
            DateTime? fromDate = null,
            DateTime? toDate = null)
        {
            var fromParam = new SqlParameter("@FromDate", SqlDbType.DateTime2)
            {
                Value = fromDate ?? (object)DBNull.Value
            };

            var toParam = new SqlParameter("@ToDate", SqlDbType.DateTime2)
            {
                Value = toDate ?? (object)DBNull.Value
            };

            return await UserStatistics
                .FromSqlRaw("EXEC GetUserStatistics @FromDate, @ToDate", fromParam, toParam)
                .ToListAsync();
        }

        public async Task<List<UserActivitySummary>> GetUserActivitySummaryAsync(
            long userId,
            int days = 30)
        {
            var userIdParam = new SqlParameter("@UserId", userId);
            var daysParam = new SqlParameter("@Days", days);

            return await UserActivitySummaries
                .FromSqlRaw("EXEC GetUserActivitySummary @UserId, @Days", userIdParam, daysParam)
                .ToListAsync();
        }

        public async Task<List<PopularPost>> GetPopularPostsAsync(
            int topCount = 10,
            DateTime? fromDate = null)
        {
            var countParam = new SqlParameter("@TopCount", topCount);
            var fromParam = new SqlParameter("@FromDate", SqlDbType.DateTime2)
            {
                Value = fromDate ?? (object)DBNull.Value
            };

            return await PopularPosts
                .FromSqlRaw("EXEC GetPopularPosts @TopCount, @FromDate", countParam, fromParam)
                .ToListAsync();
        }

        public async Task<int> CreateUserWithRolesAsync(
            string username,
            string email,
            string passwordHash,
            string[] roleNames)
        {
            var usernameParam = new SqlParameter("@Username", username);
            var emailParam = new SqlParameter("@Email", email);
            var passwordParam = new SqlParameter("@PasswordHash", passwordHash);
            var rolesParam = new SqlParameter("@RoleNames", string.Join(",", roleNames));
            var userIdParam = new SqlParameter("@NewUserId", SqlDbType.BigInt)
            {
                Direction = ParameterDirection.Output
            };

            await Database.ExecuteSqlRawAsync(
                "EXEC CreateUserWithRoles @Username, @Email, @PasswordHash, @RoleNames, @NewUserId OUTPUT",
                usernameParam, emailParam, passwordParam, rolesParam, userIdParam);

            return (int)userIdParam.Value;
        }

        public async Task UpdateUserLastLoginAsync(long userId)
        {
            var userIdParam = new SqlParameter("@UserId", userId);
            var loginTimeParam = new SqlParameter("@LoginTime", DateTime.UtcNow);

            await Database.ExecuteSqlRawAsync(
                "EXEC UpdateUserLastLogin @UserId, @LoginTime",
                userIdParam, loginTimeParam);
        }

        // Override SaveChanges to handle auditing
        public override int SaveChanges()
        {
            UpdateAuditFields();
            return base.SaveChanges();
        }

        public override async Task<int> SaveChangesAsync(CancellationToken cancellationToken = default)
        {
            UpdateAuditFields();
            return await base.SaveChangesAsync(cancellationToken);
        }

        private void UpdateAuditFields()
        {
            var entries = ChangeTracker.Entries()
                .Where(e => e.Entity is IAuditable &&
                           (e.State == EntityState.Added || e.State == EntityState.Modified));

            var currentUserId = GetCurrentUserId(); // Implementation needed
            var currentTime = DateTime.UtcNow;

            foreach (var entry in entries)
            {
                if (entry.Entity is IAuditable auditable)
                {
                    if (entry.State == EntityState.Added)
                    {
                        auditable.CreatedAt = currentTime;
                        auditable.CreatedBy = currentUserId;
                    }

                    auditable.UpdatedAt = currentTime;
                    auditable.UpdatedBy = currentUserId;
                }
            }
        }

        private long? GetCurrentUserId()
        {
            // Implementation to get current user ID from HttpContext or other source
            // This should be injected through a service
            return null;
        }
    }
}
```

### Phase 3: Repository Pattern Implementation

#### 3.1 Generic Repository and Unit of Work
```csharp
// Repositories/IGenericRepository.cs
using System.Linq.Expressions;
using YourProject.Models.Entities;

namespace YourProject.Repositories
{
    public interface IGenericRepository<T> where T : class, IEntity
    {
        // Queries
        Task<T?> GetByIdAsync(object id, CancellationToken cancellationToken = default);
        Task<IEnumerable<T>> GetAllAsync(CancellationToken cancellationToken = default);
        Task<IEnumerable<T>> FindAsync(Expression<Func<T, bool>> predicate, CancellationToken cancellationToken = default);
        Task<T?> FirstOrDefaultAsync(Expression<Func<T, bool>> predicate, CancellationToken cancellationToken = default);

        // Pagination
        Task<(IEnumerable<T> Items, int TotalCount)> GetPagedAsync(
            int page,
            int pageSize,
            Expression<Func<T, bool>>? filter = null,
            Func<IQueryable<T>, IOrderedQueryable<T>>? orderBy = null,
            string includeProperties = "",
            CancellationToken cancellationToken = default);

        // Commands
        Task<T> AddAsync(T entity, CancellationToken cancellationToken = default);
        Task<IEnumerable<T>> AddRangeAsync(IEnumerable<T> entities, CancellationToken cancellationToken = default);
        void Update(T entity);
        void UpdateRange(IEnumerable<T> entities);
        void Remove(T entity);
        void RemoveRange(IEnumerable<T> entities);

        // Utilities
        Task<bool> ExistsAsync(Expression<Func<T, bool>> predicate, CancellationToken cancellationToken = default);
        Task<int> CountAsync(Expression<Func<T, bool>>? predicate = null, CancellationToken cancellationToken = default);
    }

    // Repositories/GenericRepository.cs
    public class GenericRepository<T> : IGenericRepository<T> where T : class, IEntity
    {
        protected readonly YourDbContext _context;
        protected readonly DbSet<T> _dbSet;

        public GenericRepository(YourDbContext context)
        {
            _context = context;
            _dbSet = context.Set<T>();
        }

        public virtual async Task<T?> GetByIdAsync(object id, CancellationToken cancellationToken = default)
        {
            return await _dbSet.FindAsync(new object[] { id }, cancellationToken);
        }

        public virtual async Task<IEnumerable<T>> GetAllAsync(CancellationToken cancellationToken = default)
        {
            return await _dbSet.ToListAsync(cancellationToken);
        }

        public virtual async Task<IEnumerable<T>> FindAsync(Expression<Func<T, bool>> predicate, CancellationToken cancellationToken = default)
        {
            return await _dbSet.Where(predicate).ToListAsync(cancellationToken);
        }

        public virtual async Task<T?> FirstOrDefaultAsync(Expression<Func<T, bool>> predicate, CancellationToken cancellationToken = default)
        {
            return await _dbSet.FirstOrDefaultAsync(predicate, cancellationToken);
        }

        public virtual async Task<(IEnumerable<T> Items, int TotalCount)> GetPagedAsync(
            int page,
            int pageSize,
            Expression<Func<T, bool>>? filter = null,
            Func<IQueryable<T>, IOrderedQueryable<T>>? orderBy = null,
            string includeProperties = "",
            CancellationToken cancellationToken = default)
        {
            IQueryable<T> query = _dbSet;

            if (filter != null)
            {
                query = query.Where(filter);
            }

            // Include properties
            foreach (var includeProperty in includeProperties.Split(',', StringSplitOptions.RemoveEmptyEntries))
            {
                query = query.Include(includeProperty.Trim());
            }

            var totalCount = await query.CountAsync(cancellationToken);

            if (orderBy != null)
            {
                query = orderBy(query);
            }

            var items = await query
                .Skip((page - 1) * pageSize)
                .Take(pageSize)
                .ToListAsync(cancellationToken);

            return (items, totalCount);
        }

        public virtual async Task<T> AddAsync(T entity, CancellationToken cancellationToken = default)
        {
            var entry = await _dbSet.AddAsync(entity, cancellationToken);
            return entry.Entity;
        }

        public virtual async Task<IEnumerable<T>> AddRangeAsync(IEnumerable<T> entities, CancellationToken cancellationToken = default)
        {
            await _dbSet.AddRangeAsync(entities, cancellationToken);
            return entities;
        }

        public virtual void Update(T entity)
        {
            _dbSet.Attach(entity);
            _context.Entry(entity).State = EntityState.Modified;
        }

        public virtual void UpdateRange(IEnumerable<T> entities)
        {
            _dbSet.UpdateRange(entities);
        }

        public virtual void Remove(T entity)
        {
            if (_context.Entry(entity).State == EntityState.Detached)
            {
                _dbSet.Attach(entity);
            }
            _dbSet.Remove(entity);
        }

        public virtual void RemoveRange(IEnumerable<T> entities)
        {
            _dbSet.RemoveRange(entities);
        }

        public virtual async Task<bool> ExistsAsync(Expression<Func<T, bool>> predicate, CancellationToken cancellationToken = default)
        {
            return await _dbSet.AnyAsync(predicate, cancellationToken);
        }

        public virtual async Task<int> CountAsync(Expression<Func<T, bool>>? predicate = null, CancellationToken cancellationToken = default)
        {
            if (predicate == null)
            {
                return await _dbSet.CountAsync(cancellationToken);
            }
            return await _dbSet.CountAsync(predicate, cancellationToken);
        }
    }
}
```

### Phase 4: API Controller Generation

#### 4.1 Enhanced User Controller with Repository Pattern
```csharp
// Controllers/UsersController.cs - Enhanced with Repository Pattern
[ApiController]
[Route("api/[controller]")]
[Produces("application/json")]
[ProducesResponseType(typeof(ErrorResponse), 500)]
public class UsersController : ControllerBase
{
    private readonly IUserRepository _userRepository;
    private readonly IUnitOfWork _unitOfWork;
    private readonly IMapper _mapper;
    private readonly ILogger<UsersController> _logger;
    private readonly IPasswordHasher<User> _passwordHasher;

    public UsersController(
        IUserRepository userRepository,
        IUnitOfWork unitOfWork,
        IMapper mapper,
        ILogger<UsersController> logger,
        IPasswordHasher<User> passwordHasher)
    {
        _userRepository = userRepository;
        _unitOfWork = unitOfWork;
        _mapper = mapper;
        _logger = logger;
        _passwordHasher = passwordHasher;
    }

    [HttpGet]
    [Authorize(Policy = "UserRead")]
    [ProducesResponseType(typeof(PaginatedResponse<UserDetailResponse>), 200)]
    public async Task<ActionResult<PaginatedResponse<UserDetailResponse>>> GetUsers(
        [FromQuery] int page = 1,
        [FromQuery] int pageSize = 10,
        [FromQuery] string? search = null,
        [FromQuery] string? role = null,
        [FromQuery] bool? isActive = null,
        [FromQuery] string? sortBy = "username",
        [FromQuery] string? sortOrder = "asc",
        CancellationToken cancellationToken = default)
    {
        try
        {
            // Build filter expression
            Expression<Func<User, bool>>? filter = null;

            if (!string.IsNullOrWhiteSpace(search))
            {
                filter = u => u.Username.Contains(search) ||
                             u.Email.Contains(search) ||
                             (u.FirstName != null && u.FirstName.Contains(search)) ||
                             (u.LastName != null && u.LastName.Contains(search));
            }

            if (!string.IsNullOrWhiteSpace(role))
            {
                var roleFilter = new Expression<Func<User, bool>>(u => u.UserRoles.Any(ur => ur.Role.Name == role));
                filter = filter == null ? roleFilter : CombineExpressions(filter, roleFilter);
            }

            if (isActive.HasValue)
            {
                var activeFilter = new Expression<Func<User, bool>>(u => u.IsActive == isActive.Value);
                filter = filter == null ? activeFilter : CombineExpressions(filter, activeFilter);
            }

            // Build order by
            Func<IQueryable<User>, IOrderedQueryable<User>>? orderBy = null;

            if (sortOrder?.ToLower() == "desc")
            {
                orderBy = sortBy?.ToLower() switch
                {
                    "username" => q => q.OrderByDescending(u => u.Username),
                    "email" => q => q.OrderByDescending(u => u.Email),
                    "createdat" => q => q.OrderByDescending(u => u.CreatedAt),
                    "lastloginat" => q => q.OrderByDescending(u => u.LastLoginAt),
                    _ => q => q.OrderByDescending(u => u.Username)
                };
            }
            else
            {
                orderBy = sortBy?.ToLower() switch
                {
                    "username" => q => q.OrderBy(u => u.Username),
                    "email" => q => q.OrderBy(u => u.Email),
                    "createdat" => q => q.OrderBy(u => u.CreatedAt),
                    "lastloginat" => q => q.OrderBy(u => u.LastLoginAt),
                    _ => q => q.OrderBy(u => u.Username)
                };
            }

            var (users, totalCount) = await _userRepository.GetPagedAsync(
                page,
                pageSize,
                filter,
                orderBy,
                "UserRoles.Role",
                cancellationToken);

            var response = new PaginatedResponse<UserDetailResponse>
            {
                Data = _mapper.Map<UserDetailResponse[]>(users),
                Pagination = new PaginationInfo
                {
                    CurrentPage = page,
                    PageSize = pageSize,
                    TotalPages = (int)Math.Ceiling((double)totalCount / pageSize),
                    TotalItems = totalCount,
                    HasNext = page < (int)Math.Ceiling((double)totalCount / pageSize),
                    HasPrevious = page > 1
                }
            };

            return Ok(response);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error retrieving users");
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    [HttpPost]
    [Authorize(Policy = "UserWrite")]
    [ProducesResponseType(typeof(UserDetailResponse), 201)]
    [ProducesResponseType(typeof(ErrorResponse), 400)]
    [ProducesResponseType(typeof(ErrorResponse), 409)]
    public async Task<ActionResult<UserDetailResponse>> CreateUser(
        [FromBody] CreateUserRequest request,
        CancellationToken cancellationToken = default)
    {
        try
        {
            // Business validation
            if (await _userRepository.UsernameExistsAsync(request.Username, null, cancellationToken))
            {
                return Conflict(CreateErrorResponse("CONFLICT", "Username already exists"));
            }

            if (await _userRepository.EmailExistsAsync(request.Email, null, cancellationToken))
            {
                return Conflict(CreateErrorResponse("CONFLICT", "Email already exists"));
            }

            // Create user entity
            var user = _mapper.Map<User>(request);
            user.PasswordHash = _passwordHasher.HashPassword(user, request.Password);
            user.CreatedAt = DateTime.UtcNow;
            user.UpdatedAt = DateTime.UtcNow;

            // Create user with roles
            var roleNames = request.Roles ?? new[] { "user" };
            await _userRepository.CreateWithRolesAsync(user, roleNames, cancellationToken);

            // Load created user with roles for response
            var createdUser = await _userRepository.GetWithRolesAsync(user.Id, cancellationToken);
            var response = _mapper.Map<UserDetailResponse>(createdUser);

            return CreatedAtAction(nameof(GetUser), new { id = user.Id }, response);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error creating user");
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    // Additional specialized endpoints
    [HttpGet("statistics")]
    [Authorize(Policy = "AdminRead")]
    [ProducesResponseType(typeof(UserStatistics[]), 200)]
    public async Task<ActionResult<UserStatistics[]>> GetUserStatistics(
        [FromQuery] DateTime? fromDate = null,
        [FromQuery] DateTime? toDate = null)
    {
        try
        {
            var statistics = await _userRepository.GetUserStatisticsAsync(fromDate, toDate);
            return Ok(statistics.ToArray());
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error retrieving user statistics");
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    [HttpGet("{id}/activity")]
    [Authorize(Policy = "UserRead")]
    [ProducesResponseType(typeof(UserActivitySummary[]), 200)]
    public async Task<ActionResult<UserActivitySummary[]>> GetUserActivity(
        long id,
        [FromQuery] int days = 30)
    {
        try
        {
            var activity = await _userRepository.GetUserActivitySummaryAsync(id, days);
            return Ok(activity.ToArray());
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error retrieving user activity");
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    private ErrorResponse CreateErrorResponse(string error, string message)
    {
        return new ErrorResponse
        {
            Error = error,
            Message = message,
            Timestamp = DateTime.UtcNow,
            RequestId = HttpContext.TraceIdentifier
        };
    }

    private Expression<Func<User, bool>> CombineExpressions(
        Expression<Func<User, bool>> expr1,
        Expression<Func<User, bool>> expr2)
    {
        var parameter = Expression.Parameter(typeof(User));
        var body = Expression.AndAlso(
            Expression.Invoke(expr1, parameter),
            Expression.Invoke(expr2, parameter)
        );
        return Expression.Lambda<Func<User, bool>>(body, parameter);
    }
}
```

## Deliverables

### 1. Complete Entity Framework Setup
- **Entity Models:** All database tables as EF Core entities
- **DbContext:** Enhanced context with relationships and stored procedures
- **Migrations:** Database versioning and deployment scripts
- **Configuration:** Connection strings and EF configuration

### 2. Repository Pattern Implementation
- **Generic Repository:** Reusable CRUD operations with type safety
- **Specialized Repositories:** Business-specific query methods
- **Unit of Work:** Transaction management and coordination
- **Stored Procedure Integration:** Type-safe stored procedure execution

### 3. API Controllers
- **Complete CRUD Operations:** All database operations exposed as REST endpoints
- **Advanced Queries:** Complex filtering, sorting, and pagination
- **Stored Procedure Endpoints:** Business logic execution through APIs
- **Error Handling:** Consistent error responses and logging

### 4. Performance and Best Practices
- **Query Optimization:** Efficient data access patterns
- **Lazy Loading:** Proper navigation property configuration
- **Caching:** Service-level caching strategies
- **Auditing:** Automatic audit field population

## Quality Gates

### ✅ Data Access Quality
- [ ] All database tables mapped to entities
- [ ] Proper relationships and foreign keys configured
- [ ] Stored procedures integrated with type safety
- [ ] Query optimization and performance testing
- [ ] Transaction management implemented

### ✅ API Completeness
- [ ] All CRUD operations available as REST endpoints
- [ ] Advanced querying capabilities (filtering, sorting, pagination)
- [ ] Stored procedure execution through APIs
- [ ] Proper error handling and validation
- [ ] Comprehensive logging and monitoring

### ✅ Code Quality
- [ ] Repository pattern properly implemented
- [ ] Dependency injection configured correctly
- [ ] Unit tests for repositories and controllers
- [ ] Performance benchmarks established
- [ ] Documentation and code comments complete

## Transition to Specialized Chatmodes

After completing Entity Framework code generation:

- **For API Enhancement**: Switch to **api-engineer** chatmode to enhance REST endpoints and add advanced API features
- **For Frontend Integration**: Switch to **frontend-engineer** chatmode to integrate generated APIs with client applications
- **For Security Implementation**: Switch to **security-engineer** chatmode to add authentication, authorization, and data protection

This prompt provides comprehensive guidance for generating complete Entity Framework code with API endpoints from database schemas, including stored procedures and advanced data access patterns.