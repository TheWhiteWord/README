# READMEs Programming System

## System Configuration

```yaml
version: 1.0
context: enabled
variables:
  readme_content: ""
  previous_output: ""
  system_state: ""
  topic: ""
parser:
  heading_section: ^##\s+(.+)$
  heading_function: ^#\s+(.+)$
  list_item: ^(\s+)-\s+(.+)$
  key_value: ^(\s+)-\s+(\w+):\s*(.+)$
  nested_list: ^(\s+)-\s+(\w+):$
  indentation: 2
```

## Parser Implementation

```javascript
const parseLibrary = md => md.match(/^#\s+(.+)$/gm)
const parseTemplate = md => md.match(/^###\s+(.+)$/gm)
const parseContext = md => JSON.parse(md.match(/\{[\s\S]+\}/m)[0])
```

## Function Library

```md
# system_init
  - description: Bootstrap system from README
  - parameters:
    - content: string
  - returns:
    - system_state: ready
    - functions: loaded
    - templates: parsed

# system_execute
  - description: Run template with context
  - parameters:
    - template: string
    - input: string
    - context: object

# system_compose_program
  - description: Generates a composed program with the defined functions
  - parameters:
    - libraries: [string]
    - readme_content: string
  - returns:
    - composed_program: string
```
## Execution Context

```json
{
  "previous_output": "",
  "variables": {},
  "state": "ready"
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

## Composing the Program

```md
# Execute
  - function: system_compose_program
  - libraries:
    - my_first_library.md
    - Text_augementation_library.md
  - readme_content: "{{readme_content}}"
```

## Help Documentation
