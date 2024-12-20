# READMEs Programming System Documentation

## Table of Contents
- [Overview](#overview)
- [Core Concepts](#core-concepts)
- [System Architecture](#system-architecture)
- [Getting Started](#getting-started)
- [Function Library](#function-library)
- [Examples](#examples)
- [Advanced Features](#advanced-features)
- [Best Practices](#best-practices)

## Overview

READMEs is a revolutionary programming system that uses README.md files as both documentation and executable code. It leverages the power of Large Language Models (LLMs) to create a structured programming environment using familiar Markdown syntax.

### Key Benefits

- **Single Source of Truth**: README.md serves as both documentation and code
- **Natural Language Integration**: Seamless interaction with LLMs
- **Version Control Friendly**: Built on Git-compatible Markdown
- **Low Learning Curve**: Uses widely understood Markdown syntax
- **Self-Documenting**: Examples are executable and always up-to-date

## Core Concepts

### The README as Code

```yaml
version: 1.0
context: enabled
variables:
  readme_content: ""
  previous_output: ""
  system_state: ""
```

Your README.md file becomes a functional program through:
1. Function definitions using structured Markdown
2. Program templates for common operations
3. Metadata sections for system configuration
4. Live examples that serve as both documentation and code

### Function Structure

```mdscript
# Define Function: example_function
- description: What the function does
- parameters:
  - input: string
  - length: number
- returns: string
```

## System Architecture

### Core Components

1. **Parser System**
   - Processes Markdown structures
   - Extracts function definitions
   - Manages program context

2. **Execution Engine**
   - Interfaces with LLMs
   - Manages state through Git
   - Handles function calls

3. **Context Management**
   - Variables like `{{previous_output}}`
   - Git-based state persistence
   - Template resolution

## Getting Started

### Basic Setup

1. Create a new README.md:
```markdown
# My First Program

## Configuration
```yaml
version: 1.0
functions:
  - generate_text
  - summarize_text
```

## Function Library
```

### Built-in Functions

1. `generate_text`
   ```mdscript
   # Generate
   - type: text
   - length: 100
   - topic: "AI and the future"
   ```

2. `summarize_text`
   ```mdscript
   # Transform
   - input: "{{previous_output}}"
   - function: summarize_text
   - length: 50
   ```

## Examples

### Simple Text Generation

```mdscript
# Generate
- type: text
- length: 100
- topic: "AI programming"

## Transform
- input: "{{previous_output}}"
- function: summarize_text
- length: 50
```

### Advanced Template Usage

```mdscript
# Program Templates

## Analysis Template
- input: "{{input_text}}"
- steps:
  - extract_keywords
  - format_text
  - summarize_text
```

## Advanced Features

### Git Integration

- State management through commits
- Branch-based program variations
- Version control for templates

### Template System

```yaml
templates:
  - quick_start
  - analysis
  - documentation
```

### Web Components

- README as API endpoint
- WebSocket updates
- Browser-based execution

## Best Practices

1. **Structure**
   - Use clear hierarchical headings
   - Group related functions
   - Include examples with outputs

2. **Context Management**
   - Use explicit variable names
   - Document state changes
   - Maintain clear data flow

3. **Version Control**
   - Commit meaningful states
   - Use branches for variations
   - Tag stable versions

4. **Documentation**
   - Include live examples
   - Document parameters
   - Show expected outputs

## Reference

### System Variables
- `{{readme_content}}`: Current README content
- `{{previous_output}}`: Last operation result
- `{{system_state}}`: Current system state

### Function Parameters
- `input`: Input text for processing
- `length`: Output length control
- `style`: Formatting options

## Contributing

1. Fork the repository
2. Create a feature branch
3. Update the README.md with new functions/examples
4. Submit a pull request

## Future Development

- Enhanced template system
- IDE integration
- Custom LLM backends
- Extended function library

---

For more information, see:
- [Implementation Details](Rdm_implementation.md)
- [System Configuration](README.md)
- [Examples](examples/)
