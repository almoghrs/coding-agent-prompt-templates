---
applyTo: "**/*.{ts,js}"
---

# NestJS Best Practices and Standards

**Purpose** – Enforce consistent NestJS development patterns, architectural principles, and modern backend practices.

**Guidelines:**
- Follow modular architecture with proper separation of concerns
- Use TypeScript with strict mode for type safety
- Implement dependency injection and IoC patterns
- Use decorators for controllers, services, and validation
- Apply proper exception handling with filters
- Use class-validator and class-transformer for validation
- Follow RESTful API design with OpenAPI documentation
- Implement JWT authentication with guards
- Use proper logging and error handling
- Apply database best practices with TypeORM/Prisma

**When to Apply:**
1. Module/service/controller creation
2. API endpoint development
3. Database integration
4. Authentication implementation
5. Middleware/guard creation
6. Testing and deployment

**Project Structure:**
```
src/
├── modules/
│   ├── auth/
│   │   ├── auth.module.ts
│   │   ├── auth.service.ts
│   │   ├── auth.controller.ts
│   │   ├── guards/
│   │   └── dto/
│   └── users/
│       ├── users.module.ts
│       ├── users.service.ts
│       ├── users.controller.ts
│       ├── entities/
│       └── dto/
├── common/
│   ├── filters/
│   ├── guards/
│   ├── interceptors/
│   └── pipes/
├── config/
└── main.ts
```

**Key Patterns:**

**Module Structure:**
```typescript
// users.module.ts
@Module({
  imports: [TypeOrmModule.forFeature([User])],
  controllers: [UsersController],
  providers: [UsersService],
  exports: [UsersService],
})
export class UsersModule {}
```

**Service:**
```typescript
@Injectable()
export class UsersService {
  constructor(@InjectRepository(User) private userRepository: Repository<User>) {}

  async create(createUserDto: CreateUserDto): Promise<User> {
    const user = this.userRepository.create(createUserDto);
    return await this.userRepository.save(user);
  }

  async findOne(id: string): Promise<User> {
    const user = await this.userRepository.findOne({ where: { id } });
    if (!user) throw new NotFoundException(`User ${id} not found`);
    return user;
  }
}
```

**Controller:**
```typescript
@ApiTags('users')
@Controller('users')
@UseGuards(JwtAuthGuard)
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Post()
  @ApiOperation({ summary: 'Create user' })
  create(@Body() createUserDto: CreateUserDto) {
    return this.usersService.create(createUserDto);
  }

  @Get(':id')
  findOne(@Param('id', ParseUUIDPipe) id: string) {
    return this.usersService.findOne(id);
  }
}
```

**DTO with Validation:**
```typescript
export class CreateUserDto {
  @ApiProperty()
  @IsEmail()
  @IsNotEmpty()
  email: string;

  @ApiProperty()
  @IsString()
  @MinLength(8)
  password: string;
}
```

**Entity:**
```typescript
@Entity('users')
export class User {
  @PrimaryGeneratedColumn('uuid')
  id: string;

  @Column({ unique: true })
  email: string;

  @Column()
  @Exclude()
  password: string;

  @BeforeInsert()
  async hashPassword() {
    this.password = await bcrypt.hash(this.password, 10);
  }
}
```

**Exception Filter:**
```typescript
@Catch(HttpException)
export class HttpExceptionFilter implements ExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse<Response>();
    const status = exception.getStatus();

    response.status(status).json({
      statusCode: status,
      timestamp: new Date().toISOString(),
      message: exception.message,
    });
  }
}
```

**Guard:**
```typescript
@Injectable()
export class JwtAuthGuard extends AuthGuard('jwt') {
  canActivate(context: ExecutionContext) {
    return super.canActivate(context);
  }

  handleRequest(err, user, info) {
    if (err || !user) throw err || new UnauthorizedException();
    return user;
  }
}
```

**Authentication:**
- Use JWT tokens with proper expiration
- Implement refresh token mechanism
- Use bcrypt for password hashing
- Implement RBAC with guards
- Use rate limiting for auth endpoints

**Database:**
- Use migrations for schema changes
- Implement proper indexing
- Use transactions for complex operations
- Handle database errors properly
- Use connection pooling

**Testing:**
- Unit tests for services/controllers
- Mock external dependencies
- Integration tests for API endpoints
- Test error scenarios
- Maintain 80%+ coverage

**Security:**
- Validate all inputs with DTOs
- Use HTTPS in production
- Implement CORS properly
- Use environment variables for secrets
- Implement rate limiting
- Use helmet for security headers

**Performance:**
- Implement caching where appropriate
- Use compression middleware
- Optimize database queries
- Implement pagination
- Use proper HTTP status codes

**Output Format:**
- Follow NestJS conventions
- Use TypeScript strict mode
- Implement proper error handling
- Use OpenAPI documentation
- Apply consistent naming
- Use structured logging
