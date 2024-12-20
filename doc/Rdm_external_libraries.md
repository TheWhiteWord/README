# Importing External Libraries

1. Create library parser patterns
2. Define language-specific parsers
3. Add import template
4. Update system functions

```markdown
## System Configuration
```yaml
version: 1.0
context: enabled
parser:
  ...existing patterns...
  python_function: ^def\s+(\w+)\s*\((.*?)\)
  js_function: ^(async\s+)?function\s+(\w+)\s*\((.*?)\)
  ts_function: ^(export\s+)?(async\s+)?function\s+(\w+)\s*\((.*?)\)
```

## Function Library
```md
## CORE
...existing functions...

# system_import_library
  - description: Imports external library and converts to MDScript
  - parameters:
    - file_path: string
    - language: string  # "python"|"javascript"|"typescript"
  - returns:
    - md_library: string
```

## Program Templates

### Import External Library
# Execute
  - function: system_import_library
  - parameters:
    - file_path: "./libraries/utils.py"
    - language: "python"
  - returns:
    - md_library: string
```

Example Python -> MDScript conversion:
```python
def format_text(text: str, style: str = "plain") -> str:
    return text.upper()
```
↓ Converts to ↓
```markdown
# format_text
  - description: Formats text
  - parameters:
    - text: string
    - style: string = "plain"
  - returns: string
```