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

## Execution Context

```json
{
  "previous_output": "",
  "variables": {},
  "state": "ready"
}
```

## Help Documentation
