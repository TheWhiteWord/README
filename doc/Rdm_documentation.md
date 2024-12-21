# READMEs Programming System Documentation

!!! IMPORTANT NOTICE: this project is 'work in progress' and not all features are implemented, this doc serves as a roadmap too.

## Quick Links
📘 System Docs:
- [Documentation Standards](Rdm_standards.md)
- [Implementation Details](Rdm_implementation.md)
- [Testing Guide](Rdm_testing.md)
- [Git Integration](Rdm_git.md)
- [External Libraries](Rdm_external_libraries.md)

## Table of Contents
- [System Overview](#system-overview)
- [LLM Integration](#llm-integration)
- [Core Components](#core-components)
- [Getting Started](#getting-started)
- [Function Reference](#function-reference)
- [Advanced Usage](#advanced-usage)

## System Overview

READMEs is a programming system using README.md files as executable documentation with LLM integration.

### Key Features
- README.md as executable code
- LLM-powered processing
- Git-compatible
- Built-in testing framework
- External library support

## LLM Integration

### Processing Protocol
```yaml
llm_features:
  navigation:
    warmhole_links: enabled  # Direct knowledge jumps
    context_depth: 3
    state_tracking: enabled
  
  optimization:
    priority_sections: ["config", "examples", "state"]
    context_switches: minimal
```

### Context Management
```markdown
# Context Rules
- preserve_context: true
- state_tracking: enabled
- warmhole_navigation: enabled
```

### Document Structure
Follow [Documentation Standards](Rdm_standards.md#document-structure) for:
- File organization
- Section hierarchy
- Code block formatting
- Cross-referencing

## Core Components

### System Configuration
```yaml
version: 1.0
context: enabled
variables:
  readme_content: ""
  previous_output: ""
  system_state: ""
```

### Basic Function Structure
```mdscript
# Define Function: example_function
- description: What the function does
- parameters:
  - input: string
  - length: number
- returns: string
```

### State Management
```markdown
# State Features
- context_preservation: enabled
- state_tracking: active
- git_integration: enabled
```

## Getting Started

### Quick Start
```markdown
# My First Program

## Configuration
```yaml
version: 1.0
functions:
  - generate_text
  - summarize_text
```

### Basic Functions
1. `generate_text`: Create new content
2. `summarize_text`: Transform existing content
3. `format_text`: Style output

## Function Reference

### System Variables
- `{{readme_content}}`: Current document
- `{{previous_output}}`: Last result
- `{{system_state}}`: System context

### Core Functions
```mdscript
# Generate
- type: text
- length: 100
- topic: "example"

# Transform
- input: "{{previous_output}}"
- function: summarize_text
```

## Advanced Usage

### Templates
```mdscript
# Program Templates
## Analysis Template
- input: "{{input_text}}"
- steps:
  - extract_keywords
  - format_text
  - summarize_text
```

### Integration Points
- Git workflow: See [Git Guide](Rdm_git.md)
- External libraries: See [Libraries Guide](Rdm_external_libraries.md)
- Testing framework: See [Testing Guide](Rdm_testing.md)

### Context Navigation
1. Use warmhole links for direct jumps
2. Maintain state across documents
3. Follow [standards guidelines](Rdm_standards.md#llm-navigation-guide)

### Best Practices
1. Follow [documentation standards](Rdm_standards.md#best-practices)
2. Use proper [state management](Rdm_standards.md#state-tracking)
3. Implement [LLM protocols](Rdm_standards.md#llm-processing-protocol)
4. Maintain [context integrity](Rdm_standards.md#context-assessment)

## Contributing
See [Git Integration Guide](Rdm_git.md#contributing)

---
📝 See [Documentation Standards](Rdm_standards.md) for detailed guidelines
