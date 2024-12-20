# External Libraries Integration for READMEs Programming System

This document outlines the process of importing and using external libraries within the READMEs Programming System, allowing seamless integration of existing code into the MDScript format.

📚 [Back to Main Documentation](Rdm_documentation.md)

## Table of Contents
- [Overview](#overview)
- [System Configuration](#system-configuration)
- [Import Process](#import-process)
- [Function Library](#function-library)
- [Usage Examples](#usage-examples)

## Overview

The READMEs Programming System supports importing external libraries from various programming languages, converting them into MDScript format for seamless integration with your documentation-as-code workflow.

## System Configuration

The system includes specialized parsers for different programming languages:

```yaml
version: 1.0
context: enabled
parser:
  #other parsers..
  python_function: ^def\s+(\w+)\s*\((.*?)\)
  js_function: ^(async\s+)?function\s+(\w+)\s*\((.*?)\)
  ts_function: ^(export\s+)?(async\s+)?function\s+(\w+)\s*\((.*?)\)
```

## Import Process

### Library Parser Patterns
The system uses language-specific patterns to parse external libraries and convert them into MDScript format.

### Supported Languages
- Python
- JavaScript
- TypeScript

### Import Function
```markdown
# system_import_library
  - description: Imports external library and converts to MDScript
  - parameters:
    - file_path: string
    - language: string  # "python"|"javascript"|"typescript"
  - returns:
    - md_library: string
```

## Usage Examples

### Python to MDScript Conversion
Original Python code:
```python
def format_text(text: str, style: str = "plain") -> str:
    return text.upper()
```

Converted MDScript:
```markdown
# format_text
  - description: Formats text
  - parameters:
    - text: string
    - style: string = "plain"
  - returns: string
```

### Import Template
To import an external library, use the following template:
```markdown
# Execute
  - function: system_import_library
  - parameters:
    - file_path: "./libraries/utils.py"
    - language: "python"
  - returns:
    - md_library: string
```

## Best Practices

1. **File Organization**: Keep external libraries in a dedicated `libraries` directory
2. **Documentation**: Ensure imported functions have proper descriptions and parameter documentation
3. **Version Control**: Track both original source files and converted MDScript files
4. **Testing**: Validate converted functions maintain their original behavior

By following these guidelines, you can effectively integrate external libraries into your READMEs Programming System while maintaining clean and consistent documentation.