# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Daily Budget** application built with **Rails 8.1.0.beta1** and **Ruby 3.4.5**. It's a modern Rails application using the full cutting-edge stack with Hotwire, Solid Suite, and Kamal deployment. Currently, it's a fresh Rails installation with production-ready infrastructure but no business logic implemented yet.

## Development Commands

### Environment Setup
```bash
bin/setup        # One-time environment setup
bin/rails db:prepare # Prepare database (create, migrate, seed)
```

### Development Server
```bash
bin/dev          # Start development server with hot reload
bin/rails server # Start Rails server
```

### Testing
```bash
bin/rails test          # Run all tests
bin/rails test:system   # Run system tests
bin/rails test:controllers # Run controller tests
bin/rails test:models   # Run model tests
bin/rails test:jobs     # Run job tests
bin/rails test:mailers  # Run mailer tests
```

### Code Quality
```bash
bin/rails lint           # Run RuboCop linting
bin/brakeman             # Run Brakeman security scan
bin/bundler-audit        # Check for vulnerable gems
bundle exec rubocop -A   # Auto-fix RuboCop issues
```

### Continuous Integration
```bash
bin/ci           # Run full CI pipeline locally
```

### Database Operations
```bash
bin/rails db:create       # Create database
bin/rails db:migrate      # Run migrations
bin/rails db:rollback     # Rollback last migration
bin/rails db:seed         # Seed database
bin/rails db:reset        # Reset database (drop, create, migrate, seed)
```

### Deployment
```bash
kamal deploy     # Deploy to production
kamal setup      # Initial deployment setup
```

## Architecture Overview

### Modern Rails 8 Stack
- **Hotwire**: Turbo + Stimulus with Import Maps for frontend
- **Solid Suite**: Database-backed cache, jobs, and cable for production
- **Propshaft**: Modern asset pipeline (Sprockets replacement)
- **Kamal**: Container-based deployment (Capistrano alternative)
- **Puma + Thruster**: Modern web server setup

### Key Technologies
- **Database**: SQLite3 for development, production-ready for PostgreSQL/MySQL
- **Authentication**: None configured (ready for Devise or similar)
- **Frontend**: Hotwire with Tailwind CSS
- **Background Jobs**: Solid Queue (database-backed)
- **Caching**: Solid Cache (database-backed)
- **WebSockets**: Solid Cable (database-backed)

### Directory Structure
```
app/          # Main application code
├── channels/  # Action Cable channels
├── controllers/ # Controllers
├── helpers/   # View helpers
├── jobs/      # Background jobs
├── mailers/   # Mailers
├── models/    # ActiveRecord models
└── views/     # View templates
config/       # Configuration files
db/          # Database schema and migrations
lib/         # Library code
public/      # Static assets
test/        # Test files
├── application_system_test_case.rb
├── channels/
├── controllers/
├── fixtures/
├── helpers/
├── integration/
├── mailers/
├── models/
└── system/
```

## Development Patterns

### Controllers
- Follow Rails conventions with `ApplicationController` as base
- Use strong parameters for security
- Implement proper error handling with rescue blocks

### Models
- Use ActiveRecord with proper associations and validations
- Follow Rails naming conventions
- Implement proper indexing for database performance

### Views
- Use Hotwire patterns with Turbo frames and streams
- Implement Stimulus controllers for JavaScript functionality
- Use Tailwind CSS for styling

### Background Jobs
- Use Solid Queue for database-backed job processing
- Implement proper error handling and retry logic
- Follow Rails job conventions

### Testing
- Use Rails built-in test framework
- Implement system tests for critical user flows
- Use fixtures for test data
- Follow Rails testing conventions

## Security Considerations

### Built-in Security
- Brakeman integration for security scanning
- Bundler Audit for vulnerable gem detection
- Rails security features enabled by default
- Content Security Policy configured

### Development Security
- Never commit secrets or API keys
- Use Rails credentials for sensitive data
- Follow Rails security best practices
- Implement proper authentication and authorization

## Performance Considerations

### Database
- Use proper indexing for queries
- Implement database constraints
- Use Rails associations efficiently
- Consider query optimization with includes

### Frontend
- Use Turbo for fast page updates
- Implement proper caching strategies
- Optimize asset loading with Propshaft
- Use Stimulus efficiently for JavaScript

## Deployment

### Kamal Configuration
- Uses Docker containers for deployment
- Implements zero-downtime deployments
- Configured for production with proper security
- Includes automatic SSL certificate management

### Production Environment
- Uses Solid Suite for production scalability
- Implements proper logging and monitoring
- Configured for high availability
- Includes backup and recovery procedures

## Current State

The application is currently a **fresh Rails installation** with:
- No custom models, controllers, or business logic
- Production-ready infrastructure fully configured
- Modern development toolchain in place
- Security and quality tools integrated
- Ready for building a budget tracking application

## Next Steps

When developing features for this application:
1. Start with database models for budget tracking
2. Implement controllers following REST conventions
3. Build views using Hotwire patterns
4. Add background jobs for processing
5. Implement proper authentication
6. Add comprehensive testing
7. Optimize for production deployment