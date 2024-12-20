**Menu:**

```markdown
# Menu

- # Generate

  - type: text
  - length: 100
  - topic: "AI and the future of work"

- # Transform

  - input: "{{previous_output}}"
  - function: summarize_text
  - length: 50

- # Analyze

  - input: "{{previous_output}}"
  - function: extract_keywords
  - max_keywords: 3
```

```markdown
**Help:**
```

```markdown
# Help
```

```markdown
**Previous Output:**
```

```markdown
# Generate:
     - type: text
     - length: 100
     - topic: "AI and the future of work"

## Transform:
    - input: "{{previous_output}}"
    - function: summarize_text
    - length: 50

### Analyze:
    - input: "{{previous_output}}"
    - function: extract_keywords
    - max_keywords: 3

# Define:
  - function: format_text
  - input: "{{previous_output}}"
  - style: italic
  
```