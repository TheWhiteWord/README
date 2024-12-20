# READMEs Programming System - Initial Setup

## System Configuration
```yaml
version: 1.0
context: enabled
variables:
  readme_content: ""
  previous_output: ""
  system_state: ""
  topic: ""
  initial_output: "### Welcome to the READMEs Programming System!\n\n Write your input here"
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

# system_display_output
  - description: Displays the output string.
  - parameters:
    - output: string
  - returns:
    - output: string

## Execution Context

```json
{
  "previous_output": "",
  "variables": {},
  "state": "ready"
}
```

## Program Execution

### Display Output
```mdscript
# Execute
 - function: system_display_output
 - output: "{{initial_output}}"
```

### Bootstrap

# Execute
  - function: system_init
  - input: "{{readme_content}}"
  - outputs:
    - system_state
    - functions
    - templates

## Composing the Program

# Execute
  - function: system_compose_program
  - libraries:
    - my_first_library.md
    - Text_augementation_library.md
  - readme_content: "{{readme_content}}"

## Help Documentation
# READMEs Programming System - Initial Setup

## System Configuration
```yaml
version: 1.0
context: enabled
variables:
  readme_content: ""
  previous_output: ""
  system_state: ""
  topic: ""
  initial_output: "### Welcome to the READMEs Programming System!\n\nPlease compose your program by running the 'Composing the Program' section."
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

  # Execute
    - function: system_init
    - input: "{{readme_content}}"
    - outputs:
      - system_state
      - functions
      - templates

  ## Composing the Program

  # Execute
    - function: system_compose_program
    - libraries:
      - my_first_library.md
      - Text_augementation_library.md
    - readme_content: "{{readme_content}}"

  ## Help Documentation
