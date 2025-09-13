---
description: Generate comprehensive Swagger/OpenAPI documentation from existing backend code with complete endpoint coverage, model definitions, and interactive examples. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - search
  - editFiles
  - runCommands
  - githubRepo
  - vscodeAPI
---

# Swagger Documentation Generation from Existing Backend Code

Generate comprehensive Swagger/OpenAPI documentation from existing backend API code, ensuring complete coverage of endpoints, models, and business logic with production-ready documentation standards.

## Context Adaptation

**IMPORTANT**: Always read the `copilot.instructions.md` file in the project root directory at the beginning of your work to adapt your implementation to:

- Backend framework (Spring Boot, .NET Core, NestJS, FastAPI, etc.)
- API architecture patterns (RESTful, GraphQL documentation approach)
- Business domain requirements and industry-specific documentation standards
- Integration requirements for client SDK generation and API consumption patterns

## Mission

Generate comprehensive Swagger/OpenAPI documentation from existing backend API code, ensuring complete coverage of endpoints, models, and business logic with production-ready documentation standards.

## Documentation Generation Process

### Step 1: Code Analysis and Discovery

**Backend Code Structure Analysis:**
```bash
# Analyze project structure and technology stack
cat copilot.instructions.md | grep -A 5 "primary_language\|Backend\|Technologies"

# Discover API controllers and route definitions
find . -name "*.cs" -o -name "*.js" -o -name "*.ts" -o -name "*.py" -o -name "*.java" | head -20
tree src/ -I "node_modules|bin|obj|target|dist|build" -L 3

# Technology-specific controller discovery
find . -name "*Controller*.cs" -o -name "*Controller*.java" -o -name "*controller*.ts" -o -name "*routes*.py" | head -10
find . -name "*Model*.cs" -o -name "*Entity*.java" -o -name "*dto*.ts" -o -name "*schema*.py" | head -10
```

**Existing Documentation Review:**
```bash
# Check for existing API documentation
find . -name "*.yml" -o -name "*.yaml" -o -name "*.json" | grep -i -E "swagger|openapi" | head -5
find . -name "*swagger*" -o -name "*openapi*" -type f | head -5
ls -la docs/ api-docs/ swagger/ 2>/dev/null
```

**Key Analysis Points:**
- **Controller/Route Files**: Identify all API controllers and route definitions
- **Model/DTO Classes**: Catalog all data transfer objects and models
- **Business Logic**: Understand service layer and business operations
- **Authentication/Authorization**: Document security implementations
- **Error Handling**: Catalog custom exceptions and error responses

### Step 2: Technology-Specific Documentation Generation

**Java + Spring Boot + SpringDoc OpenAPI:**
```java
// Maven Dependencies
/*
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.2.0</version>
</dependency>
*/

// OpenAPI Configuration
@Configuration
@EnableOpenApi
public class OpenApiConfig {
    
    @Bean
    public OpenAPI customOpenAPI(@Value("${app.version:1.0.0}") String appVersion) {
        return new OpenAPI()
            .info(new Info()
                .title("Company API")
                .version(appVersion)
                .description("""
                    Comprehensive API documentation generated from Spring Boot code.
                    
                    ## Authentication
                    This API uses JWT Bearer token authentication. Include the token in the Authorization header:
                    ```
                    Authorization: Bearer <your_jwt_token>
                    ```
                    
                    ## Error Handling
                    All errors follow a standardized format with appropriate HTTP status codes.
                    Validation errors include detailed field-level information.
                    
                    ## Rate Limiting
                    API requests are rate-limited to prevent abuse. Current limits:
                    - 100 requests per minute for authenticated users
                    - 20 requests per minute for unauthenticated requests
                    """)
                .contact(new Contact()
                    .name("API Support Team")
                    .email("api-support@company.com")
                    .url("https://company.com/support"))
                .license(new License()
                    .name("Apache 2.0")
                    .url("https://www.apache.org/licenses/LICENSE-2.0.html")))
            .servers(Arrays.asList(
                new Server().url("https://api.company.com/v1").description("Production server"),
                new Server().url("https://staging-api.company.com/v1").description("Staging server"),
                new Server().url("http://localhost:8080/v1").description("Development server")
            ))
            .addSecurityItem(new SecurityRequirement().addList("bearerAuth"))
            .components(new Components()
                .addSecuritySchemes("bearerAuth",
                    new SecurityScheme()
                        .type(SecurityScheme.Type.HTTP)
                        .scheme("bearer")
                        .bearerFormat("JWT")
                        .description("JWT Bearer token authentication")));
    }
}

// Enhanced Controller Documentation
@RestController
@RequestMapping("/api/v1/users")
@Tag(name = "Users", description = "User management operations")
@SecurityRequirement(name = "bearerAuth")
public class UserController {
    
    private final UserService userService;
    
    @GetMapping("/{id}")
    @Operation(
        summary = "Get user by ID",
        description = """
            Retrieves detailed user information by unique identifier.
            
            **Business Logic:**
            - Validates user ID format
            - Checks user existence and access permissions
            - Applies user visibility rules based on requesting user's role
            - Returns user with related data based on include parameter
            
            **Permissions Required:**
            - User.Read (for own profile) or Admin.Users.Read (for any user)
            
            **Performance Notes:**
            - Response cached for 5 minutes for non-admin users
            - Include parameter triggers additional database queries
            """
    )
    @ApiResponses(value = {
        @ApiResponse(
            responseCode = "200",
            description = "User retrieved successfully",
            content = @Content(
                mediaType = "application/json",
                schema = @Schema(implementation = UserDetailResponse.class),
                examples = {
                    @ExampleObject(
                        name = "Standard User",
                        summary = "Example of standard user response",
                        description = "Response when retrieving a standard user with basic profile information",
                        value = """
                            {
                              "id": 12345,
                              "username": "john.doe",
                              "email": "john.doe@example.com",
                              "profile": {
                                "firstName": "John",
                                "lastName": "Doe",
                                "avatar": "https://cdn.example.com/avatars/12345.jpg",
                                "bio": "Software developer passionate about clean code"
                              },
                              "roles": ["user"],
                              "createdAt": "2024-01-15T10:30:00Z",
                              "isActive": true
                            }
                            """
                    ),
                    @ExampleObject(
                        name = "Admin User",
                        summary = "Example of admin user response",
                        description = "Response when retrieving an administrative user with extended permissions",
                        value = """
                            {
                              "id": 67890,
                              "username": "admin",
                              "email": "admin@company.com",
                              "profile": {
                                "firstName": "System",
                                "lastName": "Administrator"
                              },
                              "roles": ["admin", "user"],
                              "createdAt": "2023-12-01T08:00:00Z",
                              "isActive": true,
                              "adminMetadata": {
                                "lastLoginAt": "2024-03-20T09:15:00Z",
                                "loginCount": 1247
                              }
                            }
                            """
                    )
                }
            )
        ),
        @ApiResponse(
            responseCode = "400",
            description = "Invalid user ID format",
            content = @Content(
                mediaType = "application/json",
                schema = @Schema(implementation = ErrorResponse.class),
                examples = @ExampleObject(
                    value = """
                        {
                          "error": "VALIDATION_ERROR",
                          "message": "Invalid user ID format",
                          "details": [
                            {
                              "field": "id",
                              "message": "User ID must be a positive integer",
                              "code": "INVALID_FORMAT"
                            }
                          ],
                          "timestamp": "2024-03-20T14:45:30Z",
                          "requestId": "req_abc123"
                        }
                        """
                )
            )
        ),
        @ApiResponse(
            responseCode = "401",
            description = "Authentication required",
            content = @Content(
                mediaType = "application/json",
                schema = @Schema(implementation = ErrorResponse.class)
            )
        ),
        @ApiResponse(
            responseCode = "403",
            description = "Insufficient permissions to access this user",
            content = @Content(
                mediaType = "application/json",
                schema = @Schema(implementation = ErrorResponse.class)
            )
        ),
        @ApiResponse(
            responseCode = "404",
            description = "User not found",
            content = @Content(
                mediaType = "application/json",
                schema = @Schema(implementation = ErrorResponse.class)
            )
        )
    })
    public ResponseEntity<UserDetailResponse> getUserById(
            @Parameter(
                description = "Unique user identifier",
                required = true,
                example = "12345",
                schema = @Schema(type = "integer", format = "int64", minimum = "1")
            )
            @PathVariable Long id,
            
            @Parameter(
                description = "Related data to include in response",
                required = false,
                example = "profile,roles",
                schema = @Schema(
                    type = "array",
                    allowableValues = {"profile", "preferences", "roles", "adminMetadata"}
                )
            )
            @RequestParam(required = false) List<String> include
    ) {
        UserDetailResponse user = userService.getUserById(id, include);
        return ResponseEntity.ok(user);
    }
}

// Comprehensive Model Documentation
@Schema(description = "Complete user information with related data")
public class UserDetailResponse {
    
    @Schema(
        description = "Unique user identifier",
        example = "12345",
        minimum = "1",
        requiredMode = Schema.RequiredMode.REQUIRED
    )
    private Long id;
    
    @Schema(
        description = "Unique username for authentication",
        example = "john.doe",
        pattern = "^[a-zA-Z0-9_-]{3,30}$",
        minLength = 3,
        maxLength = 30,
        requiredMode = Schema.RequiredMode.REQUIRED
    )
    private String username;
    
    @Schema(
        description = "User's primary email address",
        example = "john.doe@example.com",
        format = "email",
        requiredMode = Schema.RequiredMode.REQUIRED
    )
    private String email;
    
    @Schema(
        description = "User's profile information",
        implementation = UserProfile.class
    )
    private UserProfile profile;
    
    @Schema(
        description = "User's assigned roles determining access permissions",
        example = "[\"user\"]",
        allowableValues = {"user", "admin", "moderator", "guest"}
    )
    private List<String> roles;
    
    @Schema(
        description = "Account creation timestamp",
        example = "2024-01-15T10:30:00Z",
        format = "date-time",
        requiredMode = Schema.RequiredMode.REQUIRED
    )
    private Instant createdAt;
    
    @Schema(
        description = "Last profile update timestamp",
        example = "2024-03-20T14:45:30Z",
        format = "date-time"
    )
    private Instant updatedAt;
    
    @Schema(
        description = "Account status indicating if user can access the system",
        example = "true",
        defaultValue = "true",
        requiredMode = Schema.RequiredMode.REQUIRED
    )
    private Boolean isActive;
    
    // Additional fields for admin users only
    @Schema(
        description = "Administrative metadata (only visible to admin users)",
        implementation = AdminMetadata.class
    )
    private AdminMetadata adminMetadata;
}

// Application Properties Configuration
# application.yml
springdoc:
  api-docs:
    path: /api-docs
    enabled: true
  swagger-ui:
    path: /swagger-ui.html
    tryItOutEnabled: true
    operationsSorter: method
    tagsSorter: alpha
    displayRequestDuration: true
    docExpansion: none
    deepLinking: true
    defaultModelsExpandDepth: 2
    defaultModelExpandDepth: 2
  show-actuator: false
  writer-with-default-pretty-printer: true
  override-with-generic-response: false
  auto-tag-classes: true
```

**.NET Core + Swashbuckle Implementation:**
```csharp
// Enhanced Startup Configuration
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers();
        
        services.AddSwaggerGen(c =>
        {
            c.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "Company API",
                Version = "v1",
                Description = """
                    Comprehensive API documentation generated from .NET Core code.
                    
                    ## Features
                    - RESTful API design following industry best practices
                    - JWT-based authentication and role-based authorization
                    - Comprehensive input validation and error handling
                    - Rate limiting and request throttling
                    - Detailed request/response examples
                    
                    ## Getting Started
                    1. Obtain an API key or JWT token through the authentication endpoint
                    2. Include the token in the Authorization header for protected endpoints
                    3. Review the examples provided for each endpoint
                    4. Use the "Try it out" feature to test API calls directly
                    """,
                Contact = new OpenApiContact
                {
                    Name = "API Support Team",
                    Email = "api-support@company.com",
                    Url = new Uri("https://company.com/support")
                },
                License = new OpenApiLicense
                {
                    Name = "MIT License",
                    Url = new Uri("https://opensource.org/licenses/MIT")
                }
            });
            
            // Add comprehensive security definitions
            c.AddSecurityDefinition("Bearer", new OpenApiSecurityScheme
            {
                Description = """
                    JWT Authorization header using the Bearer scheme.
                    
                    Enter 'Bearer' [space] and then your token in the text input below.
                    
                    Example: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
                    """,
                Name = "Authorization",
                In = ParameterLocation.Header,
                Type = SecuritySchemeType.ApiKey,
                Scheme = "Bearer"
            });
            
            c.AddSecurityDefinition("ApiKey", new OpenApiSecurityScheme
            {
                Description = """
                    API Key authentication for service-to-service communication.
                    
                    Include your API key in the X-API-Key header.
                    Contact the API administrator for key provisioning.
                    """,
                Name = "X-API-Key",
                In = ParameterLocation.Header,
                Type = SecuritySchemeType.ApiKey
            });
            
            c.AddSecurityRequirement(new OpenApiSecurityRequirement
            {
                {
                    new OpenApiSecurityScheme
                    {
                        Reference = new OpenApiReference
                        {
                            Type = ReferenceType.SecurityScheme,
                            Id = "Bearer"
                        }
                    },
                    Array.Empty<string>()
                }
            });
            
            // Include XML comments for detailed documentation
            var xmlFilename = $"{Assembly.GetExecutingAssembly().GetName().Name}.xml";
            var xmlPath = Path.Combine(AppContext.BaseDirectory, xmlFilename);
            c.IncludeXmlComments(xmlPath, includeControllerXmlComments: true);
            
            // Enable annotations for enhanced documentation
            c.EnableAnnotations();
            
            // Add custom schema filters for better examples
            c.SchemaFilter<ExampleSchemaFilter>();
            c.OperationFilter<ExampleOperationFilter>();
            c.DocumentFilter<TagDescriptionsDocumentFilter>();
            
            // Configure for better API grouping
            c.TagActionsBy(api => new[] { api.GroupName ?? api.ActionDescriptor.RouteValues["controller"] });
            c.DocInclusionPredicate((name, api) => true);
        });
    }
    
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        // Enhanced Swagger UI configuration
        app.UseSwagger(c =>
        {
            c.RouteTemplate = "api-docs/{documentName}/swagger.json";
        });
        
        app.UseSwaggerUI(c =>
        {
            c.SwaggerEndpoint("/api-docs/v1/swagger.json", "Company API V1");
            c.RoutePrefix = "swagger";
            
            // Enhanced UI features
            c.DisplayRequestDuration();
            c.DocExpansion(DocExpansion.None);
            c.EnableDeepLinking();
            c.EnableFilter();
            c.ShowExtensions();
            c.EnableValidator();
            c.SupportedSubmitMethods(SubmitMethod.Get, SubmitMethod.Post, SubmitMethod.Put, SubmitMethod.Delete, SubmitMethod.Patch);
            
            // Custom CSS and JavaScript
            c.InjectStylesheet("/swagger-ui/custom.css");
            c.InjectJavascript("/swagger-ui/custom.js");
            
            // OAuth configuration if needed
            c.OAuthClientId("swagger-ui");
            c.OAuthAppName("Company API - Swagger UI");
            c.OAuthUsePkce();
        });
    }
}

// Enhanced Controller Documentation
/// <summary>
/// User management operations
/// </summary>
/// <remarks>
/// This controller provides comprehensive user management functionality including:
/// - User registration and profile management
/// - Authentication and authorization operations
/// - User search and filtering capabilities
/// - Administrative user management functions
/// 
/// All operations require appropriate authentication and authorization.
/// Rate limiting is applied based on user role and endpoint sensitivity.
/// </remarks>
[ApiController]
[Route("api/v1/[controller]")]
[SwaggerTag("User management operations including registration, authentication, and profile management")]
[Produces("application/json")]
[Consumes("application/json")]
public class UsersController : ControllerBase
{
    private readonly IUserService _userService;
    
    /// <summary>
    /// Retrieves detailed user information by unique identifier
    /// </summary>
    /// <param name="id">Unique user identifier</param>
    /// <param name="include">Related data to include in response</param>
    /// <returns>User details with requested related data</returns>
    /// <remarks>
    /// <para><strong>Business Logic:</strong></para>
    /// <list type="bullet">
    /// <item>Validates user ID format and range</item>
    /// <item>Checks user existence in the system</item>
    /// <item>Applies user visibility rules based on requesting user's permissions</item>
    /// <item>Returns user data with optionally included related information</item>
    /// </list>
    /// 
    /// <para><strong>Permissions Required:</strong></para>
    /// <list type="bullet">
    /// <item>User.Read permission for accessing own profile</item>
    /// <item>Admin.Users.Read permission for accessing any user profile</item>
    /// </list>
    /// 
    /// <para><strong>Performance Considerations:</strong></para>
    /// <list type="bullet">
    /// <item>Response is cached for 5 minutes for non-admin users</item>
    /// <item>Including related data may result in additional database queries</item>
    /// <item>Admin metadata is only included for users with appropriate permissions</item>
    /// </list>
    /// 
    /// <para><strong>Sample Request:</strong></para>
    /// <code>
    /// GET /api/v1/users/12345?include=profile,roles
    /// Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
    /// </code>
    /// </remarks>
    /// <response code="200">User retrieved successfully</response>
    /// <response code="400">Invalid user ID format or parameters</response>
    /// <response code="401">Authentication required</response>
    /// <response code="403">Insufficient permissions to access this user</response>
    /// <response code="404">User not found</response>
    /// <response code="429">Rate limit exceeded</response>
    [HttpGet("{id:long}")]
    [SwaggerOperation(
        Summary = "Get user by ID",
        Description = "Retrieves detailed user information by unique identifier with optional related data inclusion",
        OperationId = "GetUserById",
        Tags = new[] { "Users" }
    )]
    [SwaggerResponse(200, "User retrieved successfully", typeof(UserDetailResponse))]
    [SwaggerResponse(400, "Invalid request parameters", typeof(ErrorResponse))]
    [SwaggerResponse(401, "Authentication required", typeof(ErrorResponse))]
    [SwaggerResponse(403, "Insufficient permissions", typeof(ErrorResponse))]
    [SwaggerResponse(404, "User not found", typeof(ErrorResponse))]
    [SwaggerResponse(429, "Rate limit exceeded", typeof(ErrorResponse))]
    public async Task<ActionResult<UserDetailResponse>> GetUserById(
        [FromRoute, SwaggerParameter("Unique user identifier", Required = true)] long id,
        [FromQuery, SwaggerParameter("Comma-separated list of related data to include")] string[] include = null)
    {
        var user = await _userService.GetUserByIdAsync(id, include);
        return Ok(user);
    }
}
```

**Node.js + NestJS Implementation:**
```typescript
// Enhanced Main Application Setup
async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  
  // Enhanced Swagger configuration
  const config = new DocumentBuilder()
    .setTitle('Company API')
    .setDescription(`
      Comprehensive API documentation generated from NestJS application.
      
      ## Overview
      This API provides a complete set of endpoints for managing users, orders, and related business entities.
      Built with NestJS framework following enterprise-grade patterns and best practices.
      
      ## Authentication
      The API supports multiple authentication methods:
      - **JWT Bearer Tokens**: For user authentication and session management
      - **API Keys**: For service-to-service communication
      - **OAuth 2.0**: For third-party integrations (coming soon)
      
      ## Rate Limiting
      To ensure fair usage and prevent abuse, the following rate limits apply:
      - **Authenticated users**: 1000 requests per hour
      - **Anonymous users**: 100 requests per hour
      - **Admin users**: 5000 requests per hour
      
      ## Error Handling
      All errors follow RFC 7807 Problem Details standard with consistent structure:
      - **error**: Machine-readable error code
      - **message**: Human-readable error description
      - **details**: Additional context when available
      - **timestamp**: ISO 8601 timestamp of the error
      - **requestId**: Unique identifier for request tracing
      
      ## Versioning
      API versioning is handled through URL path (/api/v1/, /api/v2/, etc.).
      Deprecated versions will be supported for 12 months after replacement.
    `)
    .setVersion('1.0.0')
    .setContact('API Support Team', 'https://company.com/support', 'api-support@company.com')
    .setLicense('MIT License', 'https://opensource.org/licenses/MIT')
    .addServer('https://api.company.com/v1', 'Production server')
    .addServer('https://staging-api.company.com/v1', 'Staging server')
    .addServer('http://localhost:3000/v1', 'Development server')
    .addBearerAuth(
      {
        type: 'http',
        scheme: 'bearer',
        bearerFormat: 'JWT',
        name: 'JWT',
        description: 'Enter JWT token for user authentication',
        in: 'header',
      },
      'JWT-auth'
    )
    .addApiKey(
      {
        type: 'apiKey',
        name: 'X-API-Key',
        in: 'header',
        description: 'API Key for service-to-service authentication',
      },
      'api-key'
    )
    .addTag('Users', 'User management and profile operations')
    .addTag('Authentication', 'Authentication and session management')
    .addTag('Orders', 'Order processing and management')
    .build();
    
  const document = SwaggerModule.createDocument(app, config, {
    operationIdFactory: (controllerKey: string, methodKey: string) => methodKey,
    deepScanRoutes: true,
  });
  
  // Add custom schema examples
  document.components.examples = {
    UserResponse: {
      summary: 'Standard user response',
      value: {
        id: 12345,
        username: 'john.doe',
        email: 'john.doe@example.com',
        profile: {
          firstName: 'John',
          lastName: 'Doe',
          avatar: 'https://cdn.example.com/avatars/12345.jpg'
        },
        roles: ['user'],
        createdAt: '2024-01-15T10:30:00Z',
        isActive: true
      }
    },
    ValidationError: {
      summary: 'Validation error response',
      value: {
        error: 'VALIDATION_ERROR',
        message: 'Request validation failed',
        details: [
          {
            field: 'email',
            message: 'Must be a valid email address',
            code: 'INVALID_FORMAT'
          }
        ],
        timestamp: '2024-03-20T14:45:30Z',
        requestId: 'req_abc123'
      }
    }
  };
  
  SwaggerModule.setup('swagger', app, document, {
    swaggerOptions: {
      persistAuthorization: true,
      displayRequestDuration: true,
      docExpansion: 'none',
      operationsSorter: 'method',
      tagsSorter: 'alpha',
      tryItOutEnabled: true,
      filter: true,
      deepLinking: true,
    },
    customSiteTitle: 'Company API Documentation',
    customfavIcon: '/favicon.ico',
    customCss: `
      .swagger-ui .topbar { display: none; }
      .swagger-ui .info .title { color: #1f2937; }
    `,
  });
  
  await app.listen(3000);
}
```

**Python + FastAPI Implementation:**
```python
# Enhanced FastAPI Application with Comprehensive Documentation
from fastapi import FastAPI, HTTPException, Depends, Query, Path, Body, status
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials
from fastapi.middleware.cors import CORSMiddleware
from fastapi.responses import RedirectResponse
from pydantic import BaseModel, Field, EmailStr, validator
from typing import Optional, List, Union, Dict, Any
from datetime import datetime
from enum import Enum
import uvicorn

# Enhanced FastAPI initialization with comprehensive metadata
app = FastAPI(
    title="Company API",
    description="""
    Comprehensive API documentation generated from FastAPI application.
    
    ## Features
    
    This API provides a robust set of endpoints for:
    - **User Management**: Registration, authentication, profile management
    - **Order Processing**: Create, track, and manage orders
    - **Product Catalog**: Browse and search products
    - **Administrative Functions**: User management, analytics, reporting
    
    ## Authentication
    
    The API supports multiple authentication methods:
    
    ### JWT Bearer Tokens
    Include the token in the Authorization header:
    ```
    Authorization: Bearer <your_jwt_token>
    ```
    
    ### API Keys
    For service-to-service communication, include your API key:
    ```
    X-API-Key: <your_api_key>
    ```
    
    ## Rate Limiting
    
    API requests are rate-limited to ensure fair usage:
    - **Free tier**: 100 requests per hour
    - **Premium users**: 1,000 requests per hour
    - **Enterprise**: 10,000 requests per hour
    
    ## Error Handling
    
    All API errors follow a consistent format:
    - **4xx errors**: Client errors (invalid input, authentication issues)
    - **5xx errors**: Server errors (temporary issues, maintenance)
    
    Each error response includes:
    - Human-readable error message
    - Machine-readable error code
    - Additional context when available
    - Unique request identifier for support
    
    ## Data Formats
    
    - **Timestamps**: ISO 8601 format (e.g., "2024-03-20T14:45:30Z")
    - **Currencies**: ISO 4217 currency codes (e.g., "USD", "EUR")
    - **Countries**: ISO 3166-1 alpha-2 country codes (e.g., "US", "GB")
    
    ## Support
    
    For API support, please contact:
    - **Email**: api-support@company.com
    - **Documentation**: https://docs.company.com/api
    - **Status Page**: https://status.company.com
    """,
    version="1.0.0",
    terms_of_service="https://company.com/terms",
    contact={
        "name": "API Support Team",
        "url": "https://company.com/support",
        "email": "api-support@company.com",
    },
    license_info={
        "name": "MIT License",
        "url": "https://opensource.org/licenses/MIT",
    },
    servers=[
        {"url": "https://api.company.com/v1", "description": "Production server"},
        {"url": "https://staging-api.company.com/v1", "description": "Staging server"},
        {"url": "http://localhost:8000/v1", "description": "Development server"},
    ],
    openapi_tags=[
        {
            "name": "users",
            "description": "User management and profile operations",
            "externalDocs": {
                "description": "User Management Guide",
                "url": "https://docs.company.com/users",
            },
        },
        {
            "name": "authentication",
            "description": "Authentication and session management",
            "externalDocs": {
                "description": "Authentication Guide",
                "url": "https://docs.company.com/auth",
            },
        },
        {
            "name": "orders",
            "description": "Order processing and management",
        },
    ],
    docs_url="/swagger",
    redoc_url="/redoc",
    openapi_url="/api/v1/openapi.json",
)

# Enhanced Pydantic models with comprehensive documentation
class UserDetailResponse(BaseModel):
    """
    Complete user information with related data.
    
    This model represents a comprehensive user profile including
    personal information, account status, and related metadata.
    """
    
    id: int = Field(
        ...,
        title="User ID",
        description="Unique user identifier assigned at registration",
        example=12345,
        ge=1
    )
    username: str = Field(
        ...,
        title="Username",
        description="Unique username for authentication (3-30 characters, alphanumeric plus underscore and dash)",
        example="john.doe",
        min_length=3,
        max_length=30,
        regex=r"^[a-zA-Z0-9_-]{3,30}$"
    )
    email: EmailStr = Field(
        ...,
        title="Email Address",
        description="User's primary email address (used for notifications and account recovery)",
        example="john.doe@example.com"
    )
    profile: Optional[UserProfile] = Field(
        None,
        title="User Profile",
        description="Detailed profile information including name, avatar, and bio"
    )
    roles: List[UserRole] = Field(
        ...,
        title="User Roles",
        description="List of roles assigned to the user determining access permissions",
        example=["user"]
    )
    created_at: datetime = Field(
        ...,
        title="Creation Date",
        description="Account creation timestamp in ISO 8601 format",
        example="2024-01-15T10:30:00Z"
    )
    updated_at: Optional[datetime] = Field(
        None,
        title="Last Update",
        description="Last profile update timestamp in ISO 8601 format",
        example="2024-03-20T14:45:30Z"
    )
    is_active: bool = Field(
        True,
        title="Account Status",
        description="Whether the account is active and can access the system",
        example=True
    )
    last_login_at: Optional[datetime] = Field(
        None,
        title="Last Login",
        description="Timestamp of the user's last successful login",
        example="2024-03-20T09:15:00Z"
    )
    
    class Config:
        schema_extra = {
            "examples": {
                "standard_user": {
                    "summary": "Standard User",
                    "description": "Example of a standard user account with basic permissions",
                    "value": {
                        "id": 12345,
                        "username": "john.doe",
                        "email": "john.doe@example.com",
                        "profile": {
                            "first_name": "John",
                            "last_name": "Doe",
                            "avatar": "https://cdn.example.com/avatars/12345.jpg",
                            "bio": "Software developer passionate about clean code"
                        },
                        "roles": ["user"],
                        "created_at": "2024-01-15T10:30:00Z",
                        "updated_at": "2024-03-20T14:45:30Z",
                        "is_active": True,
                        "last_login_at": "2024-03-20T09:15:00Z"
                    }
                },
                "admin_user": {
                    "summary": "Admin User",
                    "description": "Example of an administrative user with elevated permissions",
                    "value": {
                        "id": 67890,
                        "username": "admin",
                        "email": "admin@company.com",
                        "profile": {
                            "first_name": "System",
                            "last_name": "Administrator"
                        },
                        "roles": ["admin", "user"],
                        "created_at": "2023-12-01T08:00:00Z",
                        "is_active": True,
                        "last_login_at": "2024-03-20T08:30:00Z"
                    }
                }
            }
        }

# Enhanced endpoint with comprehensive documentation
@app.get(
    "/api/v1/users/{user_id}",
    response_model=UserDetailResponse,
    status_code=status.HTTP_200_OK,
    tags=["users"],
    summary="Get user by ID",
    description="""
    Retrieves detailed user information by unique identifier.
    
    ## Business Logic
    
    This endpoint performs the following operations:
    1. **Validates user ID**: Ensures the provided ID is valid and within acceptable range
    2. **Checks permissions**: Verifies the requesting user has permission to access the target user's data
    3. **Applies visibility rules**: Filters sensitive information based on the relationship between users
    4. **Fetches related data**: Optionally includes additional user information based on the include parameter
    5. **Caches response**: Stores the response for improved performance on subsequent requests
    
    ## Access Control
    
    - **Own profile**: Users can always access their own profile information
    - **Other users**: Requires 'user:read' permission or higher
    - **Admin data**: Administrative metadata only visible to users with 'admin:read' permission
    
    ## Performance Notes
    
    - Response is cached for 5 minutes for non-admin users
    - Including related data may trigger additional database queries
    - Rate limiting applies based on user role and authentication status
    
    ## Examples
    
    ### Basic Request
    ```bash
    curl -X GET "https://api.company.com/v1/users/12345" \\
         -H "Authorization: Bearer YOUR_JWT_TOKEN"
    ```
    
    ### Request with Related Data
    ```bash
    curl -X GET "https://api.company.com/v1/users/12345?include=profile,roles" \\
         -H "Authorization: Bearer YOUR_JWT_TOKEN"
    ```
    """,
    responses={
        200: {
            "description": "User retrieved successfully",
            "content": {
                "application/json": {
                    "examples": {
                        "standard_user": {
                            "summary": "Standard user response",
                            "value": {
                                "id": 12345,
                                "username": "john.doe",
                                "email": "john.doe@example.com",
                                "profile": {
                                    "first_name": "John",
                                    "last_name": "Doe",
                                    "avatar": "https://cdn.example.com/avatars/12345.jpg"
                                },
                                "roles": ["user"],
                                "created_at": "2024-01-15T10:30:00Z",
                                "is_active": True
                            }
                        }
                    }
                }
            }
        },
        400: {
            "description": "Invalid user ID format or parameters",
            "content": {
                "application/json": {
                    "example": {
                        "error": "VALIDATION_ERROR",
                        "message": "Invalid user ID format",
                        "details": [
                            {
                                "field": "user_id",
                                "message": "User ID must be a positive integer",
                                "code": "INVALID_FORMAT"
                            }
                        ],
                        "timestamp": "2024-03-20T14:45:30Z",
                        "request_id": "req_abc123"
                    }
                }
            }
        },
        401: {"description": "Authentication required"},
        403: {"description": "Insufficient permissions to access this user"},
        404: {"description": "User not found"},
        429: {"description": "Rate limit exceeded"}
    }
)
async def get_user_by_id(
    user_id: int = Path(
        ...,
        title="User ID",
        description="Unique identifier for the user to retrieve",
        example=12345,
        ge=1,
        le=2147483647
    ),
    include: Optional[List[str]] = Query(
        None,
        title="Include Related Data",
        description="Comma-separated list of related data to include in the response",
        example=["profile", "roles"],
        regex=r"^(profile|roles|preferences|admin_metadata)$"
    ),
    credentials: HTTPAuthorizationCredentials = Depends(security)
):
    """
    Get user by ID endpoint implementation.
    
    This endpoint retrieves comprehensive user information with optional
    related data inclusion based on the requesting user's permissions.
    """
    # Implementation logic here
    pass
```

## Quality Gates

### ✅ Documentation Completeness
- [ ] All endpoints documented with examples
- [ ] All models and DTOs documented with field descriptions
- [ ] Authentication methods clearly explained
- [ ] Error responses documented with examples
- [ ] Business logic explained in endpoint descriptions

### ✅ Technical Accuracy
- [ ] API documentation matches actual implementation
- [ ] Request/response models are accurate and complete
- [ ] Status codes match implementation behavior
- [ ] Authentication requirements correctly specified
- [ ] Rate limiting information accurate

### ✅ Developer Experience
- [ ] Interactive documentation (Swagger UI) functional
- [ ] "Try it out" feature works for all endpoints
- [ ] Examples are realistic and helpful
- [ ] Documentation is searchable and well-organized
- [ ] External links and references are valid

### ✅ Maintenance Integration
- [ ] Documentation generation integrated with CI/CD pipeline
- [ ] Automated validation of documentation accuracy
- [ ] Version control for API documentation changes
- [ ] Deprecation notices included where applicable

## Transition to Specialized Chatmodes

After completing Swagger documentation generation:

- **For API Implementation**: Switch to **@api-engineer** chatmode to implement endpoints that match the generated documentation
- **For Frontend Integration**: Switch to **@frontend-engineer** chatmode to generate client SDK and integration code based on the documentation
- **For Testing Strategy**: Switch to **@qa-engineer** chatmode to create comprehensive API testing suites using the documentation as specification
- **For Security Review**: Switch to **@security-engineer** chatmode to review and enhance API security based on documented endpoints and data flows

// Model with comprehensive documentation
/// <summary>
/// Complete user information with related data
/// </summary>
/// <example>
/// {
///   "id": 12345,
///   "username": "john.doe",
///   "email": "john.doe@example.com",
///   "profile": {
///     "firstName": "John",
///     "lastName": "Doe"
///   },
///   "roles": ["user"],
///   "createdAt": "2024-01-15T10:30:00Z",
///   "isActive": true
/// }
/// </example>
[SwaggerSchema("Complete user information with related data")]
public class UserDetailResponse
{
    /// <summary>
    /// Unique user identifier
    /// </summary>
    /// <example>12345</example>
    [SwaggerSchema("Unique user identifier", Format = "int64")]
    [Required]
    public long Id { get; set; }
    
    /// <summary>
    /// Unique username for authentication
    /// </summary>
    /// <example>john.doe</example>
    [SwaggerSchema("Unique username for authentication", Pattern = "^[a-zA-Z0-9_-]{3,30}$")]
    [Required]
    [StringLength(30, MinimumLength = 3)]
    public string Username { get; set; }
    
    /// <summary>
    /// User's primary email address
    /// </summary>
    /// <example>john.doe@example.com</example>
    [SwaggerSchema("User's primary email address", Format = "email")]
    [Required]
    [EmailAddress]
    public string Email { get; set; }
    
    /// <summary>
    /// User's profile information
    /// </summary>
    [SwaggerSchema("User's profile information")]
    public UserProfile Profile { get; set; }
    
    /// <summary>
    /// User's assigned roles
    /// </summary>
    /// <example>["user"]</example>
    [SwaggerSchema("User's assigned roles")]
    public List<string> Roles { get; set; } = new List<string>();
    
    /// <summary>
    /// Account creation timestamp
    /// </summary>
    /// <example>2024-01-15T10:30:00Z</example>
    [SwaggerSchema("Account creation timestamp", Format = "date-time")]
    [Required]
    public DateTime CreatedAt { get; set; }
    
    /// <summary>
    /// Last profile update timestamp
    /// </summary>
    /// <example>2024-03-20T14:45:30Z</example>
    [SwaggerSchema("Last profile update timestamp", Format = "date-time")]
    public DateTime? UpdatedAt { get; set; }
    
    /// <summary>
    /// Account status
    /// </summary>
    /// <example>true</example>
    [SwaggerSchema("Account status", Default = true)]
    [Required]
    public bool IsActive { get; set; } = true;
}

// Project file configuration for XML documentation
/*
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <GenerateDocumentationFile>true</GenerateDocumentationFile>
    <NoWarn>$(NoWarn);1591</NoWarn>
  </PropertyGroup>
</Project>
*/
```

### Node.js + NestJS + Swagger

**Recommended Pattern:** @nestjs/swagger with decorators and DTOs

```typescript
// Package Dependencies
/*
npm install @nestjs/swagger swagger-ui-express
*/

// Main Application Setup
import { NestFactory } from '@nestjs/core';
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';
import { ValidationPipe } from '@nestjs/common';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  
  // Global validation pipe
  app.useGlobalPipes(new ValidationPipe({
    transform: true,
    whitelist: true,
    forbidNonWhitelisted: true,
  }));
  
  // Swagger configuration
  const config = new DocumentBuilder()
    .setTitle('Company API')
    .setDescription('Comprehensive API documentation generated from NestJS code')
    .setVersion('1.0')
    .setContact('API Support Team', 'https://company.com/support', 'api-support@company.com')
    .setLicense('MIT License', 'https://opensource.org/licenses/MIT')
    .addServer('https://api.company.com/v1', 'Production server')
    .addServer('https://staging-api.company.com/v1', 'Staging server')
    .addServer('http://localhost:3000/v1', 'Development server')
    .addBearerAuth(
      {
        type: 'http',
        scheme: 'bearer',
        bearerFormat: 'JWT',
        name: 'JWT',
        description: 'Enter JWT token',
        in: 'header',
      },
      'JWT-auth'
    )
    .addApiKey(
      {
        type: 'apiKey',
        name: 'X-API-Key',
        in: 'header',
        description: 'API Key for service-to-service authentication',
      },
      'api-key'
    )
    .addTag('Users', 'User management operations')
    .addTag('Authentication', 'Authentication and authorization endpoints')
    .build();
    
  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('swagger', app, document, {
    swaggerOptions: {
      persistAuthorization: true,
      displayRequestDuration: true,
      docExpansion: 'none',
      operationsSorter: 'method',
      tagsSorter: 'alpha',
      tryItOutEnabled: true,
    },
    customSiteTitle: 'Company API Documentation',
  });
  
  await app.listen(3000);
}
bootstrap();

// DTOs with comprehensive documentation
import { ApiProperty, ApiPropertyOptional } from '@nestjs/swagger';
import { IsEmail, IsString, IsOptional, Length, IsArray, IsBoolean, IsDateString } from 'class-validator';
import { Transform } from 'class-transformer';

export class CreateUserRequest {
  @ApiProperty({
    description: 'Unique username for authentication',
    example: 'jane.smith',
    minLength: 3,
    maxLength: 30,
    pattern: '^[a-zA-Z0-9_-]{3,30}$',
  })
  @IsString()
  @Length(3, 30)
  username: string;
  
  @ApiProperty({
    description: "User's primary email address",
    example: 'jane.smith@example.com',
    format: 'email',
  })
  @IsEmail()
  email: string;
  
  @ApiProperty({
    description: 'Account password - must meet complexity requirements',
    example: 'SecurePass123!',
    minLength: 8,
    maxLength: 128,
    writeOnly: true,
  })
  @IsString()
  @Length(8, 128)
  password: string;
  
  @ApiPropertyOptional({
    description: "User's profile information",
    type: () => UserProfileRequest,
  })
  @IsOptional()
  profile?: UserProfileRequest;
  
  @ApiPropertyOptional({
    description: "User's initial roles",
    example: ['user'],
    enum: ['user', 'admin', 'moderator', 'guest'],
    isArray: true,
  })
  @IsOptional()
  @IsArray()
  @IsString({ each: true })
  roles?: string[];
}

export class UserDetailResponse {
  @ApiProperty({
    description: 'Unique user identifier',
    example: 12345,
    type: 'integer',
    format: 'int64',
    minimum: 1,
  })
  id: number;
  
  @ApiProperty({
    description: 'Unique username for authentication',
    example: 'john.doe',
    minLength: 3,
    maxLength: 30,
    pattern: '^[a-zA-Z0-9_-]{3,30}$',
  })
  username: string;
  
  @ApiProperty({
    description: "User's primary email address",
    example: 'john.doe@example.com',
    format: 'email',
  })
  email: string;
  
  @ApiPropertyOptional({
    description: "User's profile information",
    type: () => UserProfile,
  })
  profile?: UserProfile;
  
  @ApiProperty({
    description: "User's assigned roles",
    example: ['user'],
    enum: ['user', 'admin', 'moderator', 'guest'],
    isArray: true,
  })
  roles: string[];
  
  @ApiProperty({
    description: 'Account creation timestamp',
    example: '2024-01-15T10:30:00Z',
    format: 'date-time',
  })
  createdAt: string;
  
  @ApiPropertyOptional({
    description: 'Last profile update timestamp',
    example: '2024-03-20T14:45:30Z',
    format: 'date-time',
  })
  updatedAt?: string;
  
  @ApiProperty({
    description: 'Account status',
    example: true,
    default: true,
  })
  isActive: boolean;
}

// Controller with comprehensive documentation
@ApiTags('Users')
@ApiBearerAuth('JWT-auth')
@Controller('api/users')
@UseGuards(JwtAuthGuard)
export class UsersController {
  constructor(private readonly usersService: UsersService) {}
  
  @Get(':id')
  @ApiOperation({
    summary: 'Get user by ID',
    description: `
      Retrieves detailed user information by unique identifier.
      Requires appropriate permissions to access user data.
      
      **Business Logic:**
      - Validates user ID format
      - Checks user existence
      - Applies user visibility rules
      - Returns user with related data
      
      **Permissions Required:**
      - User.Read or Admin.Users.Read
    `,
    operationId: 'getUserById',
  })
  @ApiParam({
    name: 'id',
    description: 'Unique user identifier',
    example: 12345,
    type: 'integer',
    format: 'int64',
  })
  @ApiQuery({
    name: 'include',
    description: 'Related data to include in response',
    required: false,
    example: ['profile', 'roles'],
    enum: ['profile', 'preferences', 'roles'],
    isArray: true,
    explode: false,
  })
  @ApiResponse({
    status: 200,
    description: 'User retrieved successfully',
    type: UserDetailResponse,
    examples: {
      'Standard User': {
        summary: 'Example of standard user response',
        value: {
          id: 12345,
          username: 'john.doe',
          email: 'john.doe@example.com',
          profile: {
            firstName: 'John',
            lastName: 'Doe',
          },
          roles: ['user'],
          createdAt: '2024-01-15T10:30:00Z',
          isActive: true,
        },
      },
      'Admin User': {
        summary: 'Example of admin user response',
        value: {
          id: 67890,
          username: 'admin',
          email: 'admin@company.com',
          profile: {
            firstName: 'System',
            lastName: 'Administrator',
          },
          roles: ['admin', 'user'],
          createdAt: '2023-12-01T08:00:00Z',
          isActive: true,
        },
      },
    },
  })
  @ApiResponse({
    status: 400,
    description: 'Invalid user ID format',
    type: ErrorResponse,
  })
  @ApiResponse({
    status: 401,
    description: 'Authentication required',
    type: ErrorResponse,
  })
  @ApiResponse({
    status: 403,
    description: 'Insufficient permissions',
    type: ErrorResponse,
  })
  @ApiResponse({
    status: 404,
    description: 'User not found',
    type: ErrorResponse,
  })
  async getUserById(
    @Param('id', ParseIntPipe) id: number,
    @Query('include') include?: string[],
  ): Promise<UserDetailResponse> {
    return this.usersService.findById(id, include);
  }
  
  @Post()
  @ApiOperation({
    summary: 'Create new user',
    description: `
      Creates a new user account with the provided information.
      Email must be unique and password must meet complexity requirements.
      
      **Business Rules:**
      - Username must be unique
      - Email must be unique and valid format
      - Password must meet complexity requirements
      - Email verification will be required
    `,
    operationId: 'createUser',
  })
  @ApiBody({
    description: 'User creation data',
    type: CreateUserRequest,
    examples: {
      'Standard User Creation': {
        summary: 'Create a standard user account',
        value: {
          username: 'jane.smith',
          email: 'jane.smith@example.com',
          password: 'SecurePass123!',
          profile: {
            firstName: 'Jane',
            lastName: 'Smith',
            bio: 'Product manager with 5 years experience',
          },
        },
      },
    },
  })
  @ApiResponse({
    status: 201,
    description: 'User created successfully',
    type: UserDetailResponse,
  })
  @ApiResponse({
    status: 400,
    description: 'Validation errors in request data',
    type: ValidationErrorResponse,
  })
  @ApiResponse({
    status: 409,
    description: 'User with email already exists',
    type: ErrorResponse,
  })
  async createUser(
    @Body() createUserDto: CreateUserRequest,
  ): Promise<UserDetailResponse> {
    return this.usersService.create(createUserDto);
  }
}

// Error Response Models
export class ErrorResponse {
  @ApiProperty({
    description: 'Error code for programmatic handling',
    example: 'VALIDATION_ERROR',
    enum: [
      'VALIDATION_ERROR',
      'UNAUTHORIZED', 
      'FORBIDDEN',
      'NOT_FOUND',
      'CONFLICT',
      'RATE_LIMIT_EXCEEDED',
      'INTERNAL_ERROR'
    ],
  })
  error: string;
  
  @ApiProperty({
    description: 'Human-readable error message',
    example: 'Request validation failed',
  })
  message: string;
  
  @ApiPropertyOptional({
    description: 'Additional error details (validation errors, etc.)',
    oneOf: [
      { type: 'array', items: { $ref: '#/components/schemas/ValidationError' } },
      { type: 'null' }
    ],
  })
  details?: any;
  
  @ApiProperty({
    description: 'Error occurrence timestamp',
    example: '2024-03-20T14:45:30Z',
    format: 'date-time',
  })
  timestamp: string;
  
  @ApiProperty({
    description: 'Unique request identifier for debugging',
    example: 'req_12345',
  })
  requestId: string;
}
```

### Python + FastAPI + Automatic Documentation

**Recommended Pattern:** FastAPI built-in OpenAPI with Pydantic models

```python
# FastAPI with comprehensive documentation
from fastapi import FastAPI, HTTPException, Depends, Query, Path, Body, status
from fastapi.security import HTTPBearer, HTTPAuthorizationCredentials
from pydantic import BaseModel, Field, EmailStr, validator
from typing import Optional, List, Union
from datetime import datetime
from enum import Enum
import uvicorn

# Initialize FastAPI with comprehensive metadata
app = FastAPI(
    title="Company API",
    description="""
    Comprehensive API documentation generated from FastAPI code.
    
    ## Authentication
    
    This API uses JWT Bearer token authentication. Include the token in the Authorization header:
    ```
    Authorization: Bearer <your_jwt_token>
    ```
    
    ## Error Handling
    
    All errors follow a standardized format with appropriate HTTP status codes.
    Validation errors include detailed field-level information.
    
    ## Rate Limiting
    
    API requests are rate-limited to prevent abuse. Current limits:
    - 100 requests per minute for authenticated users
    - 20 requests per minute for unauthenticated requests
    """,
    version="1.0.0",
    contact={
        "name": "API Support Team",
        "url": "https://company.com/support",
        "email": "api-support@company.com",
    },
    license_info={
        "name": "MIT License",
        "url": "https://opensource.org/licenses/MIT",
    },
    servers=[
        {"url": "https://api.company.com/v1", "description": "Production server"},
        {"url": "https://staging-api.company.com/v1", "description": "Staging server"},
        {"url": "http://localhost:8000/v1", "description": "Development server"},
    ],
    openapi_tags=[
        {
            "name": "users",
            "description": "User management operations",
            "externalDocs": {
                "description": "User Management Guide",
                "url": "https://docs.company.com/users",
            },
        },
        {
            "name": "authentication",
            "description": "Authentication and authorization endpoints",
        },
    ],
)

# Security scheme
security = HTTPBearer()

# Pydantic models with comprehensive documentation
class UserRole(str, Enum):
    """Available user roles in the system"""
    USER = "user"
    ADMIN = "admin"
    MODERATOR = "moderator"
    GUEST = "guest"

class UserProfile(BaseModel):
    """User profile information"""
    first_name: Optional[str] = Field(
        None,
        title="First Name",
        description="User's first name",
        example="John",
        max_length=50
    )
    last_name: Optional[str] = Field(
        None,
        title="Last Name", 
        description="User's last name",
        example="Doe",
        max_length=50
    )
    avatar: Optional[str] = Field(
        None,
        title="Avatar URL",
        description="URL to user's profile picture",
        example="https://cdn.example.com/avatars/12345.jpg",
        regex=r"^https?://.*\.(jpg|jpeg|png|gif)$"
    )
    bio: Optional[str] = Field(
        None,
        title="Biography",
        description="User's biography",
        example="Software developer passionate about clean code",
        max_length=500
    )
    location: Optional[str] = Field(
        None,
        title="Location",
        description="User's location",
        example="New York, NY",
        max_length=100
    )
    
    class Config:
        schema_extra = {
            "example": {
                "first_name": "John",
                "last_name": "Doe",
                "avatar": "https://cdn.example.com/avatars/12345.jpg",
                "bio": "Software developer passionate about clean code",
                "location": "New York, NY"
            }
        }

class CreateUserRequest(BaseModel):
    """Request model for creating a new user"""
    username: str = Field(
        ...,
        title="Username",
        description="Unique username for authentication",
        example="jane.smith",
        min_length=3,
        max_length=30,
        regex=r"^[a-zA-Z0-9_-]{3,30}$"
    )
    email: EmailStr = Field(
        ...,
        title="Email Address",
        description="User's primary email address",
        example="jane.smith@example.com"
    )
    password: str = Field(
        ...,
        title="Password",
        description="Account password - must meet complexity requirements",
        example="SecurePass123!",
        min_length=8,
        max_length=128
    )
    profile: Optional[UserProfile] = Field(
        None,
        title="Profile Information",
        description="User's profile information"
    )
    roles: Optional[List[UserRole]] = Field(
        [UserRole.USER],
        title="User Roles",
        description="User's initial roles",
        example=["user"]
    )
    
    @validator('password')
    def validate_password_complexity(cls, v):
        """Validate password meets complexity requirements"""
        if not any(c.isupper() for c in v):
            raise ValueError('Password must contain at least one uppercase letter')
        if not any(c.islower() for c in v):
            raise ValueError('Password must contain at least one lowercase letter')
        if not any(c.isdigit() for c in v):
            raise ValueError('Password must contain at least one digit')
        if not any(c in '!@#$%^&*()_+-=[]{}|;:,.<>?' for c in v):
            raise ValueError('Password must contain at least one special character')
        return v
    
    class Config:
        schema_extra = {
            "example": {
                "username": "jane.smith",
                "email": "jane.smith@example.com",
                "password": "SecurePass123!",
                "profile": {
                    "first_name": "Jane",
                    "last_name": "Smith",
                    "bio": "Product manager with 5 years experience"
                },
                "roles": ["user"]
            }
        }

class UserDetailResponse(BaseModel):
    """Complete user information with related data"""
    id: int = Field(
        ...,
        title="User ID",
        description="Unique user identifier",
        example=12345,
        ge=1
    )
    username: str = Field(
        ...,
        title="Username",
        description="Unique username for authentication",
        example="john.doe"
    )
    email: EmailStr = Field(
        ...,
        title="Email Address",
        description="User's primary email address",
        example="john.doe@example.com"
    )
    profile: Optional[UserProfile] = Field(
        None,
        title="Profile Information",
        description="User's profile information"
    )
    roles: List[UserRole] = Field(
        ...,
        title="User Roles",
        description="User's assigned roles",
        example=["user"]
    )
    created_at: datetime = Field(
        ...,
        title="Creation Date",
        description="Account creation timestamp",
        example="2024-01-15T10:30:00Z"
    )
    updated_at: Optional[datetime] = Field(
        None,
        title="Update Date", 
        description="Last profile update timestamp",
        example="2024-03-20T14:45:30Z"
    )
    is_active: bool = Field(
        True,
        title="Account Status",
        description="Account status",
        example=True
    )
    
    class Config:
        schema_extra = {
            "examples": {
                "Standard User": {
                    "summary": "Example of standard user response",
                    "value": {
                        "id": 12345,
                        "username": "john.doe",
                        "email": "john.doe@example.com",
                        "profile": {
                            "first_name": "John",
                            "last_name": "Doe"
                        },
                        "roles": ["user"],
                        "created_at": "2024-01-15T10:30:00Z",
                        "is_active": True
                    }
                },
                "Admin User": {
                    "summary": "Example of admin user response",
                    "value": {
                        "id": 67890,
                        "username": "admin",
                        "email": "admin@company.com",
                        "profile": {
                            "first_name": "System",
                            "last_name": "Administrator"
                        },
                        "roles": ["admin", "user"],
                        "created_at": "2023-12-01T08:00:00Z",
                        "is_active": True
                    }
                }
            }
        }

# Error Response Models
class ValidationError(BaseModel):
    """Individual validation error details"""
    field: str = Field(..., description="Field name that failed validation", example="email")
    message: str = Field(..., description="Validation error message", example="Must be a valid email address")
    code: str = Field(..., description="Validation error code", example="INVALID_FORMAT")

class ErrorResponse(BaseModel):
    """Standardized error response format"""
    error: str = Field(
        ...,
        description="Error code for programmatic handling",
        example="VALIDATION_ERROR"
    )
    message: str = Field(
        ...,
        description="Human-readable error message",
        example="Request validation failed"
    )
    details: Optional[Union[List[ValidationError], None]] = Field(
        None,
        description="Additional error details (validation errors, etc.)"
    )
    timestamp: datetime = Field(
        ...,
        description="Error occurrence timestamp",
        example="2024-03-20T14:45:30Z"
    )
    request_id: str = Field(
        ...,
        description="Unique request identifier for debugging",
        example="req_12345"
    )

# API Endpoints with comprehensive documentation
@app.get(
    "/api/users/{user_id}",
    response_model=UserDetailResponse,
    status_code=status.HTTP_200_OK,
    tags=["users"],
    summary="Get user by ID",
    description="""
    Retrieves detailed user information by unique identifier.
    Requires appropriate permissions to access user data.
    
    **Business Logic:**
    - Validates user ID format
    - Checks user existence
    - Applies user visibility rules
    - Returns user with related data
    
    **Permissions Required:**
    - User.Read or Admin.Users.Read
    """,
    responses={
        200: {
            "description": "User retrieved successfully",
            "content": {
                "application/json": {
                    "examples": {
                        "Standard User": {
                            "summary": "Example of standard user response",
                            "value": {
                                "id": 12345,
                                "username": "john.doe",
                                "email": "john.doe@example.com",
                                "profile": {"first_name": "John", "last_name": "Doe"},
                                "roles": ["user"],
                                "created_at": "2024-01-15T10:30:00Z",
                                "is_active": True
                            }
                        }
                    }
                }
            }
        },
        400: {"model": ErrorResponse, "description": "Invalid user ID format"},
        401: {"model": ErrorResponse, "description": "Authentication required"},
        403: {"model": ErrorResponse, "description": "Insufficient permissions"},
        404: {"model": ErrorResponse, "description": "User not found"},
    }
)
async def get_user_by_id(
    user_id: int = Path(
        ...,
        title="User ID",
        description="Unique user identifier",
        example=12345,
        ge=1
    ),
    include: Optional[List[str]] = Query(
        None,
        title="Include Related Data",
        description="Related data to include in response",
        example=["profile", "roles"],
        regex=r"^(profile|preferences|roles)$"
    ),
    credentials: HTTPAuthorizationCredentials = Depends(security)
):
    """Get user by ID endpoint implementation"""
    # Implementation logic here
    pass

@app.post(
    "/api/users",
    response_model=UserDetailResponse,
    status_code=status.HTTP_201_CREATED,
    tags=["users"],
    summary="Create new user",
    description="""
    Creates a new user account with the provided information.
    Email must be unique and password must meet complexity requirements.
    
    **Business Rules:**
    - Username must be unique
    - Email must be unique and valid format
    - Password must meet complexity requirements
    - Email verification will be required
    """,
    responses={
        201: {"description": "User created successfully"},
        400: {"model": ErrorResponse, "description": "Validation errors in request data"},
        409: {"model": ErrorResponse, "description": "User with email already exists"},
    }
)
async def create_user(
    user_data: CreateUserRequest = Body(
        ...,
        title="User Creation Data",
        description="Complete user information for account creation",
        example={
            "username": "jane.smith",
            "email": "jane.smith@example.com",
            "password": "SecurePass123!",
            "profile": {
                "first_name": "Jane",
                "last_name": "Smith",
                "bio": "Product manager with 5 years experience"
            },
            "roles": ["user"]
        }
    )
):
    """Create user endpoint implementation"""
    # Implementation logic here
    pass

# Custom OpenAPI schema modifications
def custom_openapi():
    if app.openapi_schema:
        return app.openapi_schema
    
    openapi_schema = get_openapi(
        title="Company API",
        version="1.0.0",
        description="Comprehensive API documentation generated from FastAPI code",
        routes=app.routes,
    )
    
    # Add custom security schemes
    openapi_schema["components"]["securitySchemes"] = {
        "bearerAuth": {
            "type": "http",
            "scheme": "bearer",
            "bearerFormat": "JWT",
            "description": "JWT Bearer token authentication"
        }
    }
    
    app.openapi_schema = openapi_schema
    return app.openapi_schema

app.openapi = custom_openapi

if __name__ == "__main__":
    uvicorn.run(
        app,
        host="0.0.0.0",
        port=8000,
        reload=True
    )
```

### Generic/Fallback Implementation

For unsupported technologies, provide generic OpenAPI patterns:

```yaml
# Generic OpenAPI 3.0 Template
openapi: 3.0.3
info:
  title: "API Documentation"
  description: "Generated from existing backend code"
  version: "1.0.0"
  contact:
    name: "API Support"
    email: "support@company.com"
    
servers:
  - url: "https://api.company.com/v1"
    description: "Production server"
  - url: "http://localhost:PORT/v1"
    description: "Development server"
    
security:
  - bearerAuth: []
  
components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
      description: "JWT Bearer token authentication"
      
  schemas:
    ErrorResponse:
      type: object
      required: [error, message, timestamp, requestId]
      properties:
        error:
          type: string
          description: "Error code for programmatic handling"
        message:
          type: string
          description: "Human-readable error message"
        timestamp:
          type: string
          format: date-time
          description: "Error occurrence timestamp"
        requestId:
          type: string
          description: "Unique request identifier"
          
  responses:
    BadRequest:
      description: "Invalid request parameters or body"
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
    Unauthorized:
      description: "Authentication required or invalid"
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
    Forbidden:
      description: "Insufficient permissions"
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
    NotFound:
      description: "Resource not found"
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
            
tags:
  - name: "API"
    description: "API operations"
    
paths: {}
  # Populate with discovered endpoints
```

**This prompt ensures comprehensive Swagger documentation generation that matches the exact backend technology stack specified in copilot.instructions.md while providing production-ready documentation standards.**