# Zasady Migracji do GitHub Copilot - My Name Is ClaudePilot

## Meta Informacje
- **Data utworzenia**: 2025-09-13
- **Wersja**: 1.0.0
- **Dotyczy**: Wszystkich kolejnych migracji z Claude Code na GitHub Copilot
- **Status**: Obowiązujące standardy migracji

---

## 1. Filozofia Migracji

### Copilot-First Approach
- **NIE przenosimy mechanicznie** rozwiązań z Claude Code
- **Przepisujemy od nowa** rozwiązania zoptymalizowane pod GitHub Copilot
- **Wykorzystujemy mocne strony** GitHub Copilot (code completion, context awareness, GitHub integration)
- **Uwzględniamy ograniczenia** GitHub Copilot vs Claude Code

### Jakość nad Szybkością
- **Zawsze zachowujemy najwyższą jakość** - "żadnego skracania!"
- **Pełne implementacje technologiczne** dla wszystkich wspieranych języków
- **Komprehensywne przykłady kodu** z enterprise-grade standards
- **Szczegółowe instrukcje przejść** między chatmodes

---

## 2. Struktura Promptów GitHub Copilot

### Obowiązkowy Header YAML
```yaml
---
name: prompt-name
description: Brief, specific description of what this prompt does
tools: [list, of, copilot, tools, and, integrations]
model: github-copilot
context_adaptation: true
---
```

### Sekcje Prompta (Standardowa Struktura)
1. **Context Analysis Framework** - Czytanie `copilot.instructions.md`
2. **Technology Detection & Adaptation** - Auto-detection tech stack
3. **Core Implementation Patterns** - Główne wzorce dla każdego języka
4. **GitHub Integration Points** - Issues, PRs, Actions, Projects
5. **Code Generation Templates** - Gotowe templates do użycia
6. **Quality Gates & Standards** - Standardy jakości i bezpieczeństwa
7. **Transition Guidance** - Przejścia do innych chatmodes
8. **Examples & Use Cases** - Praktyczne przykłady użycia

---

## 3. Technology-Adaptive Implementation

### Wspierane Technologie (Wszystkie Równoważne)
- **Frontend**: React, Angular, Vue.js + TypeScript/JavaScript
- **Backend**: Node.js/Express, Python/FastAPI, Java/Spring Boot, .NET Core, Go, Rust
- **Mobile**: React Native, Flutter, Swift, Kotlin
- **Desktop**: Electron, Tauri, .NET MAUI, WPF, Qt, wxWidgets
- **Database**: PostgreSQL, MySQL, MongoDB, Redis, Elasticsearch
- **Cloud**: AWS, Azure, GCP + Terraform, Pulumi
- **DevOps**: Docker, Kubernetes, GitHub Actions, Jenkins

### Wzorce Adaptacyjne
```markdown
## Technology Detection
The prompt automatically detects project technology stack by analyzing:
- `package.json`, `requirements.txt`, `pom.xml`, `*.csproj`, `go.mod`, `Cargo.toml`
- Existing code patterns and framework usage
- `copilot.instructions.md` technology specifications
```

---

## 4. GitHub Copilot Specyficzne Optimizacje

### Code Completion Enhancement
- **Kontekstowe sugestie** oparte na aktualnym kodzie
- **Multi-file awareness** - uwzględnienie związanych plików
- **Pattern recognition** - rozpoznawanie wzorców projektowych

### GitHub Integration
- **Issues & PRs**: Automatyczne linkowanie do zadań
- **Actions Integration**: CI/CD workflow suggestions
- **Project Management**: GitHub Projects integration
- **Code Review**: PR review automation suggestions

### IDE Enhancement
- **IntelliSense Enhancement**: Lepsze sugestie w IDE
- **Error Prevention**: Proaktywne wykrywanie błędów
- **Refactoring Assistance**: Inteligentne refactoring suggestions

---

## 5. Różnice Claude Code vs GitHub Copilot

### Co USUWAMY z Claude Code Promptów
- **Tool-specific instructions** (Bash, Read, Write, Edit) - Copilot ma inne narzędzia
- **File system operations** - Copilot działa inaczej z plikami
- **Complex orchestration** - Copilot jest bardziej focused na kod
- **Multi-step automation** - Copilot preferuje atomic operations

### Co DODAJEMY dla GitHub Copilot
- **Code completion contexts** - Konteksty dla lepszych sugestii
- **GitHub workflow integration** - Integracja z GitHub workflow
- **IDE-specific optimizations** - Optymalizacje pod konkretne IDE
- **Real-time collaboration** - Wsparcie dla team collaboration

### Co ADAPTUJEMY
- **Chatmode transitions** → **Context switching guidance**
- **File operations** → **Code generation patterns**
- **Complex workflows** → **Step-by-step code guidance**
- **Tool orchestration** → **GitHub ecosystem integration**

---

## 6. Standardy Jakości

### Code Generation Standards
- **Production-ready code** - Kod gotowy do produkcji
- **Enterprise security** - OWASP, NIST compliance
- **Performance optimized** - Wydajność i skalowność
- **Test coverage** - Uwzględnienie testów
- **Documentation** - Automatyczna dokumentacja

### Technology Standards
- **Type safety** - TypeScript, strong typing gdzie możliwe
- **Error handling** - Comprehensive error handling patterns
- **Logging & monitoring** - Structured logging, metrics
- **Configuration** - Environment-based configuration
- **Deployment readiness** - Docker, CI/CD ready

---

## 7. Prompt Engineering Best Practices

### Struktura Instrukcji
1. **Clear objective** - Jasny cel prompta
2. **Context requirements** - Wymagane informacje kontekstowe
3. **Step-by-step guidance** - Krok po kroku instrukcje
4. **Technology adaptations** - Adaptacje technologiczne
5. **Quality checkpoints** - Punkty kontroli jakości
6. **Next steps guidance** - Wskazówki kolejnych kroków

### Przykłady vs Templates
- **Zawsze pełne przykłady** - Kompletny, działający kod
- **Template patterns** - Gotowe wzorce do użycia
- **Configuration examples** - Przykłady konfiguracji
- **Test patterns** - Wzorce testowe

---

## 8. Migration Checklist Template

Dla każdego migrowanego prompta:

### Pre-Migration Analysis
- [ ] Przeanalizuj oryginalny prompt Claude Code
- [ ] Zidentyfikuj elementy specyficzne dla Claude Code do usunięcia
- [ ] Określ optimizacje specyficzne dla GitHub Copilot
- [ ] Sprawdź zgodność z `copilot.instructions.md`

### Migration Execution
- [ ] Utwórz nowy prompt z YAML header
- [ ] Zaimplementuj Context Analysis Framework
- [ ] Dodaj Technology Detection & Adaptation
- [ ] Przepisz implementacje dla wszystkich języków
- [ ] Dodaj GitHub Integration Points
- [ ] Utwórz Code Generation Templates
- [ ] Dodaj Quality Gates & Standards
- [ ] Zaimplementuj Transition Guidance
- [ ] Dodaj Examples & Use Cases

### Post-Migration Validation
- [ ] Sprawdź wszystkie przykłady kodu
- [ ] Zweryfikuj technology adaptations
- [ ] Przetestuj transition guidance
- [ ] Sprawdź zgodność z enterprise standards
- [ ] Waliduj GitHub integration points

---

## 9. Specific Technology Guidelines

### Frontend (React/Angular/Vue)
- **Component patterns** - Functional components, hooks, composition
- **State management** - Redux, Zustand, Pinia patterns
- **Styling** - CSS-in-JS, Tailwind, styled-components
- **Testing** - Jest, Testing Library, Cypress

### Backend (Node.js/Python/Java/.NET)
- **API patterns** - REST, GraphQL, gRPC
- **Database integration** - ORM patterns, connection pooling
- **Authentication** - JWT, OAuth2, RBAC
- **Monitoring** - Structured logging, metrics, health checks

### DevOps & Infrastructure
- **Containerization** - Multi-stage builds, security scanning
- **CI/CD** - GitHub Actions workflows, deployment strategies
- **Infrastructure** - Terraform modules, environment management
- **Monitoring** - Observability patterns, alerting

---

## 10. Maintenance & Evolution

### Regular Updates
- **Technology trends** - Aktualizacja do najnowszych wzorców
- **GitHub Copilot features** - Wykorzystanie nowych funkcji
- **Community feedback** - Uwzględnienie feedback od społeczności
- **Security updates** - Aktualizacja security best practices

### Quality Assurance
- **Peer review** - Review wszystkich migracji
- **Testing** - Test wszystkich przykładów kodu
- **Documentation** - Aktualna dokumentacja
- **Version control** - Proper versioning strategy

---

**WAŻNE**: Te zasady obowiązują dla WSZYSTKICH kolejnych migracji. Każda migracja musi przejść przez ten framework aby zapewnić najwyższą jakość i optimizację pod GitHub Copilot.

*Dokument będzie aktualizowany wraz z rozwojem projektu i pojawianiem się nowych best practices dla GitHub Copilot.*