---
description: Implement comprehensive database integration for desktop applications with advanced data access layers, migrations, offline synchronization, and performance optimization. Adapts to project specifications defined in copilot.instructions.md.
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

# Desktop Database Integration

## FUNCTIONAL REQUIREMENTS

**What needs to be accomplished:**

### Comprehensive Desktop Database Architecture
- **Local Database Implementation**: Implement robust local database solutions with SQLite, embedded PostgreSQL, or file-based databases for desktop applications
- **Data Access Layer Design**: Create efficient data access layers with ORM integration, connection management, and transaction handling
- **Migration and Versioning**: Implement database migration systems with version control and automatic schema updates
- **Performance Optimization**: Optimize database operations for desktop constraints including memory usage and disk I/O efficiency

### Desktop-Specific Data Management
- **Offline Data Synchronization**: Implement offline-first data management with synchronization capabilities for cloud-connected applications
- **Local Caching Strategies**: Design intelligent caching mechanisms for improved performance and offline operation
- **Data Backup and Recovery**: Create automatic backup systems with point-in-time recovery and data integrity validation
- **Cross-Platform Database Support**: Ensure database integration works across Windows, macOS, and Linux desktop environments

### Application Framework Integration
- **Desktop Framework Adaptation**: Integrate database access with desktop frameworks including WPF, Qt, Electron, JavaFX, or native applications
- **Reactive Data Binding**: Implement reactive data patterns with automatic UI updates when database changes occur
- **Multi-Threading Support**: Design thread-safe database access patterns for responsive desktop user interfaces
- **Configuration Management**: Create flexible configuration systems for database connections and application settings

### Security and Compliance
- **Data Encryption**: Implement encryption at rest and in transit for sensitive desktop application data
- **User Access Control**: Create user-based access control and data segmentation for multi-user desktop applications
- **Audit Trail Implementation**: Implement comprehensive audit logging for data changes and user actions
- **Compliance Integration**: Ensure database implementation meets industry-specific compliance requirements for desktop applications

## HIGH-LEVEL ALGORITHMS

**How to approach the problem:**

### 1. Desktop Technology Stack Analysis
```
1. Read copilot.instructions.md to extract:
   - Desktop framework and programming language preferences
   - Database system selection for desktop environment
   - Business domain and data modeling requirements
   - Performance and scalability expectations for desktop use

2. Desktop Environment Assessment:
   - Analyze target desktop platforms and constraints
   - Evaluate local storage requirements and limitations
   - Assess offline operation and synchronization needs
   - Review security and compliance requirements for desktop data
```

### 2. Local Database Design and Implementation
```
1. Database System Configuration:
   - Configure appropriate database system for desktop constraints
   - Set up connection pooling and resource management
   - Implement database initialization and seeding procedures
   - Configure performance optimization for local storage

2. Schema Design and Migration:
   - Design database schema optimized for desktop application needs
   - Implement migration system with version control and rollback
   - Create data seeding and initial setup procedures
   - Plan schema evolution and backward compatibility
```

### 3. Data Access Layer and ORM Integration
```
1. ORM Configuration and Setup:
   - Configure ORM framework appropriate for desktop technology stack
   - Implement entity mapping with desktop-specific optimizations
   - Set up connection management and transaction handling
   - Configure lazy loading and caching for performance

2. Repository and Service Pattern Implementation:
   - Create repository pattern with desktop-optimized data access
   - Implement service layer with business logic encapsulation
   - Add error handling and logging specific to desktop environments
   - Design reactive data patterns for UI integration
```

### 4. Offline Synchronization and Data Management
```
1. Offline Data Strategy:
   - Implement offline-first data access patterns
   - Create conflict resolution for data synchronization
   - Design incremental sync mechanisms for efficiency
   - Plan connectivity detection and automatic sync

2. Caching and Performance Optimization:
   - Implement intelligent caching strategies for desktop performance
   - Create data prefetching for improved user experience
   - Optimize queries for local database constraints
   - Design memory-efficient data loading patterns
```

### 5. Security, Backup, and Maintenance
```
1. Security Implementation:
   - Implement data encryption for sensitive information
   - Create user authentication and authorization for multi-user scenarios
   - Add audit logging and compliance tracking
   - Design secure data export and import capabilities

2. Backup and Maintenance:
   - Implement automatic backup and recovery systems
   - Create data integrity validation and repair procedures
   - Design maintenance and optimization routines
   - Plan disaster recovery and data migration procedures
```

## VALIDATION CRITERIA

**What conditions must be met:**

### ✅ Desktop Database Integration Excellence
- **Local Database Performance**: Optimized database operations meeting desktop performance requirements
- **Framework Integration**: Seamless integration with desktop application framework and UI components
- **Migration System**: Robust migration system with automatic schema updates and rollback capabilities
- **Cross-Platform Compatibility**: Database integration works consistently across target desktop platforms

### ✅ Data Management Quality
- **Offline Operation**: Comprehensive offline data access with intelligent synchronization when connectivity is available
- **Caching Efficiency**: Effective caching strategies improving application performance and user experience
- **Data Integrity**: Strong data integrity validation with automatic backup and recovery capabilities
- **Transaction Management**: Proper transaction handling with ACID compliance and rollback mechanisms

### ✅ Security and Compliance
- **Data Protection**: Appropriate encryption and access control for sensitive desktop application data
- **User Authentication**: Proper user authentication and authorization for multi-user desktop scenarios
- **Audit Trail**: Comprehensive audit logging for data changes and user actions
- **Compliance Implementation**: Meeting industry-specific compliance requirements for desktop data storage

### ✅ Development and Maintenance
- **Code Quality**: Clean, maintainable data access code following desktop development best practices
- **Error Handling**: Comprehensive error handling with proper user feedback and logging
- **Documentation Quality**: Complete documentation for database setup, configuration, and maintenance
- **Testing Support**: Comprehensive testing framework for database operations and data integrity validation

### ✅ GitHub Copilot Integration
- **Chatmode Coordination**: Seamless integration with frontend-engineer for UI data binding and security-engineer for data protection
- **Configuration Adaptation**: Proper adaptation to desktop technology stack and business domain requirements
- **Deployment Support**: Database integration supports desktop application packaging and deployment workflows
- **Performance Monitoring**: Integrated monitoring and diagnostics for desktop database performance

## USAGE EXAMPLES

**For different GitHub Copilot scenarios:**

### Scenario 1: Electron Desktop App with SQLite
```yaml
Context: Cross-platform desktop application built with Electron requiring local data storage
Technology Stack: Detected from copilot.instructions.md (Electron, React, TypeScript, SQLite, better-sqlite3)
Business Domain: Productivity application with document management and user preferences

Desktop Database Focus:
- Document metadata and content storage with full-text search
- User preferences and application configuration management
- Offline synchronization with cloud storage services
- Cross-platform data compatibility and migration

GitHub Copilot Workflow:
1. data-engineer chatmode → Implement SQLite integration with better-sqlite3 and migration system
2. frontend-engineer chatmode → Create React components with reactive data binding
3. security-engineer chatmode → Implement data encryption and secure storage
4. qa-engineer chatmode → Create comprehensive testing for offline and sync scenarios

Expected Deliverables:
- SQLite database integration with TypeScript ORM and migration system
- Reactive data layer with automatic UI updates for document changes
- Offline-first architecture with intelligent cloud synchronization
- Cross-platform data storage with encryption and backup capabilities
```

### Scenario 2: WPF Enterprise Application with Entity Framework
```yaml
Context: Enterprise WPF application with complex business data management and reporting
Technology Stack: Enterprise setup (.NET Framework, WPF, Entity Framework, SQL Server LocalDB)
Business Domain: Enterprise resource planning with complex data relationships and reporting

Desktop Database Focus:
- Complex business entity relationships with referential integrity
- Advanced reporting and data analytics with local processing
- User-based data access control and audit trails
- Enterprise data synchronization with central database

GitHub Copilot Workflow:
1. data-engineer chatmode → Implement Entity Framework with LocalDB and enterprise data patterns
2. frontend-engineer chatmode → Create WPF views with MVVM data binding and validation
3. security-engineer chatmode → Implement enterprise security and audit requirements
4. deployment-engineer chatmode → Set up enterprise deployment with database provisioning

Expected Deliverables:
- Entity Framework integration with SQL Server LocalDB and migration system
- WPF MVVM architecture with reactive data binding and validation
- Enterprise security implementation with user access control and audit trails
- Advanced reporting capabilities with local data processing and export
```

### Scenario 3: Qt Desktop Application with PostgreSQL
```yaml
Context: Cross-platform Qt application requiring robust database integration for scientific data
Technology Stack: Scientific setup (C++, Qt, PostgreSQL embedded, QML)
Business Domain: Scientific data analysis with complex calculations and data visualization

Desktop Database Focus:
- Scientific data storage with precision and performance requirements
- Complex query optimization for large datasets and calculations
- Data visualization integration with real-time updates
- Cross-platform deployment with embedded database distribution

GitHub Copilot Workflow:
1. data-engineer chatmode → Implement PostgreSQL embedded integration with Qt and C++
2. frontend-engineer chatmode → Create QML interfaces with data visualization components
3. qa-engineer chatmode → Implement performance testing for large dataset operations
4. deployment-engineer chatmode → Set up cross-platform deployment with database embedding

Expected Deliverables:
- PostgreSQL embedded integration with Qt C++ application and ORM patterns
- Scientific data models with precision handling and performance optimization
- Real-time data visualization with efficient update mechanisms
- Cross-platform deployment package with embedded database and migration tools
```

### Scenario 4: JavaFX Application with H2 Database
```yaml
Context: JavaFX desktop application for small business management with local data storage
Technology Stack: Java setup (JavaFX, Spring Boot, H2 Database, Hibernate)
Business Domain: Small business management with customer, inventory, and sales tracking

Desktop Database Focus:
- Business data management with customer and inventory relationships
- Local transaction processing with data validation and business rules
- Backup and restore capabilities for business continuity
- Simple deployment and maintenance for small business users

GitHub Copilot Workflow:
1. data-engineer chatmode → Implement H2 database with Hibernate and Spring Boot integration
2. frontend-engineer chatmode → Create JavaFX interfaces with business workflow support
3. qa-engineer chatmode → Create business logic testing and data validation
4. deployment-engineer chatmode → Set up simple deployment with automatic database setup

Expected Deliverables:
- H2 database integration with Hibernate ORM and Spring Boot configuration
- JavaFX business application with complete CRUD operations and validation
- Automatic backup and restore system for business data protection
- Simple deployment package with embedded database and business logic
```

## GitHub Copilot Integration

### Chatmode Coordination Patterns
```
Desktop Database Integration → data-engineer chatmode (lead)
├─ Desktop UI Integration → frontend-engineer chatmode
├─ Desktop Security Implementation → security-engineer chatmode
├─ Performance Testing → qa-engineer chatmode
└─ Desktop Deployment → deployment-engineer chatmode
```

### Context Handoff Information
- **To frontend-engineer**: Database models, reactive data patterns, UI binding requirements, offline capabilities
- **To security-engineer**: Data encryption requirements, access control specifications, audit trail needs
- **To qa-engineer**: Performance benchmarks, data integrity testing, offline scenario validation
- **To deployment-engineer**: Database deployment requirements, migration procedures, backup configurations

### GitHub Actions Integration
- **Database Migration**: Automated database schema deployment and version management
- **Desktop Testing**: Automated testing for desktop database operations across platforms
- **Performance Monitoring**: Continuous monitoring of desktop database performance and optimization
- **Deployment Automation**: Automated desktop application packaging with database integration

## Configuration Adaptation

**IMPORTANT**: This prompt adapts to project specifications by reading `copilot.instructions.md`:

- **Desktop Framework**: Automatically configures database integration for Electron, WPF, Qt, JavaFX, or other desktop frameworks
- **Database System**: Optimizes for SQLite, embedded PostgreSQL, H2, LocalDB, or other desktop-appropriate databases
- **Business Domain**: Adapts data modeling and validation patterns to productivity, enterprise, scientific, or business applications
- **Platform Requirements**: Configures cross-platform compatibility for Windows, macOS, and Linux deployment
- **Performance Constraints**: Optimizes for desktop-specific performance requirements including memory usage and responsiveness

**The data-engineer chatmode will automatically analyze project configuration and desktop requirements to deliver optimal desktop database integration while maintaining the functional requirements specified above.**
```

**Technology-specific database analysis:**
```bash
# For SQLite (most common for desktop)
find . -name "*.db" -o -name "*.sqlite*" | head -5
ls -la data/ db/ database/ 2>/dev/null

# For PostgreSQL/MySQL desktop connections
find . -name "*config*" -o -name "*connection*" | grep -i db | head -5
grep -r "postgresql\|mysql\|mariadb" . --include="*.py" --include="*.cpp" --include="*.cs" 2>/dev/null | head -5

# For embedded databases
find . -name "*.mdb" -o -name "*.accdb" -o -name "*.sdf" | head -5

# Check existing database scripts
find . -name "*.sql" -o -name "*migration*" -o -name "*schema*" | head -10
```

### Step 2: Application Technology Analysis
```bash
# Python applications
find . -name "requirements.txt" -o -name "*.py" | head -5
grep -r "sqlite3\|sqlalchemy\|peewee" . --include="*.py" 2>/dev/null | head -3

# C++ applications
find . -name "*.cpp" -o -name "*.h" -o -name "CMakeLists.txt" | head -5
grep -r "sqlite\|mysql\|postgresql" . --include="*.cpp" --include="*.h" 2>/dev/null | head -3

# .NET applications
find . -name "*.csproj" -o -name "*.cs" | head -5
grep -r "Entity.*Framework\|System.Data" . --include="*.cs" 2>/dev/null | head -3

# Java applications
find . -name "*.java" -o -name "pom.xml" | head -5
grep -r "hibernate\|jpa\|jdbc" . --include="*.java" 2>/dev/null | head -3
```

## Technology-Specific Database Integration

**⚠️ IMPORTANT: Select integration approach based on copilot.instructions.md database and language specification**

### Python/SQLite Integration

**Use when copilot.instructions.md specifies: Python, SQLite, desktop**

```python
# database/connection_manager.py - Database connection management
import sqlite3
import threading
import logging
from contextlib import contextmanager
from typing import Optional, Generator
import os

class DatabaseManager:
    _instance = None
    _lock = threading.Lock()

    def __new__(cls, db_path: str = "app_data.db"):
        if cls._instance is None:
            with cls._lock:
                if cls._instance is None:
                    cls._instance = super().__new__(cls)
                    cls._instance.db_path = db_path
                    cls._instance.logger = logging.getLogger(__name__)
                    cls._instance._initialize_database()
        return cls._instance

    def _initialize_database(self):
        """Initialize database with schema"""
        try:
            # Ensure database directory exists
            os.makedirs(os.path.dirname(self.db_path) if os.path.dirname(self.db_path) else '.', exist_ok=True)

            with self.get_connection() as conn:
                self._create_schema(conn)
                self._apply_migrations(conn)

        except Exception as e:
            self.logger.error(f"Database initialization failed: {e}")
            raise

    @contextmanager
    def get_connection(self) -> Generator[sqlite3.Connection, None, None]:
        """Context manager for database connections"""
        conn = sqlite3.connect(
            self.db_path,
            timeout=30.0,
            check_same_thread=False
        )
        conn.row_factory = sqlite3.Row  # Enable dict-like access
        conn.execute("PRAGMA foreign_keys = ON")  # Enable foreign key constraints
        conn.execute("PRAGMA journal_mode = WAL")  # Better concurrency

        try:
            yield conn
        except Exception as e:
            conn.rollback()
            self.logger.error(f"Database operation failed: {e}")
            raise
        else:
            conn.commit()
        finally:
            conn.close()

    def _create_schema(self, conn: sqlite3.Connection):
        """Create initial database schema"""
        schema_sql = '''
        -- Main entities table
        CREATE TABLE IF NOT EXISTS entities (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL UNIQUE,
            description TEXT,
            status TEXT DEFAULT 'active' CHECK (status IN ('active', 'inactive', 'archived')),
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            version INTEGER DEFAULT 1
        );

        -- Categories table
        CREATE TABLE IF NOT EXISTS categories (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL UNIQUE,
            color TEXT DEFAULT '#FFFFFF',
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );

        -- Many-to-many relationship
        CREATE TABLE IF NOT EXISTS entity_categories (
            entity_id INTEGER NOT NULL,
            category_id INTEGER NOT NULL,
            assigned_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            PRIMARY KEY (entity_id, category_id),
            FOREIGN KEY (entity_id) REFERENCES entities(id) ON DELETE CASCADE,
            FOREIGN KEY (category_id) REFERENCES categories(id) ON DELETE CASCADE
        );

        -- Settings table for application configuration
        CREATE TABLE IF NOT EXISTS app_settings (
            key TEXT PRIMARY KEY,
            value TEXT,
            data_type TEXT DEFAULT 'string',
            updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );

        -- Audit log table
        CREATE TABLE IF NOT EXISTS audit_log (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            table_name TEXT NOT NULL,
            record_id INTEGER NOT NULL,
            operation TEXT NOT NULL CHECK (operation IN ('INSERT', 'UPDATE', 'DELETE')),
            old_values TEXT,  -- JSON
            new_values TEXT,  -- JSON
            timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );

        -- Indexes for performance
        CREATE INDEX IF NOT EXISTS idx_entities_name ON entities(name);
        CREATE INDEX IF NOT EXISTS idx_entities_status ON entities(status);
        CREATE INDEX IF NOT EXISTS idx_entities_created_at ON entities(created_at);
        CREATE INDEX IF NOT EXISTS idx_categories_name ON categories(name);
        CREATE INDEX IF NOT EXISTS idx_audit_log_table_record ON audit_log(table_name, record_id);
        CREATE INDEX IF NOT EXISTS idx_audit_log_timestamp ON audit_log(timestamp);

        -- Triggers for updated_at
        CREATE TRIGGER IF NOT EXISTS tr_entities_updated_at
        AFTER UPDATE ON entities
        BEGIN
            UPDATE entities SET updated_at = CURRENT_TIMESTAMP WHERE id = NEW.id;
        END;

        CREATE TRIGGER IF NOT EXISTS tr_app_settings_updated_at
        AFTER UPDATE ON app_settings
        BEGIN
            UPDATE app_settings SET updated_at = CURRENT_TIMESTAMP WHERE key = NEW.key;
        END;
        '''

        conn.executescript(schema_sql)
        self.logger.info("Database schema created successfully")

    def _apply_migrations(self, conn: sqlite3.Connection):
        """Apply database migrations"""
        # Get current schema version
        try:
            cursor = conn.execute("SELECT value FROM app_settings WHERE key = 'schema_version'")
            current_version = int(cursor.fetchone()[0] if cursor.fetchone() else 0)
        except:
            current_version = 0

        migrations = [
            # Migration 1: Add email field to entities
            (1, '''
                ALTER TABLE entities ADD COLUMN email TEXT;
                CREATE INDEX IF NOT EXISTS idx_entities_email ON entities(email);
            '''),
            # Migration 2: Add preferences table
            (2, '''
                CREATE TABLE IF NOT EXISTS user_preferences (
                    id INTEGER PRIMARY KEY AUTOINCREMENT,
                    preference_key TEXT NOT NULL UNIQUE,
                    preference_value TEXT,
                    data_type TEXT DEFAULT 'string',
                    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
                    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
                );
            '''),
        ]

        for version, migration_sql in migrations:
            if current_version < version:
                try:
                    conn.executescript(migration_sql)
                    conn.execute(
                        "INSERT OR REPLACE INTO app_settings (key, value) VALUES (?, ?)",
                        ('schema_version', str(version))
                    )
                    self.logger.info(f"Applied migration version {version}")
                except Exception as e:
                    self.logger.error(f"Migration {version} failed: {e}")
                    raise

    def backup_database(self, backup_path: str) -> bool:
        """Create database backup"""
        try:
            with sqlite3.connect(self.db_path) as source:
                with sqlite3.connect(backup_path) as backup:
                    source.backup(backup)

            self.logger.info(f"Database backed up to {backup_path}")
            return True
        except Exception as e:
            self.logger.error(f"Backup failed: {e}")
            return False

    def vacuum_database(self) -> bool:
        """Optimize database by vacuuming"""
        try:
            with sqlite3.connect(self.db_path) as conn:
                conn.execute("VACUUM")

            self.logger.info("Database vacuumed successfully")
            return True
        except Exception as e:
            self.logger.error(f"Vacuum failed: {e}")
            return False
```

```python
# models/base_repository.py - Generic repository pattern
from abc import ABC, abstractmethod
from typing import List, Optional, TypeVar, Generic, Dict, Any
import json
from datetime import datetime
from database.connection_manager import DatabaseManager

T = TypeVar('T')

class BaseRepository(Generic[T], ABC):
    def __init__(self, db_manager: DatabaseManager):
        self.db_manager = db_manager
        self.table_name = self.get_table_name()

    @abstractmethod
    def get_table_name(self) -> str:
        pass

    @abstractmethod
    def from_row(self, row: dict) -> T:
        """Convert database row to entity"""
        pass

    @abstractmethod
    def to_dict(self, entity: T) -> Dict[str, Any]:
        """Convert entity to dictionary for database storage"""
        pass

    def get_by_id(self, entity_id: int) -> Optional[T]:
        """Get entity by ID"""
        with self.db_manager.get_connection() as conn:
            cursor = conn.execute(
                f"SELECT * FROM {self.table_name} WHERE id = ?",
                (entity_id,)
            )
            row = cursor.fetchone()
            return self.from_row(dict(row)) if row else None

    def get_all(self, limit: Optional[int] = None, offset: int = 0) -> List[T]:
        """Get all entities with optional pagination"""
        with self.db_manager.get_connection() as conn:
            sql = f"SELECT * FROM {self.table_name} ORDER BY created_at DESC"
            if limit:
                sql += f" LIMIT {limit} OFFSET {offset}"

            cursor = conn.execute(sql)
            return [self.from_row(dict(row)) for row in cursor.fetchall()]

    def create(self, entity: T) -> Optional[T]:
        """Create new entity"""
        entity_dict = self.to_dict(entity)

        # Remove id and auto-generated fields
        entity_dict.pop('id', None)
        entity_dict.pop('created_at', None)
        entity_dict.pop('updated_at', None)

        columns = ', '.join(entity_dict.keys())
        placeholders = ', '.join(['?' for _ in entity_dict])
        values = list(entity_dict.values())

        with self.db_manager.get_connection() as conn:
            cursor = conn.execute(
                f"INSERT INTO {self.table_name} ({columns}) VALUES ({placeholders})",
                values
            )

            # Log audit trail
            self._log_audit(conn, cursor.lastrowid, 'INSERT', None, entity_dict)

            return self.get_by_id(cursor.lastrowid)

    def update(self, entity_id: int, updates: Dict[str, Any]) -> Optional[T]:
        """Update existing entity"""
        # Get old values for audit
        old_entity = self.get_by_id(entity_id)
        if not old_entity:
            return None

        # Remove auto-generated fields
        updates.pop('id', None)
        updates.pop('created_at', None)
        updates.pop('updated_at', None)

        if not updates:
            return old_entity

        set_clause = ', '.join([f"{key} = ?" for key in updates.keys()])
        values = list(updates.values()) + [entity_id]

        with self.db_manager.get_connection() as conn:
            conn.execute(
                f"UPDATE {self.table_name} SET {set_clause} WHERE id = ?",
                values
            )

            # Log audit trail
            old_dict = self.to_dict(old_entity)
            self._log_audit(conn, entity_id, 'UPDATE', old_dict, updates)

            return self.get_by_id(entity_id)

    def delete(self, entity_id: int) -> bool:
        """Delete entity by ID"""
        old_entity = self.get_by_id(entity_id)
        if not old_entity:
            return False

        with self.db_manager.get_connection() as conn:
            cursor = conn.execute(
                f"DELETE FROM {self.table_name} WHERE id = ?",
                (entity_id,)
            )

            if cursor.rowcount > 0:
                # Log audit trail
                old_dict = self.to_dict(old_entity)
                self._log_audit(conn, entity_id, 'DELETE', old_dict, None)
                return True

        return False

    def search(self, search_term: str, columns: List[str] = None) -> List[T]:
        """Search entities by term"""
        if not columns:
            columns = ['name']  # Default search column

        conditions = [f"{col} LIKE ?" for col in columns]
        where_clause = " OR ".join(conditions)
        search_values = [f"%{search_term}%" for _ in columns]

        with self.db_manager.get_connection() as conn:
            cursor = conn.execute(
                f"SELECT * FROM {self.table_name} WHERE {where_clause} ORDER BY created_at DESC",
                search_values
            )
            return [self.from_row(dict(row)) for row in cursor.fetchall()]

    def count(self) -> int:
        """Get total count of entities"""
        with self.db_manager.get_connection() as conn:
            cursor = conn.execute(f"SELECT COUNT(*) FROM {self.table_name}")
            return cursor.fetchone()[0]

    def _log_audit(self, conn, record_id: int, operation: str,
                   old_values: Optional[Dict], new_values: Optional[Dict]):
        """Log audit trail"""
        try:
            conn.execute('''
                INSERT INTO audit_log (table_name, record_id, operation, old_values, new_values)
                VALUES (?, ?, ?, ?, ?)
            ''', (
                self.table_name,
                record_id,
                operation,
                json.dumps(old_values) if old_values else None,
                json.dumps(new_values) if new_values else None
            ))
        except Exception as e:
            # Don't fail the main operation if audit logging fails
            print(f"Audit logging failed: {e}")
```

### C++/SQLite Integration

**Use when copilot.instructions.md specifies: C++, SQLite, desktop**

```cpp
// include/database/DatabaseManager.h - C++ SQLite integration
#pragma once
#include <sqlite3.h>
#include <string>
#include <vector>
#include <memory>
#include <functional>
#include <mutex>

struct Entity {
    int id = 0;
    std::string name;
    std::string description;
    std::string status = "active";
    std::string created_at;
    std::string updated_at;
    int version = 1;
};

class DatabaseManager {
public:
    static DatabaseManager& getInstance(const std::string& db_path = "app_data.db");
    ~DatabaseManager();

    // Database operations
    bool initialize();
    bool backup(const std::string& backup_path);
    bool vacuum();

    // Entity operations
    std::vector<Entity> getAllEntities();
    std::unique_ptr<Entity> getEntityById(int id);
    std::unique_ptr<Entity> createEntity(const Entity& entity);
    bool updateEntity(int id, const Entity& entity);
    bool deleteEntity(int id);

    // Search operations
    std::vector<Entity> searchEntities(const std::string& search_term);
    int getEntityCount();

    // Transaction support
    class Transaction {
    public:
        Transaction(DatabaseManager& manager);
        ~Transaction();
        void commit();
        void rollback();

    private:
        DatabaseManager& manager_;
        bool committed_ = false;
        bool active_ = true;
    };

    std::unique_ptr<Transaction> beginTransaction();

private:
    DatabaseManager(const std::string& db_path);
    DatabaseManager(const DatabaseManager&) = delete;
    DatabaseManager& operator=(const DatabaseManager&) = delete;

    sqlite3* db_;
    std::string db_path_;
    mutable std::mutex db_mutex_;

    bool createSchema();
    bool applyMigrations();
    int getCurrentSchemaVersion();
    void logError(const std::string& message);
    void logAudit(const std::string& table_name, int record_id,
                  const std::string& operation, const std::string& old_values = "",
                  const std::string& new_values = "");

    // Prepared statements for performance
    sqlite3_stmt* stmt_get_all_entities_ = nullptr;
    sqlite3_stmt* stmt_get_entity_by_id_ = nullptr;
    sqlite3_stmt* stmt_insert_entity_ = nullptr;
    sqlite3_stmt* stmt_update_entity_ = nullptr;
    sqlite3_stmt* stmt_delete_entity_ = nullptr;

    void prepareFequentStatements();
    void finalizeStatements();
};
```

```cpp
// src/database/DatabaseManager.cpp
#include "database/DatabaseManager.h"
#include <iostream>
#include <sstream>
#include <fstream>
#include <filesystem>

DatabaseManager& DatabaseManager::getInstance(const std::string& db_path) {
    static DatabaseManager instance(db_path);
    return instance;
}

DatabaseManager::DatabaseManager(const std::string& db_path) : db_path_(db_path), db_(nullptr) {
    // Constructor
}

DatabaseManager::~DatabaseManager() {
    finalizeStatements();
    if (db_) {
        sqlite3_close(db_);
    }
}

bool DatabaseManager::initialize() {
    std::lock_guard<std::mutex> lock(db_mutex_);

    // Create directory if it doesn't exist
    std::filesystem::path db_file(db_path_);
    std::filesystem::create_directories(db_file.parent_path());

    int rc = sqlite3_open(db_path_.c_str(), &db_);
    if (rc != SQLITE_OK) {
        logError("Cannot open database: " + std::string(sqlite3_errmsg(db_)));
        return false;
    }

    // Configure SQLite
    sqlite3_exec(db_, "PRAGMA foreign_keys = ON", nullptr, nullptr, nullptr);
    sqlite3_exec(db_, "PRAGMA journal_mode = WAL", nullptr, nullptr, nullptr);
    sqlite3_exec(db_, "PRAGMA synchronous = NORMAL", nullptr, nullptr, nullptr);
    sqlite3_exec(db_, "PRAGMA cache_size = 10000", nullptr, nullptr, nullptr);
    sqlite3_exec(db_, "PRAGMA temp_store = memory", nullptr, nullptr, nullptr);

    if (!createSchema()) {
        logError("Failed to create database schema");
        return false;
    }

    if (!applyMigrations()) {
        logError("Failed to apply database migrations");
        return false;
    }

    prepareFequentStatements();

    return true;
}

bool DatabaseManager::createSchema() {
    const char* schema_sql = R"(
        -- Main entities table
        CREATE TABLE IF NOT EXISTS entities (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL UNIQUE,
            description TEXT,
            status TEXT DEFAULT 'active' CHECK (status IN ('active', 'inactive', 'archived')),
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            version INTEGER DEFAULT 1
        );

        -- Categories table
        CREATE TABLE IF NOT EXISTS categories (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            name TEXT NOT NULL UNIQUE,
            color TEXT DEFAULT '#FFFFFF',
            created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );

        -- Many-to-many relationship
        CREATE TABLE IF NOT EXISTS entity_categories (
            entity_id INTEGER NOT NULL,
            category_id INTEGER NOT NULL,
            assigned_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
            PRIMARY KEY (entity_id, category_id),
            FOREIGN KEY (entity_id) REFERENCES entities(id) ON DELETE CASCADE,
            FOREIGN KEY (category_id) REFERENCES categories(id) ON DELETE CASCADE
        );

        -- Settings table
        CREATE TABLE IF NOT EXISTS app_settings (
            key TEXT PRIMARY KEY,
            value TEXT,
            data_type TEXT DEFAULT 'string',
            updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );

        -- Audit log table
        CREATE TABLE IF NOT EXISTS audit_log (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            table_name TEXT NOT NULL,
            record_id INTEGER NOT NULL,
            operation TEXT NOT NULL CHECK (operation IN ('INSERT', 'UPDATE', 'DELETE')),
            old_values TEXT,
            new_values TEXT,
            timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
        );

        -- Indexes
        CREATE INDEX IF NOT EXISTS idx_entities_name ON entities(name);
        CREATE INDEX IF NOT EXISTS idx_entities_status ON entities(status);
        CREATE INDEX IF NOT EXISTS idx_entities_created_at ON entities(created_at);

        -- Triggers
        CREATE TRIGGER IF NOT EXISTS tr_entities_updated_at
        AFTER UPDATE ON entities
        BEGIN
            UPDATE entities SET updated_at = CURRENT_TIMESTAMP WHERE id = NEW.id;
        END;
    )";

    char* err_msg = nullptr;
    int rc = sqlite3_exec(db_, schema_sql, nullptr, nullptr, &err_msg);
    if (rc != SQLITE_OK) {
        logError("SQL error in schema creation: " + std::string(err_msg));
        sqlite3_free(err_msg);
        return false;
    }

    return true;
}

void DatabaseManager::prepareFequentStatements() {
    // Prepare frequently used statements for better performance
    sqlite3_prepare_v2(db_,
        "SELECT id, name, description, status, created_at, updated_at, version FROM entities ORDER BY created_at DESC",
        -1, &stmt_get_all_entities_, nullptr);

    sqlite3_prepare_v2(db_,
        "SELECT id, name, description, status, created_at, updated_at, version FROM entities WHERE id = ?",
        -1, &stmt_get_entity_by_id_, nullptr);

    sqlite3_prepare_v2(db_,
        "INSERT INTO entities (name, description, status) VALUES (?, ?, ?)",
        -1, &stmt_insert_entity_, nullptr);

    sqlite3_prepare_v2(db_,
        "UPDATE entities SET name = ?, description = ?, status = ?, version = version + 1 WHERE id = ?",
        -1, &stmt_update_entity_, nullptr);

    sqlite3_prepare_v2(db_,
        "DELETE FROM entities WHERE id = ?",
        -1, &stmt_delete_entity_, nullptr);
}

std::vector<Entity> DatabaseManager::getAllEntities() {
    std::lock_guard<std::mutex> lock(db_mutex_);
    std::vector<Entity> entities;

    if (!stmt_get_all_entities_) return entities;

    sqlite3_reset(stmt_get_all_entities_);

    while (sqlite3_step(stmt_get_all_entities_) == SQLITE_ROW) {
        Entity entity;
        entity.id = sqlite3_column_int(stmt_get_all_entities_, 0);
        entity.name = reinterpret_cast<const char*>(sqlite3_column_text(stmt_get_all_entities_, 1));

        const char* desc = reinterpret_cast<const char*>(sqlite3_column_text(stmt_get_all_entities_, 2));
        entity.description = desc ? desc : "";

        const char* status = reinterpret_cast<const char*>(sqlite3_column_text(stmt_get_all_entities_, 3));
        entity.status = status ? status : "active";

        const char* created = reinterpret_cast<const char*>(sqlite3_column_text(stmt_get_all_entities_, 4));
        entity.created_at = created ? created : "";

        const char* updated = reinterpret_cast<const char*>(sqlite3_column_text(stmt_get_all_entities_, 5));
        entity.updated_at = updated ? updated : "";

        entity.version = sqlite3_column_int(stmt_get_all_entities_, 6);

        entities.push_back(entity);
    }

    return entities;
}

std::unique_ptr<Entity> DatabaseManager::createEntity(const Entity& entity) {
    std::lock_guard<std::mutex> lock(db_mutex_);

    if (!stmt_insert_entity_) return nullptr;

    sqlite3_reset(stmt_insert_entity_);
    sqlite3_bind_text(stmt_insert_entity_, 1, entity.name.c_str(), -1, SQLITE_STATIC);
    sqlite3_bind_text(stmt_insert_entity_, 2, entity.description.c_str(), -1, SQLITE_STATIC);
    sqlite3_bind_text(stmt_insert_entity_, 3, entity.status.c_str(), -1, SQLITE_STATIC);

    int rc = sqlite3_step(stmt_insert_entity_);
    if (rc == SQLITE_DONE) {
        int new_id = static_cast<int>(sqlite3_last_insert_rowid(db_));
        logAudit("entities", new_id, "INSERT", "",
                 "name=" + entity.name + ",desc=" + entity.description);

        return getEntityById(new_id);
    }

    logError("Failed to insert entity: " + std::string(sqlite3_errmsg(db_)));
    return nullptr;
}

DatabaseManager::Transaction::Transaction(DatabaseManager& manager) : manager_(manager) {
    sqlite3_exec(manager_.db_, "BEGIN TRANSACTION", nullptr, nullptr, nullptr);
}

DatabaseManager::Transaction::~Transaction() {
    if (active_ && !committed_) {
        rollback();
    }
}

void DatabaseManager::Transaction::commit() {
    if (active_ && !committed_) {
        sqlite3_exec(manager_.db_, "COMMIT", nullptr, nullptr, nullptr);
        committed_ = true;
        active_ = false;
    }
}

void DatabaseManager::Transaction::rollback() {
    if (active_) {
        sqlite3_exec(manager_.db_, "ROLLBACK", nullptr, nullptr, nullptr);
        active_ = false;
    }
}

std::unique_ptr<DatabaseManager::Transaction> DatabaseManager::beginTransaction() {
    return std::make_unique<Transaction>(*this);
}

void DatabaseManager::logError(const std::string& message) {
    std::cerr << "DatabaseManager Error: " << message << std::endl;
}
```

### .NET Entity Framework Integration

**Use when copilot.instructions.md specifies: C#, .NET, Entity Framework**

```csharp
// Data/ApplicationDbContext.cs - Entity Framework context
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.Logging;
using DesktopApp.Models;

namespace DesktopApp.Data
{
    public class ApplicationDbContext : DbContext
    {
        private readonly ILogger<ApplicationDbContext> _logger;

        public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options,
                                   ILogger<ApplicationDbContext> logger) : base(options)
        {
            _logger = logger;
        }

        public DbSet<Entity> Entities { get; set; }
        public DbSet<Category> Categories { get; set; }
        public DbSet<AppSetting> AppSettings { get; set; }
        public DbSet<AuditLog> AuditLogs { get; set; }

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            base.OnModelCreating(modelBuilder);

            // Entity configuration
            modelBuilder.Entity<Entity>(entity =>
            {
                entity.HasKey(e => e.Id);
                entity.Property(e => e.Name).IsRequired().HasMaxLength(200);
                entity.Property(e => e.Status).HasDefaultValue("active");
                entity.Property(e => e.Version).HasDefaultValue(1);
                entity.Property(e => e.CreatedAt).HasDefaultValueSql("datetime('now')");
                entity.Property(e => e.UpdatedAt).HasDefaultValueSql("datetime('now')");

                entity.HasIndex(e => e.Name).IsUnique();
                entity.HasIndex(e => e.Status);
                entity.HasIndex(e => e.CreatedAt);
            });

            // Category configuration
            modelBuilder.Entity<Category>(entity =>
            {
                entity.HasKey(c => c.Id);
                entity.Property(c => c.Name).IsRequired().HasMaxLength(100);
                entity.Property(c => c.Color).HasDefaultValue("#FFFFFF");
                entity.HasIndex(c => c.Name).IsUnique();
            });

            // Many-to-many relationship
            modelBuilder.Entity<Entity>()
                .HasMany(e => e.Categories)
                .WithMany(c => c.Entities)
                .UsingEntity<Dictionary<string, object>>(
                    "EntityCategories",
                    j => j.HasOne<Category>().WithMany().HasForeignKey("CategoryId"),
                    j => j.HasOne<Entity>().WithMany().HasForeignKey("EntityId"),
                    j =>
                    {
                        j.Property<DateTime>("AssignedAt").HasDefaultValueSql("datetime('now')");
                        j.HasKey("EntityId", "CategoryId");
                    });

            // App settings configuration
            modelBuilder.Entity<AppSetting>(entity =>
            {
                entity.HasKey(s => s.Key);
                entity.Property(s => s.DataType).HasDefaultValue("string");
                entity.Property(s => s.UpdatedAt).HasDefaultValueSql("datetime('now')");
            });

            // Audit log configuration
            modelBuilder.Entity<AuditLog>(entity =>
            {
                entity.HasKey(a => a.Id);
                entity.Property(a => a.TableName).IsRequired().HasMaxLength(50);
                entity.Property(a => a.Operation).IsRequired();
                entity.Property(a => a.Timestamp).HasDefaultValueSql("datetime('now')");

                entity.HasIndex(a => new { a.TableName, a.RecordId });
                entity.HasIndex(a => a.Timestamp);
            });

            // Seed default data
            SeedData(modelBuilder);
        }

        private static void SeedData(ModelBuilder modelBuilder)
        {
            modelBuilder.Entity<AppSetting>().HasData(
                new AppSetting { Key = "schema_version", Value = "1", DataType = "integer" },
                new AppSetting { Key = "app_initialized", Value = "true", DataType = "boolean" }
            );

            modelBuilder.Entity<Category>().HasData(
                new Category { Id = 1, Name = "General", Color = "#007ACC" },
                new Category { Id = 2, Name = "Important", Color = "#FF6B35" }
            );
        }

        public override int SaveChanges()
        {
            AddAuditLogs();
            return base.SaveChanges();
        }

        public override async Task<int> SaveChangesAsync(CancellationToken cancellationToken = default)
        {
            AddAuditLogs();
            return await base.SaveChangesAsync(cancellationToken);
        }

        private void AddAuditLogs()
        {
            var auditEntries = new List<AuditLog>();

            foreach (var entry in ChangeTracker.Entries())
            {
                if (entry.Entity is AuditLog || entry.State == EntityState.Unchanged)
                    continue;

                var auditLog = new AuditLog
                {
                    TableName = entry.Entity.GetType().Name,
                    RecordId = GetPrimaryKeyValue(entry),
                    Operation = entry.State.ToString().ToUpper(),
                    Timestamp = DateTime.UtcNow
                };

                if (entry.State == EntityState.Modified)
                {
                    auditLog.OldValues = GetOriginalValues(entry);
                    auditLog.NewValues = GetCurrentValues(entry);
                }
                else if (entry.State == EntityState.Added)
                {
                    auditLog.NewValues = GetCurrentValues(entry);
                }
                else if (entry.State == EntityState.Deleted)
                {
                    auditLog.OldValues = GetOriginalValues(entry);
                }

                auditEntries.Add(auditLog);
            }

            AuditLogs.AddRange(auditEntries);
        }

        private int GetPrimaryKeyValue(EntityEntry entry)
        {
            var keyProperty = entry.Properties.FirstOrDefault(p => p.Metadata.IsPrimaryKey());
            return keyProperty?.CurrentValue as int? ?? 0;
        }

        private string GetOriginalValues(EntityEntry entry)
        {
            var values = new Dictionary<string, object>();
            foreach (var property in entry.Properties)
            {
                values[property.Metadata.Name] = property.OriginalValue;
            }
            return System.Text.Json.JsonSerializer.Serialize(values);
        }

        private string GetCurrentValues(EntityEntry entry)
        {
            var values = new Dictionary<string, object>();
            foreach (var property in entry.Properties)
            {
                values[property.Metadata.Name] = property.CurrentValue;
            }
            return System.Text.Json.JsonSerializer.Serialize(values);
        }
    }
}
```

## Quality Gates

### ✅ Database Integration
- [ ] Database technology matches copilot.instructions.md specification
- [ ] Connection management properly implemented
- [ ] Migration system in place
- [ ] Error handling and logging configured

### ✅ Data Access Layer
- [ ] Repository pattern implemented where appropriate
- [ ] ORM configuration correct for technology stack
- [ ] Audit logging implemented
- [ ] Transaction support available

### ✅ Performance & Reliability
- [ ] Database indexes created for performance
- [ ] Connection pooling configured appropriately
- [ ] Backup and maintenance procedures defined
- [ ] Concurrency handling implemented

## Transition to Specialized Chatmodes

After completing desktop database integration:

- **For API Development**: Switch to **api-engineer** chatmode to implement data access APIs for desktop application services
- **For Frontend Integration**: Switch to **frontend-engineer** chatmode to connect UI components with database layer
- **For Security Implementation**: Switch to **security-engineer** chatmode to implement data encryption and access controls

**This prompt ensures database integration follows best practices for the specific technology stack defined in copilot.instructions.md, providing robust data access for desktop applications.**