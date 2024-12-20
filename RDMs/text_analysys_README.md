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
## CORE

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
  - description: Generates a composed program by combining README.md with custom libraries
  - parameters:
    - readme_file: string
    - libraries: [string]
  - returns:
    - composed_readme: string
    - execution_state: ready

## CUSTOM

# format_text
  - description: Formats text according to style
  - parameters:
    - input: string
    - style:
      - plain
      - bold 
      - italic
    - uppercase: boolean

# summarize_text
  - description: Summarizes input text
  - parameters:
    - input: string
    - length: number

# extract_keywords
  - description: Extracts keywords from text
  - parameters:
    - input: string
    - max_keywords: number
    - stop_words:
      - the
      - and
      - is
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

#### CUSTOM  

### Text Analysis
# Execute
  - function: system_execute
  - template: text_analysis_pipeline
  - input: "{{input_text}}"
  - context: "{{system_state}}"
```

### Text Analysis Pipeline

```md
# Generate
   - type: text
   - length: 100
   - topic: "{{topic}}"

## Transform
   - input: "{{previous_output}}"
   - function: summarize_text
   - length: 50

### Analyze
   - input: "{{previous_output}}"
   - function: extract_keywords
   - max_keywords: 3
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

## Program Composition

```md
# Execute
  - function: system_compose_program
  - libraries:
    - my_first_library.md
  - readme_content: "{{readme_content}}"
```

## Help Documentation
