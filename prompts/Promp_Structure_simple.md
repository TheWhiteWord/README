[SYSTEM_INSTRUCTION]: "IMPORT_LIBRARY: library.md"

# Generate

- type: text
- length: 200
- topic: "The benefits of sustainable living"

## Transform

- input_data: "{{previous_output}}"
- function: summarize_text
- length: 70

### Analyze

- input: "{{previous_output}}"
- function: extract_keywords
- max_keywords: 5
- stop_words: "is, a, the, of, and"

# Define

- function: format_text
- input: "{{previous_output}}"
- style: italic
