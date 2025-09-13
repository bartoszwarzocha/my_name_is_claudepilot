# Szczegółowy Przewodnik Migracji Prompts → Copilot Prompt Files

## Dokumentacja Źródłowa

### Oficjalne zasoby Copilot Prompt Files:
- **Główna dokumentacja**: https://code.visualstudio.com/docs/copilot/customization/prompt-files
- **GitHub dokumentacja**: https://docs.github.com/en/copilot/tutorials/customization-library/prompt-files/document-api
- **Repozytorium przykładów**: https://github.com/github/awesome-copilot
- **Community prompts**: https://github.com/Code-and-Sorts/awesome-copilot-instructions

---

## Format Pliku Prompt

### Nazwa pliku:
```
{prompt-name}.prompt.md
```

### Struktura YAML Frontmatter:
```yaml
---
description: "Szczegółowy opis funkcji prompt w jednym zdaniu"
mode: "agent"
model: "claude-4-sonnet"
tools:
  - lista
  - dostępnych
  - narzędzi
---
```

### Wymagane pola:
- **description**: String - krótki opis funkcji prompt
- **model**: String - wybrany model AI
- **tools**: Array - lista dostępnych narzędzi

### Opcjonalne pola:
- **mode**: String - TYLKO podstawowe tryby (`agent`, `ask`, `edit`) - domyślnie `agent`
  - ⚠️ **WAŻNE**: NIE można używać nazw niestandardowych chatmodes!

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

## Dostępne Tryby (Mode)

### ⚠️ KRYTYCZNA INFORMACJA O POLU MODE

**BŁĘDNE ZAŁOŻENIE POCZĄTKOWE**: Pole `mode` NIE może odwoływać się do niestandardowych chatmodes!

### Akceptowane wartości dla pola `mode` (TYLKO podstawowe tryby):
```yaml
# Opcja 1 - domyślna (można pominąć):
mode: "agent"

# Opcja 2 - dla prostych pytań:
mode: "ask" 

# Opcja 3 - dla edycji kodu:
mode: "edit"
```

**NOWA REKOMENDACJA**: 
- **Pominąć pole `mode`** - domyślnie będzie `agent`
- **Połączenie z chatmodes** realizować przez instrukcje przejścia w treści prompta
- **NIE używać** nazw niestandardowych chatmodes w polu `mode`

---

## Dostępne Narzędzia (Tools)

### Kompletna lista narzędzi dla promptów:
```yaml
tools:
  - codebase          # Analiza całej bazy kodu
  - usages            # Znajdowanie użyć kodu
  - search            # Wyszukiwanie
  - findTestFiles     # Znajdowanie plików testowych
  - githubRepo        # Dostęp do repozytorium GitHub
  - fetch             # Pobieranie danych zewnętrznych
  - searchResults     # Wyniki wyszukiwania
  - vscodeAPI         # Dostęp do API VS Code
  - editFiles         # Edycja plików
  - runCommands       # Uruchamianie komend
  - runTasks          # Uruchamianie zadań
  - openSimpleBrowser # Otwieranie przeglądarki
```

### Rekomendacje narzędzi według typu promptu:

#### API Development Prompts:
```yaml
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
```

#### Frontend Development Prompts:
```yaml
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - runTasks
  - findTestFiles
  - search
```

#### Architecture Design Prompts:
```yaml
tools:
  - codebase
  - usages
  - vscodeAPI
  - searchResults
  - githubRepo
  - search
```

#### Security/Review Prompts:
```yaml
tools:
  - codebase
  - usages
  - vscodeAPI
  - searchResults
  - githubRepo
  - search
```

---

## Proces Migracji Krok po Kroku

### 1. Przygotowanie
- Przeczytaj oryginalny plik prompt z `.claude/prompts/`
- Zidentyfikuj główne funkcje i cele prompt
- Wybierz odpowiednie narzędzia dla typu prompt

### 2. Tworzenie YAML Frontmatter
```yaml
---
description: "Przepisz description z oryginalnego prompt, skróć do 1-2 zdań"
model: claude-4-sonnet  # lub GPT-4o, lub GPT-4.1
tools:
  - [wybierz z listy powyżej według typu prompt]
# mode: "agent"  # OPCJONALNE - domyślnie agent, lepiej pominąć
---
```

### 3. Adaptacja zawartości
- **Zmień referencje**: `CLAUDE.md` → `copilot.instructions.md`
- **Zachowaj wszystkie sekcje**: zadania, wymagania, przykłady, instrukcje
- **Dodaj referencje do chatmodes**: instrukcje przełączania
- **Zachowaj adaptacyjność**: automatyczne odczytywanie konfiguracji

### 4. Instrukcje przejść między chatmodes
Na końcu każdego prompt dodaj:
```markdown
## Transition to Specialized Chatmodes

After completing this task, switch to the appropriate specialized chatmode:

- **For [następny krok]**: Switch to **[Chatmode Name]** chatmode to [co robi]
- **For [alternatywny krok]**: Switch to **[Other Chatmode]** chatmode to [co robi]
```

### 5. Zmienne i parametry
Prompts mogą używać zmiennych:
```markdown
Focus on: ${input:focus_area:Specific area to concentrate on}
Target technology: ${input:technology:Technology stack to use}
```

---

## Przykład Kompletnej Migracji

### Oryginalny prompt (fragment):
```markdown
# REST API Design and Implementation

You are tasked with designing and implementing RESTful APIs...

**Context Adaptation**: Read CLAUDE.md to understand:
- Backend technologies and frameworks
- Business domain requirements
```

### Zmigrowany prompt:
```yaml
---
description: Design and implement RESTful APIs with best practices, security, and performance optimization. Adapts to project specifications defined in copilot.instructions.md.
model: claude-4-sonnet
tools:
  - codebase
  - usages
  - editFiles
  - runCommands
  - githubRepo
  - search
---

# REST API Design and Implementation

You are tasked with designing and implementing RESTful APIs...

**Context Adaptation**: Read copilot.instructions.md to understand:
- Backend technologies and frameworks
- Business domain requirements

## Transition to Specialized Chatmodes

After completing API design and implementation:

- **For Frontend Integration**: Switch to **frontend-engineer** chatmode to integrate with the implemented APIs
- **For Security Implementation**: Switch to **security-engineer** chatmode to implement API security controls
```

---

## Częste Błędy i jak ich Unikać

### ❌ Błędy w YAML:
- Nie używać niepoprawnych modeli (tylko claude-4-sonnet, GPT-4o, GPT-4.1)
- Nie zostawiać pustych narzędzi (zawsze dodać przynajmniej `codebase`, `search`)
- **KRYTYCZNE**: Nie używać nazw chatmodes w polu `mode` (tylko: agent, ask, edit)
- Lepiej całkowicie pominąć pole `mode` niż używać błędnych wartości

### ❌ Błędy w zawartości:
- Nie zmieniać `CLAUDE.md` na `copilot.instructions.md`
- Nie usuwać sekcji adaptacyjności
- Nie zapominać o instrukcjach przejść do chatmodes

### ❌ Błędy w narzędziach:
- Nie używać wszystkich narzędzi dla każdego prompt
- Wybierać narzędzia odpowiednie do funkcji prompt
- Nie zostawiać pustej listy tools

---

## Walidacja Poprawności

### Checklist przed zakończeniem migracji:
- [ ] YAML frontmatter ma 3 wymagane pola (description, model, tools)
- [ ] Model jest jednym z trzech dozwolonych (claude-4-sonnet, GPT-4o, GPT-4.1)
- [ ] **OPCJONALNE**: Pole mode używa TYLKO podstawowych trybów (`agent`, `ask`, `edit`) lub jest pominięte
- [ ] Tools zawiera odpowiednie narzędzia dla typu prompt (min. codebase, search)
- [ ] Wszystkie `CLAUDE.md` zmienione na `copilot.instructions.md`
- [ ] Zachowana sekcja adaptacyjności
- [ ] Dodane instrukcje przejść do chatmodes na końcu
- [ ] Description jest zwięzły i opisowy (1-2 zdania)
- [ ] ❌ **NIE używać** nazw chatmodes w polu mode!

---

## Struktura Zawartości Prompt

### Typowa struktura prompt:
```markdown
---
[YAML frontmatter]
---

# [Tytuł Prompt]

[Główny opis zadania i celu]

**Context Adaptation**: Read copilot.instructions.md to understand:
- [lista elementów adaptacyjnych]

## Task Description

[Szczegółowy opis zadania]

## Requirements

[Lista wymagań i ograniczeń]

## Implementation Guidelines

[Wytyczne implementacji]

## Examples

[Przykłady użycia]

## Validation Criteria

[Kryteria walidacji]

## Transition to Specialized Chatmodes

[Instrukcje przejść]
```

---

## Mapowanie Kategorii Promptów

### Oryginalny katalog → Docelowy katalog:
```
.claude/prompts/agents/api/          → .copilot/prompts/agents/api/
.claude/prompts/agents/architecture/ → .copilot/prompts/agents/architecture/
.claude/prompts/agents/business/     → .copilot/prompts/agents/business/
.claude/prompts/agents/data/         → .copilot/prompts/agents/data/
.claude/prompts/agents/deployment/   → .copilot/prompts/agents/deployment/
.claude/prompts/agents/design/       → .copilot/prompts/agents/design/
.claude/prompts/agents/frontend/     → .copilot/prompts/agents/frontend/
.claude/prompts/agents/product/      → .copilot/prompts/agents/product/
.claude/prompts/agents/qa/           → .copilot/prompts/agents/qa/
.claude/prompts/agents/quality/      → .copilot/prompts/agents/quality/
.claude/prompts/agents/review/       → .copilot/prompts/agents/review/
.claude/prompts/agents/security/     → .copilot/prompts/agents/security/
.claude/prompts/init/                → .copilot/prompts/init/
.claude/prompts/workflows/           → .copilot/prompts/workflows/
```

---

## Lokalizacja Plików

### Źródło:
```
.claude/prompts/**/*.md
```

### Cel:
```
.copilot/prompts/**/*.prompt.md
```

**WAŻNE**: Dodanie rozszerzenia `.prompt.md` jest obowiązkowe!

---

## Użycie Prompt Files

### Wywołanie prompt:
```
/prompt-name
```

### Wywołanie z parametrami:
```
/prompt-name focus_area="API security" technology="Node.js"
```

---

**WAŻNE**: Ten przewodnik zawiera wszystkie niezbędne informacje do samodzielnej migracji promptów do format Copilot prompt files bez konieczności ponownego researchu dokumentacji.