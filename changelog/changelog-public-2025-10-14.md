# Pontus-X Changelog
## October 1-14, 2025

### Features
- **Wallet Onboarding Interface**: Added new identity section on wallet settings page allowing users to request onboarding of their wallets with loading states and improved UX
- **Terms & Conditions**: Added dedicated terms and conditions page with proper routing and footer links for compliance
- **Light Mode Support**: Enhanced light mode design across HomePage, header, footer, and wallet components for better accessibility

### Identity & Access
- **Automated Faucet Integration**: Implemented automatic token airdrops after successful organization wallet onboarding via RabbitMQ events
- **Registry Service Connection**: Connected onboarding backend with registry microservice, enabling `POST /organizations/{id}/onboard` endpoint for organization registration
- **Environment-Based Contract Configuration**: Added support for environment variables in registry service with validation for all deployment addresses and role hashes

### Infrastructure
- **Microservice Architecture**: Moved faucet service into platform monorepo with updated GitHub workflows and reduced build triggers
- **RabbitMQ Event System**: Added comprehensive RabbitMQ integration with queue management, event schemas, and DTOs for cross-service communication
- **Testing Infrastructure**: Implemented Jest-based testing suite for NFT factory and identity issuer services with mock and integration test support
- **Health Monitoring**: Added health check endpoints and container monitoring capabilities across services

### Ocean Protocol Enhancements
- **Job Details Service**: Improved dependency injection architecture and simplified public API for better maintainability
- **DID Auto-Detection**: Added automatic DID detection capabilities for streamlined data asset management
- **Dynamic Path Support**: Enhanced input file handling with dynamic path resolution and easier iteration

### Bug Fixes
- **Onboarding Response Handling**: Fixed success response handling in onboard API routes and improved error wallet checking
- **Authorization Security**: Added proper authorization checks before nonce generation to prevent unauthorized access
- **Container Deployment**: Resolved missing environment variables in Kubernetes deployments and fixed Docker build configurations
- **UI State Management**: Corrected address form optional flag handling and improved form visibility state management

### Performance & Reliability
- **Request Timeouts**: Increased onboard request timeout to 20 seconds to accommodate on-chain interactions
- **API Key Authentication**: Added API key authentication for registry microservice requests
- **Docker Optimization**: Improved Dockerfiles with better layer caching and added .dockerignore for optimized builds