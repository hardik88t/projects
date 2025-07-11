# Good Coding Practices (GCP) - Security & Best Practices

## 🔐 Security Standards

### Environment Variables & Secrets Management
- **NEVER commit credentials, API keys, or secrets to git**
- Always use `.env` files for sensitive configuration
- Include `.env.example` with dummy values to show required variables
- Add `.env*` to `.gitignore` (except `.env.example`)
- Use different `.env` files for different environments (`.env.local`, `.env.production`)

```bash
# .env.example
GEMINI_API_KEY=your_gemini_api_key_here
DATABASE_URL=postgresql://user:password@localhost:5432/dbname
JWT_SECRET=your_jwt_secret_here
STRIPE_SECRET_KEY=sk_test_your_stripe_key
```

### API Key Security
- **Gemini API**: Use OpenAI-compatible libraries with Gemini credentials
- **Local LLM**: Prefer local models when possible for sensitive data
- **Rate Limiting**: Implement proper rate limiting for API endpoints
- **Input Validation**: Always validate and sanitize user inputs
- **CORS**: Configure proper CORS policies for web applications

### Authentication & Authorization
- Use secure session management (JWT with proper expiration)
- Implement proper password hashing (bcrypt, argon2)
- Add multi-factor authentication where applicable
- Use HTTPS in production environments
- Implement proper role-based access control (RBAC)

## 🏗️ Code Quality Standards

### Project Structure
```
project-name/
├── .env.example          # Environment variables template
├── .gitignore           # Git ignore rules
├── README.md            # Project documentation
├── DEVLOG.md            # Development progress
├── package.json         # Dependencies and scripts
├── src/
│   ├── components/      # Reusable components
│   ├── pages/          # Page components
│   ├── hooks/          # Custom hooks
│   ├── utils/          # Utility functions
│   ├── types/          # TypeScript type definitions
│   └── config/         # Configuration files
├── public/             # Static assets
└── tests/              # Test files
```

### TypeScript Usage
- Use TypeScript for all new projects where applicable
- Define proper interfaces and types
- Avoid `any` type - use proper typing
- Use strict TypeScript configuration
- Document complex types with JSDoc comments

### Error Handling
- Implement proper error boundaries in React applications
- Use try-catch blocks for async operations
- Provide meaningful error messages to users
- Log errors appropriately (without exposing sensitive data)
- Implement graceful fallbacks for failed operations

## 🧪 Testing & Quality Assurance

### Testing Strategy
- Write unit tests for utility functions
- Add integration tests for API endpoints
- Include end-to-end tests for critical user flows
- Maintain test coverage above 80% for critical code
- Use proper mocking for external dependencies

### Code Linting & Formatting
- Use ESLint for JavaScript/TypeScript projects
- Configure Prettier for consistent code formatting
- Set up pre-commit hooks with Husky
- Use consistent naming conventions
- Follow language-specific style guides

## 🚀 Deployment & DevOps

### Docker Best Practices
- Use multi-stage builds to reduce image size
- Don't run containers as root user
- Use specific version tags, avoid `latest`
- Implement health checks
- Use `.dockerignore` to exclude unnecessary files

### CI/CD Pipeline
- Run tests on every pull request
- Implement automated security scanning
- Use environment-specific deployments
- Implement proper rollback strategies
- Monitor deployment success/failure

### Performance Optimization
- Implement proper caching strategies
- Optimize database queries
- Use CDN for static assets
- Implement lazy loading where appropriate
- Monitor and optimize bundle sizes

## 🤖 AI Project Specific Guidelines

### API Usage
- **Gemini API**: Use OpenAI-compatible libraries for cost efficiency
- **Local LLM**: Implement fallback to local models for privacy-sensitive operations
- **Rate Limiting**: Implement proper rate limiting to avoid API quota issues
- **Caching**: Cache AI responses when appropriate to reduce API calls
- **Error Handling**: Graceful degradation when AI services are unavailable

### Data Privacy
- Never send sensitive user data to external AI APIs
- Implement data anonymization where necessary
- Provide clear privacy policies for AI features
- Allow users to opt-out of AI features
- Store minimal data required for functionality

### Local LLM Integration
- Use lightweight models for simple tasks (e.g., Ollama with Llama 2 7B)
- Implement proper resource management
- Provide fallback to cloud APIs when local resources are insufficient
- Document hardware requirements clearly
- Implement model downloading and management

## 📱 Frontend Best Practices

### React/Vue/Angular Specific
- Use functional components with hooks (React)
- Implement proper state management (Zustand, Pinia, NgRx)
- Optimize re-renders with proper memoization
- Use proper component composition patterns
- Implement accessibility (a11y) standards

### ShadCN/UI Integration
- Follow ShadCN component patterns consistently
- Customize theme tokens properly
- Use proper component composition
- Implement responsive design patterns
- Maintain consistent spacing and typography

### Performance
- Implement code splitting and lazy loading
- Optimize images and assets
- Use proper caching strategies
- Monitor Core Web Vitals
- Implement proper SEO practices

## 🗄️ Backend Best Practices

### API Design
- Follow RESTful principles or GraphQL best practices
- Implement proper HTTP status codes
- Use consistent response formats
- Implement API versioning
- Provide comprehensive API documentation

### Database Security
- Use parameterized queries to prevent SQL injection
- Implement proper database connection pooling
- Use database migrations for schema changes
- Implement proper backup strategies
- Monitor database performance

### Logging & Monitoring
- Implement structured logging
- Monitor application performance
- Set up proper alerting
- Track user analytics (with privacy compliance)
- Implement health check endpoints

## 🔧 Development Tools

### Recommended Tools
- **Gemini CLI**: Use for AI-assisted development when available
- **GitHub CLI**: For repository management and automation
- **Docker**: For consistent development environments
- **VS Code**: With proper extensions for each tech stack
- **Postman/Insomnia**: For API testing

### Git Best Practices
- Use conventional commit messages
- Create feature branches for new development
- Use pull requests for code review
- Keep commits atomic and focused
- Write descriptive commit messages

## 📋 Project Checklist

### Before Starting Development
- [ ] Set up proper project structure
- [ ] Configure environment variables
- [ ] Set up linting and formatting
- [ ] Initialize testing framework
- [ ] Configure CI/CD pipeline

### Before Deployment
- [ ] Remove all hardcoded secrets
- [ ] Test with production-like data
- [ ] Verify all environment variables
- [ ] Run security scans
- [ ] Test deployment process

### Post-Deployment
- [ ] Monitor application performance
- [ ] Set up logging and alerting
- [ ] Document deployment process
- [ ] Plan backup and recovery
- [ ] Schedule security updates

## 🚨 Common Security Pitfalls to Avoid

1. **Committing secrets to git** - Use .env files and .gitignore
2. **Exposing API keys in frontend** - Use backend proxy for sensitive APIs
3. **SQL injection** - Use parameterized queries
4. **XSS attacks** - Sanitize user inputs
5. **CSRF attacks** - Implement proper CSRF protection
6. **Insecure dependencies** - Regularly update and audit dependencies
7. **Weak authentication** - Use strong password policies and MFA
8. **Insufficient logging** - Log security events properly
9. **Missing HTTPS** - Always use HTTPS in production
10. **Improper error handling** - Don't expose sensitive information in errors

---

*This document should be referenced for every project in the templates collection to ensure consistent security and quality standards.*
