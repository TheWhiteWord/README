# READMEs Programming System

An innovative programming system using README.md files as both documentation and executable code, optimized for LLM interaction.

## Quick Links
- [Documentation](doc/Rdm_documentation.md)
- [Git Integration](doc/Rdm_git.md)
- [External Libraries](doc/Rdm_external_libraries.md)

## System Configuration

```yaml
version: 1.0
context: enabled
variables:
  readme_content: ""
  previous_output: ""
  system_state: ""
  topic: ""
  llm_context: enabled
  git_integration: enabled
parser:
  heading_section: ^##\s+(.+)$
  heading_function: ^#\s+(.+)$
  list_item: ^(\s+)-\s+(.+)$
  key_value: ^(\s+)-\s+(\w+):\s*(.+)$
  nested_list: ^(\s+)-\s+(\w+):$
  indentation: 2
llm_settings:
  context_depth: 3
  branch_awareness: true
  cross_reference: enabled
```

## Parser Implementation

```javascript
const parseLibrary = md => md.match(/^#\s+(.+)$/gm)
const parseTemplate = md => md.match(/^###\s+(.+)$/gm)
const parseContext = md => JSON.parse(md.match(/\{[\s\S]+\}/m)[0])
```

## Function Library

```md
## CORE

# system_init
  - description: Bootstrap system from README with LLM context
  - parameters:
    - content: string
    - llm_context: object
  - returns:
    - system_state: ready
    - functions: loaded
    - templates: parsed
    - llm_context: initialized

# system_execute
  - description: Run template with context
  - parameters:
    - template: string
    - input: string
    - context: object

# system_compose_program
  - description: Generates a composed program by combining README.md with custom libraries
  - parameters:
    - readme_file: string
    - libraries: [string]
  - returns:
    - composed_readme: string
    - execution_state: ready

## LLM Integration

# llm_context_switch
  - description: Switch LLM context based on Git branch or documentation section
  - parameters:
    - context_type: "git"|"doc"
    - context_id: string
  - returns:
    - new_context: object

# llm_reference_resolver
  - description: Resolve cross-references in documentation for LLM
  - parameters:
    - reference: string
    - context: object
  - returns:
    - resolved_content: string

## CUSTOM
```

# Program Templates

```md
### Bootstrap
# Execute
  - function: system_init
  - input: "{{readme_content}}"
  - outputs:
    - system_state
    - functions
    - templates

### Program Composing
# Execute
  - function: system_compose_program
  - libraries:
    - my_first_library.md
  - readme_content: "{{readme_content}}"

```

## Execution Context

```json
{
  "previous_output": "",
  "variables": {},
  "state": "ready",
  "llm_context": {
    "current_branch": "main",
    "doc_section": "root",
    "reference_depth": 0
  }
}
```

## Program Execution

### Bootstrap

```md
# Execute
  - function: system_init
  - input: "{{readme_content}}"
  - outputs:
    - system_state
    - functions
    - templates
```

## Program Composition

```md
# Execute
  - function: system_compose_program
  - libraries:
    - my_first_library.md
  - readme_content: "{{readme_content}}"
```

## LLM Interaction Guide

For optimal LLM interaction, use:
- Internal links: [Function Library](#function-library)
- Git branches for context switching
- Cross-references between documentation files
- Structured metadata in YAML format

See [Documentation](doc/Rdm_documentation.md) for detailed usage.
