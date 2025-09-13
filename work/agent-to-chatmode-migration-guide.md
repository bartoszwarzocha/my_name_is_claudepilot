# Szczegółowy Przewodnik Migracji Agent → Chatmode

## Dokumentacja Źródłowa

### Oficjalne zasoby Copilot:
- **Główna dokumentacja**: https://code.visualstudio.com/docs/copilot/customization/custom-chat-modes
- **Repozytorium przykładów**: https://github.com/github/awesome-copilot
- **Przykład implementation-plan**: https://github.com/github/awesome-copilot/blob/main/chatmodes/implementation-plan.chatmode.md
- **Community chatmodes**: https://github.com/dfinke/awesome-copilot-chatmodes

---

## Format Pliku Chatmode

### Nazwa pliku:
```
{agent-name}.chatmode.md
```

### Struktura YAML Frontmatter:
```yaml
---
description: "Szczegółowy opis funkcji chatmode w jednym zdaniu"
tools:
  - lista
  - dostępnych
  - narzędzi
model: wybór-modelu
---
```

### Wymagane pola:
- **description**: String - krótki opis funkcji chatmode
- **tools**: Array - lista dostępnych narzędzi
- **model**: String - wybrany model AI

### Pola NIEDOZWOLONE:
- ❌ `name` - usunąć z YAML (nie jest potrzebne)
- ❌ `title` - nie używać
- ❌ `version` - nie używać

---

## Dostępne Modele

### Akceptowane wartości dla pola `model`:
```yaml
# Opcja 1:
model: claude-4-sonnet

# Opcja 2:
model: GPT-4o

# Opcja 3:
model: GPT-4.1
```

**WAŻNE**: Używać wyłącznie tych trzech opcji!

---

## Dostępne Narzędzia (Tools)

### Kompletna lista narzędzi z implementation-plan.chatmode.md:
```yaml
tools:
  - codebase          # Analiza całej bazy kodu
  - usages            # Znajdowanie użyć kodu
  - vscodeAPI         # Dostęp do API VS Code
  - think             # Tryb myślenia/analizy
  - problems          # Dostęp do problemów w kodzie
  - changes           # Śledzenie zmian
  - testFailure       # Informacje o nieudanych testach
  - terminalSelection # Wybór z terminala
  - terminalLastCommand # Ostatnia komenda z terminala
  - openSimpleBrowser # Otwieranie przeglądarki
  - fetch             # Pobieranie danych zewnętrznych
  - findTestFiles     # Znajdowanie plików testowych
  - searchResults     # Wyniki wyszukiwania
  - githubRepo        # Dostęp do repozytorium GitHub
  - extensions        # Dostęp do rozszerzeń VS Code
  - editFiles         # Edycja plików
  - runNotebooks      # Uruchamianie notebooków
  - search            # Wyszukiwanie
  - new               # Tworzenie nowych elementów
  - runCommands       # Uruchamianie komend
  - runTasks          # Uruchamianie zadań
```

### Rekomendacje narzędzi według typu agenta:

#### Business Analyst:
```yaml
tools:
  - codebase
  - search
  - usages
  - githubRepo
  - findTestFiles
  - fetch
  - problems
  - searchResults
  - vscodeAPI
```

#### Software Architect:
```yaml
tools:
  - codebase
  - usages
  - vscodeAPI
  - problems
  - changes
  - findTestFiles
  - searchResults
  - githubRepo
  - extensions
  - search
```

#### Frontend/Backend Engineer:
```yaml
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - runTasks
  - problems
  - changes
  - testFailure
  - findTestFiles
  - githubRepo
  - search
```

#### Security Engineer:
```yaml
tools:
  - codebase
  - usages
  - vscodeAPI
  - problems
  - changes
  - searchResults
  - githubRepo
  - extensions
  - fetch
  - search
```

#### QA Engineer:
```yaml
tools:
  - codebase
  - usages
  - findTestFiles
  - testFailure
  - runCommands
  - runTasks
  - problems
  - changes
  - githubRepo
  - search
```

---

## Proces Migracji Krok po Kroku

### 1. Przygotowanie
- Przeczytaj oryginalny plik agenta z `.claude/agents/`
- Zidentyfikuj główne funkcje i kompetencje agenta
- Wybierz odpowiednie narzędzia dla typu agenta

### 2. Tworzenie YAML Frontmatter
```yaml
---
description: "Przepisz description z oryginalnego agenta, skróć do 1-2 zdań"
tools:
  - [wybierz z listy powyżej według typu agenta]
model: claude-4-sonnet  # lub GPT-4o, lub GPT-4.1
---
```

### 3. Adaptacja zawartości
- **Zmień referencje**: `CLAUDE.md` → `copilot.instructions.md`
- **Zachowaj wszystkie sekcje**: philosophy, competencies, specializations
- **Dodaj sekcję przejść**: instrukcje przełączania na inne chatmodes
- **Zachowaj adaptacyjność**: automatyczne odczytywanie konfiguracji

### 4. Instrukcje przejść między chatmodes
Na końcu każdego chatmode dodaj:
```markdown
## Transition Instructions

After completing [typ pracy], recommend switching to the appropriate specialized chatmode:

- **For [następny krok]**: "Switch to **[Chatmode Name]** chatmode to [co robi]"
- **For [alternatywny krok]**: "Switch to **[Other Chatmode]** chatmode to [co robi]"
```

### 5. Dependency Order dla przejść
```
Business Analyst → Software Architect/UX Designer
Software Architect → Frontend/Backend/Data/Security/Deployment/QA Engineers
UX Designer → Frontend Engineer
Product Manager → wszystkie inne
Reviewer → ostatni (weryfikuje wszystko)
```

---

## Przykład Kompletnej Migracji

### Oryginalny agent (fragment):
```yaml
---
name: business-analyst
description: Senior business analyst specializing in requirements gathering...
---
```

### Zmigrowany chatmode:
```yaml
---
description: Senior business analyst specializing in requirements gathering, process modeling, and stakeholder management for enterprise software projects. Adapts to project specifications defined in copilot.instructions.md.
tools:
  - codebase
  - search
  - usages
  - githubRepo
  - findTestFiles
  - fetch
  - problems
  - searchResults
  - vscodeAPI
model: claude-4-sonnet
---
```

---

## Częste Błędy i jak ich Unikać

### ❌ Błędy w YAML:
- Nie dodawać pola `name`
- Nie używać niepoprawnych modeli
- Nie zostawiać pustych narzędzi (zawsze dodać przynajmniej `codebase`, `search`)

### ❌ Błędy w zawartości:
- Nie zmieniać `CLAUDE.md` na `copilot.instructions.md`
- Nie usuwać sekcji adaptacyjności
- Nie zapominać o instrukcjach przejść

### ❌ Błędy w narzędziach:
- Nie używać wszystkich narzędzi dla każdego agenta
- Wybierać narzędzia odpowiednie do funkcji agenta
- Nie zostawiać pustej listy tools

---

## Walidacja Poprawności

### Checklist przed zakończeniem migracji:
- [ ] YAML frontmatter ma wszystkie 3 wymagane pola
- [ ] Model jest jednym z trzech dozwolonych
- [ ] Tools zawiera odpowiednie narzędzia dla typu agenta
- [ ] Wszystkie `CLAUDE.md` zmienione na `copilot.instructions.md`
- [ ] Zachowana sekcja adaptacyjności
- [ ] Dodane instrukcje przejść na końcu
- [ ] Brak pola `name` w YAML
- [ ] Description jest zwięzły i opisowy

---

## Lokalizacja Plików

### Źródło:
```
.claude/agents/{kategoria}/{agent-name}.md
```

### Cel:
```
.copilot/chatmodes/{agent-name}.chatmode.md
```

---

**WAŻNE**: Ten przewodnik zawiera wszystkie niezbędne informacje do samodzielnej migracji agentów do chatmodes bez konieczności ponownego researchu dokumentacji.