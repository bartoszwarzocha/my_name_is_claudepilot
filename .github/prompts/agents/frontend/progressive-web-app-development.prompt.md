---
name: progressive-web-app
description: |
  **🤖 GitHub Copilot Chatmode: @frontend-engineer**

  Design and implement comprehensive Progressive Web Applications (PWAs) with advanced offline functionality, background sync, push notifications, and native-like experiences across all devices and platforms.

  **📋 Context Integration**: Automatically reads .github/copilot.instructions.md to adapt PWA strategies to project requirements.
---

# Progressive Web App Development

**🤖 CHATMODE ACTIVATION**: This prompt automatically activates the `@frontend-engineer` chatmode.
**📋 AGENT CONTEXT**: The activated chatmode will read .github/copilot.instructions.md and adapt to project requirements.
**🔄 WORKFLOW INTEGRATION**: All PWA development tasks will be managed through integrated GitHub Copilot workflows.

## ✅ FUNCTIONAL REQUIREMENTS

Design and implement comprehensive Progressive Web Applications that deliver native-like experiences with advanced offline functionality, background synchronization, push notifications, and seamless integration with device features. Create app-like experiences that work consistently across all platforms and devices while maintaining web accessibility.

**PWA Implementation Requirements:**
- Develop advanced Service Worker with sophisticated caching strategies and background sync
- Create comprehensive PWA manifest with installation prompts and native integration
- Implement offline-first architecture with IndexedDB storage and conflict resolution
- Configure push notifications with targeting, interactive actions, and engagement tracking
- Integrate native device APIs with graceful fallbacks and permission management
- Establish automatic update management with user-controlled deployment

## 🔄 HIGH-LEVEL ALGORITHMS

**Phase 1: PWA Architecture and Service Worker Setup**
1. Read .github/copilot.instructions.md to determine PWA requirements and technology constraints
2. Configure advanced Service Worker with intelligent caching strategies and request routing
3. Implement background sync for offline data synchronization and conflict resolution
4. Establish PWA manifest with comprehensive app configuration and installation prompts
5. Create offline fallback strategies and error handling for network failures

**Phase 2: Offline Functionality and Data Management**
1. Implement IndexedDB storage system with versioning and automatic cleanup
2. Create offline-first data synchronization with conflict resolution algorithms
3. Develop background sync queue for deferred operations and retry mechanisms
4. Configure cache management with expiration policies and storage optimization
5. Establish offline state management and user feedback systems

**Phase 3: Push Notifications and Engagement**
1. Configure push notification system with VAPID keys and subscription management
2. Implement notification targeting, segmentation, and personalization features
3. Create interactive notification actions and deep linking capabilities
4. Develop notification scheduling and background notification handling
5. Establish engagement analytics and notification performance tracking

**Phase 4: Native Features and Performance Optimization**
1. Integrate device APIs including camera, geolocation, device motion, and sensors
2. Implement Web Share API, File System Access, and clipboard integration
3. Configure performance optimization with resource preloading and critical path optimization
4. Establish cross-platform compatibility testing and graceful degradation
5. Create update management system with automatic detection and user-controlled installation

## ✓ VALIDATION CRITERIA

**PWA Performance Excellence:**
- Lighthouse PWA score achieves 90+ points across all categories
- First load performance under 3 seconds on 3G networks
- Offline functionality covers 100% of critical user workflows
- Installation rate exceeds 25% of repeat visitors

**Native Integration Standards:**
- Device API integration covers 80%+ of available platform features
- Permission handling includes graceful fallbacks for all scenarios
- Cross-platform experience maintains consistency across iOS, Android, and Desktop
- Battery impact remains under 5% additional drain from PWA features

**User Experience Metrics:**
- App-like navigation and interaction patterns throughout application
- User engagement increases 40%+ post-installation compared to web usage
- 30-day retention rate exceeds 60% for installed PWA users
- Push notification click-through rate achieves 20%+ engagement

**Technical Implementation Quality:**
- Service Worker implements sophisticated caching with cache-first, network-first strategies
- Background sync handles all offline operations with retry mechanisms
- IndexedDB storage includes automatic conflict resolution and data versioning
- Update management provides seamless updates with user notification and control

## 💡 USAGE EXAMPLES

**E-commerce PWA Implementation:**
```
PWA Features: Focus on offline cart, product browsing, payment integration
- Service Worker: Cache product catalog, offline cart persistence, payment queue
- Offline Storage: Product details, user preferences, shopping cart state
- Push Notifications: Order status, sale alerts, abandoned cart recovery
- Native Features: Camera for product scanning, payment request API, share functionality
- Background Sync: Order submission, inventory updates, wishlist synchronization
```

**Enterprise Dashboard PWA:**
```
PWA Features: Emphasize security, compliance, background sync, offline data access
- Service Worker: Secure caching with authentication, compliance data handling
- Offline Storage: Encrypted document storage, user roles, audit trails
- Push Notifications: System alerts, approval requests, security notifications
- Native Features: File system access, clipboard integration, wake lock for presentations
- Background Sync: Document synchronization, approval workflows, compliance reporting
```

**Healthcare Application PWA:**
```
PWA Features: Prioritize privacy, secure storage, offline forms, appointment notifications
- Service Worker: HIPAA-compliant caching, secure data transmission, offline forms
- Offline Storage: Encrypted patient data, appointment schedules, medical records
- Push Notifications: Appointment reminders, medication alerts, health tips
- Native Features: Camera for medical photos, geolocation for facility finder
- Background Sync: Appointment booking, medical record updates, prescription management
```

**Social Media PWA:**
```
PWA Features: Focus on content caching, share functionality, real-time notifications
- Service Worker: Content caching, image optimization, offline posting queue
- Offline Storage: User profiles, cached feeds, draft posts, media files
- Push Notifications: Social interactions, friend requests, trending content
- Native Features: Camera for content creation, web share for content distribution
- Background Sync: Post publishing, media uploads, social interactions
```

## 🔄 GitHub Copilot Workflow Integration

**Chatmode Coordination Patterns:**
- **@frontend-engineer** leads PWA architecture and service worker implementation
- **@security-engineer** consultation for secure offline storage and data protection
- **@performance-engineer** coordination for caching strategies and optimization
- **@ux-designer** collaboration for native-like user experience design

**Integration with GitHub Copilot IDE:**
- Intelligent service worker configuration based on project structure and requirements
- Automated PWA manifest generation with project-specific metadata and configuration
- Context-aware push notification setup with best practices and security considerations
- Real-time performance optimization suggestions for PWA metrics and user experience

---
*This prompt enables comprehensive Progressive Web App development with native-like experiences, advanced offline capabilities, and seamless device integration for all business domains and project scales.*