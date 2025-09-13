---
description: Generate complete, production-ready API endpoints from Swagger/OpenAPI specifications with proper validation, error handling, and security implementation. Adapts to technology stack defined in copilot.instructions.md.
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

# API Endpoint Generation from Swagger Documentation

Generate complete, production-ready API endpoints from Swagger/OpenAPI specifications, ensuring consistency between documentation and implementation while maintaining best practices for security, validation, and error handling.

## Context Adaptation

**IMPORTANT**: Always read the `copilot.instructions.md` file in the project root directory at the beginning of your work to adapt your implementation to:

- Backend technology stack (Spring Boot, .NET Core, NestJS, FastAPI, Express, etc.)
- Business domain requirements and validation rules
- Security and authentication mechanisms
- Database technology and ORM patterns
- Performance and scalability requirements

## Mission

Generate complete, production-ready API endpoints from Swagger/OpenAPI specifications, ensuring consistency between documentation and implementation while maintaining best practices for security, validation, and error handling through technology-adaptive patterns.

## Implementation Process

### Step 1: Technology Stack Detection and Analysis

**Project Configuration Analysis:**
```bash
# Detect backend technology from project configuration
cat copilot.instructions.md | grep -A 5 "primary_language\|Backend\|Technologies"

# Analyze existing project structure
find . -name "*.csproj" -o -name "*.sln" | head -3  # .NET
find . -name "pom.xml" -o -name "build.gradle" | head -3  # Java
find . -name "package.json" | head -3  # Node.js
find . -name "requirements.txt" -o -name "pyproject.toml" | head -3  # Python
find . -name "go.mod" | head -3  # Go
find . -name "CMakeLists.txt" | head -3  # C++

# Check existing project patterns
ls -la Controllers/ Models/ Services/ src/ api/ routes/ handlers/ 2>/dev/null | head -10
```

**Swagger Specification Analysis:**
```bash
# Validate and analyze Swagger specification
find . -name "*.yml" -o -name "*.yaml" -o -name "*.json" | grep -i -E "swagger|openapi" | head -3

# Extract key information from OpenAPI spec (if tools available)
if command -v yq &> /dev/null; then
    yq eval '.paths | keys' swagger.yml | head -20
    yq eval '.components.schemas | keys' swagger.yml | head -10
    yq eval '.components.securitySchemes' swagger.yml
else
    echo "Manual analysis required - check paths, schemas, and security sections"
fi
```

### Step 2: Technology-Adaptive Implementation

**C# / .NET Core Implementation:**
```csharp
// Generated from Swagger: /api/v1/users/{id}
[ApiController]
[Route("api/v1/[controller]")]
[Produces("application/json")]
[ProducesResponseType(typeof(ErrorResponse), 500)]
public class UsersController : ControllerBase
{
    private readonly IUserService _userService;
    private readonly IMapper _mapper;
    private readonly ILogger<UsersController> _logger;

    public UsersController(
        IUserService userService, 
        IMapper mapper, 
        ILogger<UsersController> logger)
    {
        _userService = userService;
        _mapper = mapper;
        _logger = logger;
    }

    /// <summary>
    /// Get user by ID - Generated from Swagger specification
    /// </summary>
    /// <param name="id">Unique user identifier</param>
    /// <param name="include">Related data to include in response</param>
    /// <returns>User details with requested related data</returns>
    [HttpGet("{id:long}")]
    [Authorize(Policy = "UserRead")]
    [ProducesResponseType(typeof(UserDetailResponse), 200)]
    [ProducesResponseType(typeof(ErrorResponse), 400)]
    [ProducesResponseType(typeof(ErrorResponse), 404)]
    [ProducesResponseType(typeof(ErrorResponse), 403)]
    public async Task<ActionResult<UserDetailResponse>> GetUserById(
        [FromRoute] long id,
        [FromQuery] string[]? include = null)
    {
        try
        {
            // Input validation based on Swagger constraints
            if (id <= 0)
            {
                return BadRequest(CreateErrorResponse("INVALID_ID", "User ID must be a positive integer"));
            }

            // Business logic implementation
            var user = await _userService.GetByIdAsync(id, include);
            if (user == null)
            {
                return NotFound(CreateErrorResponse("USER_NOT_FOUND", $"User with ID {id} not found"));
            }

            // Map to response DTO as defined in Swagger
            var response = _mapper.Map<UserDetailResponse>(user);
            return Ok(response);
        }
        catch (UnauthorizedAccessException)
        {
            return Forbid();
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error retrieving user {UserId}", id);
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    /// <summary>
    /// Create new user - Generated from Swagger specification
    /// </summary>
    /// <param name="request">User creation data</param>
    /// <returns>Created user details</returns>
    [HttpPost]
    [Authorize(Policy = "UserWrite")]
    [ProducesResponseType(typeof(UserDetailResponse), 201)]
    [ProducesResponseType(typeof(ValidationErrorResponse), 400)]
    [ProducesResponseType(typeof(ErrorResponse), 409)]
    public async Task<ActionResult<UserDetailResponse>> CreateUser([FromBody] CreateUserRequest request)
    {
        if (!ModelState.IsValid)
        {
            return BadRequest(CreateValidationErrorResponse());
        }

        try
        {
            // Business logic with validation
            var user = await _userService.CreateAsync(request);
            var response = _mapper.Map<UserDetailResponse>(user);
            
            return CreatedAtAction(
                nameof(GetUserById), 
                new { id = user.Id }, 
                response);
        }
        catch (DuplicateUserException ex)
        {
            return Conflict(CreateErrorResponse("USER_EXISTS", ex.Message));
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error creating user");
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    /// <summary>
    /// Update user - Generated from Swagger specification
    /// </summary>
    [HttpPut("{id:long}")]
    [Authorize(Policy = "UserWrite")]
    [ProducesResponseType(typeof(UserDetailResponse), 200)]
    [ProducesResponseType(typeof(ValidationErrorResponse), 400)]
    [ProducesResponseType(typeof(ErrorResponse), 404)]
    public async Task<ActionResult<UserDetailResponse>> UpdateUser(
        [FromRoute] long id,
        [FromBody] UpdateUserRequest request)
    {
        if (!ModelState.IsValid)
        {
            return BadRequest(CreateValidationErrorResponse());
        }

        try
        {
            var user = await _userService.UpdateAsync(id, request);
            if (user == null)
            {
                return NotFound(CreateErrorResponse("USER_NOT_FOUND", $"User with ID {id} not found"));
            }

            var response = _mapper.Map<UserDetailResponse>(user);
            return Ok(response);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error updating user {UserId}", id);
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    /// <summary>
    /// Delete user - Generated from Swagger specification
    /// </summary>
    [HttpDelete("{id:long}")]
    [Authorize(Policy = "UserDelete")]
    [ProducesResponseType(204)]
    [ProducesResponseType(typeof(ErrorResponse), 404)]
    public async Task<ActionResult> DeleteUser([FromRoute] long id)
    {
        try
        {
            var deleted = await _userService.DeleteAsync(id);
            if (!deleted)
            {
                return NotFound(CreateErrorResponse("USER_NOT_FOUND", $"User with ID {id} not found"));
            }

            return NoContent();
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error deleting user {UserId}", id);
            return StatusCode(500, CreateErrorResponse("INTERNAL_ERROR", "An unexpected error occurred"));
        }
    }

    private ErrorResponse CreateErrorResponse(string error, string message) => new()
    {
        Error = error,
        Message = message,
        Timestamp = DateTime.UtcNow,
        RequestId = HttpContext.TraceIdentifier
    };

    private ValidationErrorResponse CreateValidationErrorResponse()
    {
        var errors = ModelState
            .Where(x => x.Value.Errors.Count > 0)
            .SelectMany(x => x.Value.Errors.Select(e => new ValidationError
            {
                Field = x.Key,
                Message = e.ErrorMessage,
                Code = "VALIDATION_ERROR"
            }))
            .ToList();

        return new ValidationErrorResponse
        {
            Error = "VALIDATION_ERROR",
            Message = "Request validation failed",
            Details = errors,
            Timestamp = DateTime.UtcNow,
            RequestId = HttpContext.TraceIdentifier
        };
    }
}

// Generated DTOs from Swagger models
public class UserDetailResponse
{
    public long Id { get; set; }
    public string Username { get; set; }
    public string Email { get; set; }
    public UserProfile Profile { get; set; }
    public List<string> Roles { get; set; }
    public DateTime CreatedAt { get; set; }
    public DateTime? UpdatedAt { get; set; }
    public bool IsActive { get; set; }
}

public class CreateUserRequest
{
    [Required]
    [EmailAddress]
    public string Email { get; set; }

    [Required]
    [StringLength(100, MinimumLength = 2)]
    public string Name { get; set; }

    [Required]
    [StringLength(128, MinimumLength = 8)]
    public string Password { get; set; }

    public UserProfileRequest Profile { get; set; }
}

// Service interface based on Swagger operations
public interface IUserService
{
    Task<User> GetByIdAsync(long id, string[] include = null);
    Task<User> CreateAsync(CreateUserRequest request);
    Task<User> UpdateAsync(long id, UpdateUserRequest request);
    Task<bool> DeleteAsync(long id);
    Task<PagedResult<User>> GetUsersAsync(UserFilterCriteria criteria, int page, int pageSize);
}
```

**Java + Spring Boot Implementation:**
```java
// Generated from Swagger: Spring Boot REST Controller
@RestController
@RequestMapping("/api/v1/users")
@Validated
@RequiredArgsConstructor
@Slf4j
public class UserController {

    private final UserService userService;
    private final UserMapper userMapper;

    /**
     * Get user by ID - Generated from Swagger specification
     */
    @GetMapping("/{id}")
    @PreAuthorize("hasAuthority('USER_READ')")
    @Operation(summary = "Get user by ID", description = "Retrieves user information by unique identifier")
    @ApiResponses({
        @ApiResponse(responseCode = "200", description = "User found"),
        @ApiResponse(responseCode = "404", description = "User not found"),
        @ApiResponse(responseCode = "400", description = "Invalid user ID")
    })
    public ResponseEntity<UserDetailResponse> getUserById(
            @PathVariable @Valid @Positive Long id,
            @RequestParam(required = false) List<String> include) {
        
        try {
            Optional<User> user = userService.findById(id, include);
            return user.map(u -> ResponseEntity.ok(userMapper.toDetailResponse(u)))
                    .orElse(ResponseEntity.notFound().build());
        } catch (AccessDeniedException e) {
            throw new ResponseStatusException(HttpStatus.FORBIDDEN, "Access denied");
        } catch (Exception e) {
            log.error("Error retrieving user {}", id, e);
            throw new ResponseStatusException(HttpStatus.INTERNAL_SERVER_ERROR, "Internal server error");
        }
    }

    /**
     * Create new user - Generated from Swagger specification
     */
    @PostMapping
    @PreAuthorize("hasAuthority('USER_WRITE')")
    @Operation(summary = "Create user", description = "Creates a new user account")
    public ResponseEntity<UserDetailResponse> createUser(@Valid @RequestBody CreateUserRequest request) {
        try {
            User created = userService.create(request);
            UserDetailResponse response = userMapper.toDetailResponse(created);
            
            return ResponseEntity.status(HttpStatus.CREATED)
                    .location(URI.create("/api/v1/users/" + created.getId()))
                    .body(response);
        } catch (DuplicateUserException e) {
            throw new ResponseStatusException(HttpStatus.CONFLICT, e.getMessage());
        } catch (Exception e) {
            log.error("Error creating user", e);
            throw new ResponseStatusException(HttpStatus.INTERNAL_SERVER_ERROR, "Internal server error");
        }
    }

    /**
     * Update user - Generated from Swagger specification
     */
    @PutMapping("/{id}")
    @PreAuthorize("hasAuthority('USER_WRITE')")
    public ResponseEntity<UserDetailResponse> updateUser(
            @PathVariable @Valid @Positive Long id,
            @Valid @RequestBody UpdateUserRequest request) {
        try {
            Optional<User> updated = userService.update(id, request);
            return updated.map(u -> ResponseEntity.ok(userMapper.toDetailResponse(u)))
                    .orElse(ResponseEntity.notFound().build());
        } catch (Exception e) {
            log.error("Error updating user {}", id, e);
            throw new ResponseStatusException(HttpStatus.INTERNAL_SERVER_ERROR, "Internal server error");
        }
    }

    /**
     * Delete user - Generated from Swagger specification
     */
    @DeleteMapping("/{id}")
    @PreAuthorize("hasAuthority('USER_DELETE')")
    public ResponseEntity<Void> deleteUser(@PathVariable @Valid @Positive Long id) {
        try {
            boolean deleted = userService.delete(id);
            return deleted ? ResponseEntity.noContent().build() : ResponseEntity.notFound().build();
        } catch (Exception e) {
            log.error("Error deleting user {}", id, e);
            throw new ResponseStatusException(HttpStatus.INTERNAL_SERVER_ERROR, "Internal server error");
        }
    }
}

// Generated entities and DTOs
@Entity
@Table(name = "users")
@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    @Column(unique = true, nullable = false)
    private String email;
    
    @Column(nullable = false)
    private String name;
    
    @Enumerated(EnumType.STRING)
    private UserStatus status;
    
    @CreationTimestamp
    private LocalDateTime createdAt;
    
    @UpdateTimestamp
    private LocalDateTime updatedAt;
}

// Service implementation based on Swagger operations
@Service
@Transactional
@RequiredArgsConstructor
public class UserService {
    private final UserRepository userRepository;
    
    public Optional<User> findById(Long id, List<String> include) {
        // Implementation with include handling
        return userRepository.findById(id);
    }
    
    public User create(CreateUserRequest request) {
        // Implementation with validation
        User user = new User();
        user.setEmail(request.getEmail());
        user.setName(request.getName());
        return userRepository.save(user);
    }
    
    public Optional<User> update(Long id, UpdateUserRequest request) {
        return userRepository.findById(id)
                .map(user -> {
                    user.setName(request.getName());
                    return userRepository.save(user);
                });
    }
    
    public boolean delete(Long id) {
        if (userRepository.existsById(id)) {
            userRepository.deleteById(id);
            return true;
        }
        return false;
    }
}
```

**Node.js + TypeScript Implementation:**
```typescript
// Generated from Swagger: Express.js REST endpoints
import { Router, Request, Response, NextFunction } from 'express';
import { body, param, query, validationResult } from 'express-validator';
import { UserService } from '../services/UserService';
import { auth, requirePermission } from '../middleware/auth';
import { handleAsync } from '../middleware/asyncHandler';

export class UserController {
    private router = Router();
    
    constructor(private userService: UserService) {
        this.setupRoutes();
    }

    private setupRoutes() {
        // GET /api/v1/users/:id - Generated from Swagger
        this.router.get('/:id',
            auth.authenticate,
            requirePermission('user:read'),
            param('id').isInt({ min: 1 }).withMessage('User ID must be a positive integer'),
            query('include').optional().isArray().withMessage('Include must be an array'),
            handleAsync(this.getUserById.bind(this))
        );

        // POST /api/v1/users - Generated from Swagger
        this.router.post('/',
            auth.authenticate,
            requirePermission('user:write'),
            body('email').isEmail().withMessage('Must be a valid email'),
            body('name').isLength({ min: 2, max: 100 }).withMessage('Name must be 2-100 characters'),
            body('password').isLength({ min: 8 }).withMessage('Password must be at least 8 characters'),
            handleAsync(this.createUser.bind(this))
        );

        // PUT /api/v1/users/:id - Generated from Swagger
        this.router.put('/:id',
            auth.authenticate,
            requirePermission('user:write'),
            param('id').isInt({ min: 1 }),
            body('name').optional().isLength({ min: 2, max: 100 }),
            body('email').optional().isEmail(),
            handleAsync(this.updateUser.bind(this))
        );

        // DELETE /api/v1/users/:id - Generated from Swagger
        this.router.delete('/:id',
            auth.authenticate,
            requirePermission('user:delete'),
            param('id').isInt({ min: 1 }),
            handleAsync(this.deleteUser.bind(this))
        );
    }

    /**
     * Get user by ID - Generated from Swagger specification
     */
    private async getUserById(req: Request, res: Response): Promise<void> {
        const errors = validationResult(req);
        if (!errors.isEmpty()) {
            res.status(400).json({
                error: 'VALIDATION_ERROR',
                message: 'Request validation failed',
                details: errors.array(),
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
            return;
        }

        try {
            const id = parseInt(req.params.id);
            const include = req.query.include as string[] | undefined;

            const user = await this.userService.findById(id, include);
            if (!user) {
                res.status(404).json({
                    error: 'USER_NOT_FOUND',
                    message: `User with ID ${id} not found`,
                    timestamp: new Date().toISOString(),
                    requestId: req.id
                });
                return;
            }

            res.json(user);
        } catch (error) {
            throw error; // Handled by async handler middleware
        }
    }

    /**
     * Create new user - Generated from Swagger specification
     */
    private async createUser(req: Request, res: Response): Promise<void> {
        const errors = validationResult(req);
        if (!errors.isEmpty()) {
            res.status(400).json({
                error: 'VALIDATION_ERROR',
                message: 'Request validation failed',
                details: errors.array(),
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
            return;
        }

        try {
            const created = await this.userService.create(req.body);
            
            res.status(201)
               .location(`/api/v1/users/${created.id}`)
               .json(created);
        } catch (error) {
            if (error.code === 'USER_EXISTS') {
                res.status(409).json({
                    error: 'USER_EXISTS',
                    message: error.message,
                    timestamp: new Date().toISOString(),
                    requestId: req.id
                });
                return;
            }
            throw error;
        }
    }

    /**
     * Update user - Generated from Swagger specification
     */
    private async updateUser(req: Request, res: Response): Promise<void> {
        const errors = validationResult(req);
        if (!errors.isEmpty()) {
            res.status(400).json({
                error: 'VALIDATION_ERROR',
                message: 'Request validation failed',
                details: errors.array(),
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
            return;
        }

        try {
            const id = parseInt(req.params.id);
            const updated = await this.userService.update(id, req.body);
            
            if (!updated) {
                res.status(404).json({
                    error: 'USER_NOT_FOUND',
                    message: `User with ID ${id} not found`,
                    timestamp: new Date().toISOString(),
                    requestId: req.id
                });
                return;
            }

            res.json(updated);
        } catch (error) {
            throw error;
        }
    }

    /**
     * Delete user - Generated from Swagger specification
     */
    private async deleteUser(req: Request, res: Response): Promise<void> {
        const errors = validationResult(req);
        if (!errors.isEmpty()) {
            res.status(400).json({
                error: 'VALIDATION_ERROR',
                message: 'Request validation failed',
                details: errors.array(),
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
            return;
        }

        try {
            const id = parseInt(req.params.id);
            const deleted = await this.userService.delete(id);
            
            if (!deleted) {
                res.status(404).json({
                    error: 'USER_NOT_FOUND',
                    message: `User with ID ${id} not found`,
                    timestamp: new Date().toISOString(),
                    requestId: req.id
                });
                return;
            }

            res.status(204).send();
        } catch (error) {
            throw error;
        }
    }

    public getRouter(): Router {
        return this.router;
    }
}

// Generated interfaces from Swagger models
export interface UserDetailResponse {
    id: number;
    username: string;
    email: string;
    profile?: UserProfile;
    roles: string[];
    createdAt: string;
    updatedAt?: string;
    isActive: boolean;
}

export interface CreateUserRequest {
    email: string;
    name: string;
    password: string;
    profile?: UserProfileRequest;
}

export interface UpdateUserRequest {
    name?: string;
    email?: string;
    profile?: UserProfileRequest;
}

// Service implementation
export class UserService {
    constructor(private userRepository: UserRepository) {}

    async findById(id: number, include?: string[]): Promise<UserDetailResponse | null> {
        // Implementation with include parameter handling
        const user = await this.userRepository.findById(id);
        if (!user) return null;
        
        return this.mapToResponse(user, include);
    }

    async create(request: CreateUserRequest): Promise<UserDetailResponse> {
        // Check for existing user
        const existing = await this.userRepository.findByEmail(request.email);
        if (existing) {
            throw new Error('User with this email already exists');
        }

        const user = await this.userRepository.create(request);
        return this.mapToResponse(user);
    }

    async update(id: number, request: UpdateUserRequest): Promise<UserDetailResponse | null> {
        const user = await this.userRepository.update(id, request);
        return user ? this.mapToResponse(user) : null;
    }

    async delete(id: number): Promise<boolean> {
        return await this.userRepository.delete(id);
    }

    private mapToResponse(user: any, include?: string[]): UserDetailResponse {
        // Map entity to response DTO based on Swagger schema
        return {
            id: user.id,
            username: user.username,
            email: user.email,
            profile: include?.includes('profile') ? user.profile : undefined,
            roles: user.roles || [],
            createdAt: user.createdAt.toISOString(),
            updatedAt: user.updatedAt?.toISOString(),
            isActive: user.isActive
        };
    }
}
```

**Python + FastAPI Implementation:**
```python
# Generated from Swagger: FastAPI endpoints
from fastapi import APIRouter, Depends, HTTPException, status, Query, Path
from typing import List, Optional
from pydantic import BaseModel, EmailStr, validator
from ..services.user_service import UserService
from ..dependencies.auth import get_current_user, require_permission
from ..schemas.user_schemas import UserDetailResponse, CreateUserRequest, UpdateUserRequest
from ..models.user import User
import logging

logger = logging.getLogger(__name__)
router = APIRouter(prefix="/api/v1/users", tags=["users"])

@router.get(
    "/{user_id}",
    response_model=UserDetailResponse,
    status_code=status.HTTP_200_OK,
    summary="Get user by ID",
    description="Retrieves detailed user information by unique identifier - Generated from Swagger",
    dependencies=[Depends(require_permission("user:read"))]
)
async def get_user_by_id(
    user_id: int = Path(..., title="User ID", description="Unique user identifier", ge=1),
    include: Optional[List[str]] = Query(None, description="Related data to include"),
    current_user: User = Depends(get_current_user),
    user_service: UserService = Depends(get_user_service)
):
    """Get user by ID - Generated from Swagger specification"""
    try:
        user = await user_service.get_by_id(user_id, include)
        if not user:
            raise HTTPException(
                status_code=status.HTTP_404_NOT_FOUND,
                detail=f"User with ID {user_id} not found"
            )
        return user
    except PermissionError:
        raise HTTPException(
            status_code=status.HTTP_403_FORBIDDEN,
            detail="Insufficient permissions"
        )
    except Exception as e:
        logger.error(f"Error retrieving user {user_id}: {e}")
        raise HTTPException(
            status_code=status.HTTP_500_INTERNAL_SERVER_ERROR,
            detail="Internal server error"
        )

@router.post(
    "/",
    response_model=UserDetailResponse,
    status_code=status.HTTP_201_CREATED,
    summary="Create new user",
    description="Creates a new user account - Generated from Swagger",
    dependencies=[Depends(require_permission("user:write"))]
)
async def create_user(
    request: CreateUserRequest,
    current_user: User = Depends(get_current_user),
    user_service: UserService = Depends(get_user_service)
):
    """Create new user - Generated from Swagger specification"""
    try:
        created = await user_service.create(request)
        return created
    except ValueError as e:
        raise HTTPException(
            status_code=status.HTTP_409_CONFLICT,
            detail=str(e)
        )
    except Exception as e:
        logger.error(f"Error creating user: {e}")
        raise HTTPException(
            status_code=status.HTTP_500_INTERNAL_SERVER_ERROR,
            detail="Internal server error"
        )

@router.put(
    "/{user_id}",
    response_model=UserDetailResponse,
    status_code=status.HTTP_200_OK,
    summary="Update user",
    description="Updates user information - Generated from Swagger",
    dependencies=[Depends(require_permission("user:write"))]
)
async def update_user(
    user_id: int = Path(..., ge=1),
    request: UpdateUserRequest,
    current_user: User = Depends(get_current_user),
    user_service: UserService = Depends(get_user_service)
):
    """Update user - Generated from Swagger specification"""
    try:
        updated = await user_service.update(user_id, request)
        if not updated:
            raise HTTPException(
                status_code=status.HTTP_404_NOT_FOUND,
                detail=f"User with ID {user_id} not found"
            )
        return updated
    except Exception as e:
        logger.error(f"Error updating user {user_id}: {e}")
        raise HTTPException(
            status_code=status.HTTP_500_INTERNAL_SERVER_ERROR,
            detail="Internal server error"
        )

@router.delete(
    "/{user_id}",
    status_code=status.HTTP_204_NO_CONTENT,
    summary="Delete user",
    description="Deletes a user account - Generated from Swagger",
    dependencies=[Depends(require_permission("user:delete"))]
)
async def delete_user(
    user_id: int = Path(..., ge=1),
    current_user: User = Depends(get_current_user),
    user_service: UserService = Depends(get_user_service)
):
    """Delete user - Generated from Swagger specification"""
    try:
        deleted = await user_service.delete(user_id)
        if not deleted:
            raise HTTPException(
                status_code=status.HTTP_404_NOT_FOUND,
                detail=f"User with ID {user_id} not found"
            )
    except Exception as e:
        logger.error(f"Error deleting user {user_id}: {e}")
        raise HTTPException(
            status_code=status.HTTP_500_INTERNAL_SERVER_ERROR,
            detail="Internal server error"
        )

# Generated Pydantic models from Swagger schemas
class UserDetailResponse(BaseModel):
    """User detail response generated from Swagger schema"""
    id: int
    username: str
    email: EmailStr
    profile: Optional[UserProfile] = None
    roles: List[str]
    created_at: datetime
    updated_at: Optional[datetime] = None
    is_active: bool

    class Config:
        from_attributes = True

class CreateUserRequest(BaseModel):
    """Create user request generated from Swagger schema"""
    email: EmailStr
    name: str
    password: str
    profile: Optional[UserProfileRequest] = None

    @validator('name')
    def validate_name(cls, v):
        if len(v.strip()) < 2:
            raise ValueError('Name must be at least 2 characters')
        return v.strip()

    @validator('password')
    def validate_password(cls, v):
        if len(v) < 8:
            raise ValueError('Password must be at least 8 characters')
        return v

# Service implementation
class UserService:
    def __init__(self, user_repository: UserRepository):
        self.user_repository = user_repository

    async def get_by_id(self, user_id: int, include: Optional[List[str]] = None) -> Optional[UserDetailResponse]:
        user = await self.user_repository.get_by_id(user_id)
        if not user:
            return None
        
        return UserDetailResponse.from_orm(user)

    async def create(self, request: CreateUserRequest) -> UserDetailResponse:
        # Check for existing user
        existing = await self.user_repository.get_by_email(request.email)
        if existing:
            raise ValueError("User with this email already exists")

        user = await self.user_repository.create(request)
        return UserDetailResponse.from_orm(user)

    async def update(self, user_id: int, request: UpdateUserRequest) -> Optional[UserDetailResponse]:
        user = await self.user_repository.update(user_id, request)
        return UserDetailResponse.from_orm(user) if user else None

    async def delete(self, user_id: int) -> bool:
        return await self.user_repository.delete(user_id)
```

### Step 3: Security and Validation Implementation

**Authentication Middleware:**
```typescript
// JWT Authentication middleware generated from Swagger security schemes
import jwt from 'jsonwebtoken';
import { Request, Response, NextFunction } from 'express';

interface AuthenticatedRequest extends Request {
    user?: {
        id: number;
        username: string;
        roles: string[];
    };
}

export const authenticate = async (req: AuthenticatedRequest, res: Response, next: NextFunction) => {
    try {
        const authHeader = req.headers.authorization;
        if (!authHeader?.startsWith('Bearer ')) {
            return res.status(401).json({
                error: 'UNAUTHORIZED',
                message: 'Authentication token required',
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
        }

        const token = authHeader.substring(7);
        const decoded = jwt.verify(token, process.env.JWT_SECRET!) as any;
        
        req.user = {
            id: decoded.sub,
            username: decoded.username,
            roles: decoded.roles || []
        };
        
        next();
    } catch (error) {
        return res.status(401).json({
            error: 'UNAUTHORIZED',
            message: 'Invalid or expired token',
            timestamp: new Date().toISOString(),
            requestId: req.id
        });
    }
};

export const requirePermission = (permission: string) => {
    return (req: AuthenticatedRequest, res: Response, next: NextFunction) => {
        if (!req.user) {
            return res.status(401).json({
                error: 'UNAUTHORIZED',
                message: 'Authentication required',
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
        }

        // Simple permission check - enhance based on your permission system
        if (!req.user.roles.includes('admin') && !req.user.roles.includes(permission.split(':')[0])) {
            return res.status(403).json({
                error: 'FORBIDDEN',
                message: 'Insufficient permissions',
                timestamp: new Date().toISOString(),
                requestId: req.id
            });
        }

        next();
    };
};
```

## Quality Gates

### ✅ Swagger Compliance
- [ ] All endpoints from Swagger specification implemented
- [ ] Request/response models match Swagger schemas exactly
- [ ] HTTP status codes match documentation
- [ ] Authentication requirements implemented correctly

### ✅ Technology Alignment
- [ ] Implementation uses framework specified in copilot.instructions.md
- [ ] Code follows existing project patterns and conventions
- [ ] Integration with existing middleware and services
- [ ] Proper dependency injection configuration

### ✅ Production Readiness
- [ ] Comprehensive error handling and logging
- [ ] Input validation and sanitization
- [ ] Security best practices applied
- [ ] Performance considerations addressed

### ✅ Code Quality
- [ ] Clean, maintainable code structure
- [ ] Proper separation of concerns
- [ ] Comprehensive unit tests included
- [ ] Documentation comments added

## Transition to Specialized Chatmodes

After completing API endpoint generation from Swagger:

- **For Frontend Integration**: Switch to **@frontend-engineer** chatmode to generate client SDK and integration code for the implemented endpoints
- **For Database Implementation**: Switch to **@data-engineer** chatmode to implement the data access layer and optimize database queries
- **For Security Enhancement**: Switch to **@security-engineer** chatmode to implement advanced security controls and vulnerability assessments
- **For Testing Implementation**: Switch to **@qa-engineer** chatmode to create comprehensive test suites for the generated endpoints

**This prompt ensures API endpoints are generated using the exact technology stack specified in copilot.instructions.md, maintaining consistency between Swagger documentation and implementation while following industry best practices.**