# "*READMEs*" How It Works: Building Programs with Markdown-Based Language

This documentation describes a system for creating programs using a Markdown-based language that interfaces with LLMs (Large Language Models). The system provides a structured approach to text processing and generation through reusable functions and clear workflow patterns.

## Core Components

### Files

- [`my_first_library.md`](#my_first_librarymd): Contains reusable text processing functions
- [`System Install.md`](#system-installmd): Initial setup file for system configuration
- [`Prompt_Structure_with_Menu.md`](#prompt_structure_with_menumd): Main program structure file
- [`library.md`](#librarymd): Function definitions and documentation

### Key Features

- ["*READMEs*" How It Works: Building Programs with Markdown-Based Language](#READMEs-how-it-works-building-programs-with-markdown-based-language)
  - [Core Components](#core-components)
    - [Files](#files)
    - [Key Features](#key-features)
  - [System Advantages](#system-advantages)
    - [Compared to Traditional Prompting](#compared-to-traditional-prompting)
    - [Compared to Complex Programming Languages](#compared-to-complex-programming-languages)
  - [Usage Instructions](#usage-instructions)
    - [Basic Workflow](#basic-workflow)
    - [Available Functions](#available-functions)
    - [Context Management](#context-management)
  - [Implementation Notes](#implementation-notes)
  - [Future Development Focus](#future-development-focus)
- [Menu:](#menu)
- [Help:](#help)
    - [`format_text`](#format_text)
    - [`summarize_text`](#summarize_text)
    - [`extract_keywords`](#extract_keywords)
- [Generate](#generate)
  - [Transform](#transform)
    - [Analyze](#analyze)
- [Define](#define)
- [Important Note on Indentation](#important-note-on-indentation)

## System Advantages

### Compared to Traditional Prompting

- [Structured approach with explicit steps](#structured-approach-with-explicit-steps)
- [Reusable components](#reusable-components)
- [Clear parameter control](#clear-parameter-control)
- [Transparent context management](#transparent-context-management)
- [Version control friendly](#version-control-friendly)

### Compared to Complex Programming Languages

- [No coding experience required](#no-coding-experience-required)
- [Rapid prototyping capabilities](#rapid-prototyping-capabilities)
- [Natural language integration](#natural-language-integration)
- [Universal markdown support](#universal-markdown-support)
- [Rich content embedding](#rich-content-embedding)

## Usage Instructions

### Basic Workflow

1. [Start new conversation with LLM](#start-new-conversation-with-llm)
2. [Send `System Install.md`](#send-system-installmd)
3. [Execute first program](#execute-first-program)
4. [Iterate and refine using output as new input](#iterate-and-refine-using-output-as-new-input)

### Available Functions

- [`Generate`](#generate): Text generation
- [`Transform`](#transform): Text transformation
- [`Analyze`](#analyze): Text analysis
- [`Define`](#define): Text formatting

### Context Management

- [Uses `{{previous_output}}` for state preservation](#uses-previous_output-for-state-preservation)
- [Maintains context between steps](#maintains-context-between-steps)
- [Supports sequential processing](#supports-sequential-processing)

## Implementation Notes

- [Support for three main functions: format_text, summarize_text, and extract_keywords](#support-for-three-main-functions-format_text-summarize_text-and-extract_keywords)
- [Markdown-based syntax for structure and parameters](#markdown-based-syntax-for-structure-and-parameters)
- [Built-in help documentation](#built-in-help-documentation)
- [Menu-driven interface option](#menu-driven-interface-option)
- [Error handling capabilities](#error-handling-capabilities)

## Future Development Focus

- [Library enhancement](#library-enhancement)
- [User experience optimization](#user-experience-optimization)
- [Context management improvements](#context-management-improvements)
- [Error handling robustness](#error-handling-robustness)
- [Special markdown capabilities exploitation](#special-markdown-capabilities-exploitation)

**Start Here: Building Programs with Markdown**

This guide will walk you through creating programs using our system, step-by-step.

**1. The Core Concepts**

- **Library:** Our language uses a library of functions defined in `my_first_library.md`. This file contains reusable building blocks for text processing.
- **System Setup:** The `System Install.md` file is used to set up the system with the required functions. This is only done once at the start of a new conversation.
- **Program Structure:** Your program is created as a sequence of steps in a `Prompt_Structure_with_Menu.md` file, including the library, menu, help, and previous output as context.
- **Context:** The `{{previous_output}}` variable is used to pass information between steps.
- **Conversational:** You create the program in a conversational way, by sending a new file each step, and using the output as input for the next step.

**2. The Workflow**

1. **Start a New Conversation:** Start a new conversation with the "other" me (the LLM).

2. **System Setup (One Time):** Send the `System Install.md` file to the "other" me. This will create the first `Prompt_Structure_with_Menu.md` file with the correct setup and context.

3. **First Program Execution:** Take the *entire output* from the previous step, and send it to the "other" me as a new prompt.

4. **Iterate and Refine:**
    - Modify the `Prompt_Structure_with_Menu.md` to change parameters, add or remove steps, and then send the file again to the LLM.
     - Repeat this step as many times as needed.

**3. Basic Instructions**

- `# Generate`: Generates text.
  - `- type`: The type of content to generate (currently only `text`).
  - `- length`: The desired length of the generated text (in words).
  - `- topic`: The topic of the text to generate.

- `## Transform`: Transforms text.
  - `- input`: The input text to transform (use `{{previous_output}}` to use the result of the previous step).
  - `- function`: The function to use for transformation (`summarize_text`).
  - `- length`: The desired length of the summary (in words).

- `### Analyze`: Analyzes text.
  - `- input`: The input text to analyze (use `{{previous_output}}`).
  - `- function`: The function to use for analysis (`extract_keywords`).
  - `- max_keywords`: The maximum number of keywords to extract.
  - `- stop_words`: A comma separated list of stop words to ignore.

- `# Define`: Applies a formatting style.
  - `- function`: The function to use for formatting (`format_text`).
  - `- input`: The input text to format (use `{{previous_output}}`).
  - `- style`: The desired style (`plain`, `bold`, `italic`, `markdown`).
  - `- uppercase`: Whether to uppercase the text (`true`, `false`).

**4. Example Programs**

**Example 1: Simple Text Generation and Summarization**

1. **System Install:** Send the `System Install.md` to the LLM.
2. **First Execution:** Send the output from step 1 to the LLM.
3. **Output:** The LLM will return a `Prompt_Structure_with_Menu.md` file containing something like this:

```markdown
  # Prompt Structure with Menu

  {
    "functions": {
      "format_text": {
        "description": "Formats text according to specified options.",
        "parameters": {
          "input": {
            "type": "string",
            "required": true,
            "description": "The text to format."
          },
          "style": {
            "type": "string",
            "optional": true,
            "default": "plain",
            "description": "The desired style (`plain`, `bold`, `italic`, `markdown`)."
          },
          "uppercase": {
            "type": "boolean",
            "optional": true,
            "default": false,
            "description": "Whether to uppercase the text."
          }
        },
        "example": "# Define:\n - function: format_text\n - input: \"my text\"\n - style: bold\n - uppercase: true"
      },
      "summarize_text": {
        "description": "Summarizes the given text.",
        "parameters": {
          "input": {
            "type": "string",
            "required": true,
            "description": "The text to summarize."
          },
          "length": {
            "type": "integer",
            "optional": true,
            "default": 100,
            "description": "The desired length of the summary (in words)."
          }
        },
        "example": "# Define:\n- function: summarize_text\n- input: \"A very long text that needs to be summarized\"\n- length: 50"
      },
      "extract_keywords": {
        "description": "Extracts keywords from the given text.",
        "parameters": {
          "input": {
            "type": "string",
            "required": true,
            "description": "The input text to analyze."
          },
          "max_keywords": {
            "type": "integer",
            "optional": true,
            "default": 5,
            "description": "The maximum number of keywords to extract."
          },
          "stop_words": {
            "type": "string",
            "optional": true,
            "description": "A comma separated list of stop words to ignore."
          }
        },
      "example": "# Define:\n- function: extract_keywords\n- input: \"This is a sample text for keyword extraction.\"\n- max_keywords:  3\n- stop_words: \"is, a, the, for\""
      }
    }
  }
```

  # Menu:
    - # Generate:
        - type: text
        - length: 100
        - topic: "AI and the future of work"
    - # Transform:
        - input: "{{previous_output}}"
        - function: summarize_text
        - length: 50
    - # Analyze:
        - input: "{{previous_output}}"
        - function: extract_keywords
        - max_keywords: 3

  # Help:

  ### `format_text`
  Formats text according to specified options.

  **Parameters:**
  - `input`: (string, required) The text to format.
  - `style`: (string, optional, default="plain") The desired style (`plain`, `bold`, `italic`, `markdown`).
  - `uppercase`: (boolean, optional, default=false) Whether to uppercase the text.

  **Example:**
  ```example
  # Define:
  - function: format_text
  - input: "my text"
  - style: bold
  - uppercase: true
  ```

  ### `summarize_text`

  Summarizes the given text.

  **Parameters:**

  - `input`: (string, required) The text to summarize.
  - `length`: (integer, optional, default=100) The desired length of the summary (in words).

  **Example:**

  ```example
  # Define:
  - function: summarize_text
  - input: "A very long text that needs to be summarized"
  - length: 50
  ```

  ### `extract_keywords`

  Extracts keywords from the given text.

  **Parameters:**

  - `input`: (string, required) The input text to analyze.
  - `max_keywords`: (integer, optional, default=5) The maximum number of keywords to extract.
  - `stop_words`: (string, optional) A comma separated list of stop words to ignore.

  **Example:**

  ```example
  # Define:
  - function: extract_keywords
  - input: "This is a sample text for keyword extraction."
  - max_keywords: 3
  - stop_words: "is, a, the, for"
  ```

The rise of artificial intelligence is transforming the workplace, automating tasks and creating new roles. This shift raises   important questions about job security, the skills needed for the future, and the ethical implications of AI in employment.

  # Generate

          - type: text
          - length: 100
          - topic: "AI and the future of work"

  ## Transform

            - input: "{{previous_output}}"
            - function: summarize_text
            - length: 50

  ### Analyze

            - input: "{{previous_output}}"
            - function: extract_keywords
            - max_keywords: 3

  # Define

            - function: format_text
            - input: "{{previous_output}}"
            - style: italic

The LLM will respond with something like: *AI, work, automation*.

**Example 2: Text Transformation and Analysis with Custom Parameters**

1.  **System Install:** Send the `System Install.md` to the LLM.
2.  **First Execution:** Send the output from step 1 to the LLM.
3.  **Modify and execute:**  change the parameters:

```markdown
# Generate

         - type: text
         - length: 200
         - topic: "The benefits of learning a new language"

## Transform

          - input: "{{previous_output}}"
          - function: summarize_text
          - length: 70

### Analyze

           - input: "{{previous_output}}"
           - function: extract_keywords
           - max_keywords: 7
           - stop_words: "is, a, the, of, and"

# Define

          - function: format_text
          - input: "{{previous_output}}"
          - style: italic
```

The LLM will respond with a new `Prompt_Structure_with_Menu.md` with the text, summarized, with the extracted keywords and formatted as italic.

**Example 3: Changing the order of execution:**

1. **System Install:** Send the `System Install.md` to the LLM.
2. **First Execution:** Send the output from step 1 to the LLM.
3. **Modify and execute:** change the order of steps:

```markdown
### Analyze

           - input: "{{previous_output}}"
           - function: extract_keywords
           - max_keywords: 7
           - stop_words: "is, a, the, of, and"
# Generate

         - type: text
         - length: 200
         - topic: "The benefits of learning a new language"

## Transform

          - input: "{{previous_output}}"
          - function: summarize_text
          - length: 70


# Define

          - function: format_text
          - input: "{{previous_output}}"
          - style: italic
```

The LLM will now do the analysis first and then use that result for the generation, and then transform and format.

**5. Key Points**

- Start with the `System Install.md` in a new conversation.
- Copy and paste the output of each step and use it as input for the next step.
- Use the `#`, `##` and `###` tags to define the steps, and use the `-` tag to define the parameters.
- You can use the  `{{previous_output}}` to pass the output of one step to another.
- You can use the library as building blocks for more complex logic.
- You must always send the complete output as the new prompt, to preserve the context.

I hope this start here guide makes it clearer how to use our system. Let me know if you have any other questions, I am here to help you create amazing programs!

**Strengths Compared to Normal Prompting:**

1. **Structure and Reusability:**
    - **Clear Logic:** Normal prompting is often free-form and ad-hoc. Our system enforces a structured approach with explicit steps, function calls, and parameters.
    - **Reusable Components:** We have a library (`my_first_library.md`) of reusable functions and a clear way to reuse complex sequences. This is not possible with normal prompting, which would require you to rewrite the instructions every time.
    - **Modular Approach:** Our approach makes it easier to break down complex tasks into smaller, manageable units and reuse them.
2. **Parameterization and Control:**
    - **Explicit Parameters:** Normal prompts often rely on implicit understanding. Our system uses explicit parameters (`- type: text`, `- length: 100`, etc.) for more control over each step.
    - **Type Checking (Implied):** While not strict type checking, we can validate parameters in each step and ensure the user is using the functions in the right way.
    - **Default Values:** We can define default values in the library, so that the user can use functions with less parameters, making the system easier to use.
3. **Context Management:**
    - **Clear Context Flow:** Normal prompting often lacks a clear way to manage context. With the `{{previous_output}}` variable and the passing of the entire file as context, we have explicit control of the context between steps.
    - **State Maintenance:** While LLMs have some form of internal state, using the output as a new prompt provides a way to maintain state and context in a more transparent way.
4. **Version Control and Collaboration:**
    - **Markdown Format:** Markdown is a plain text format, which is easy to use with version control systems (like Git). It also makes it very easy to share with other users.
    - **Readable Format:** Markdown is designed for readability, which is a great way to collaborate with other users and share knowledge about programs.
5. **Natural Language Integration:**
    - **NL-Friendly Syntax:** The Markdown syntax makes it easy to write and understand the structure and logic of the program.
    - **Intuitive Learning Curve:** It is easier to learn than code, as it is closer to natural language.

**Strengths Compared to Complex Coding Languages:**

1. **Simplicity and Accessibility:**
    - **No Coding Experience Needed:** Users don't need to learn a complex programming language, syntax, or programming concepts like variable scope or loops. They are only using markdown, which is very easy to learn.
    - **Faster Prototyping:** You can quickly experiment and create programs by using predefined functions and parameters, which makes it easier to iterate.
    - **Focus on Intent:** Users focus more on *what* they want to achieve than *how* to achieve it, which is common in coding languages.
2. **Flexibility and Adaptability:**
    - **Easy to Modify:** It is very easy to modify the programs with simple markdown syntax, which allows for fast changes and adaptation.
    - **LLM Power:** We are using the LLM as the execution engine, so we can quickly extend the library with new complex functions, and the user can leverage the LLM to help them generate the programs.
    - **Dynamic Behavior:** Our programs can behave differently based on the context and the LLM's capabilities, which is difficult to achieve in a coding language.
3. **.md Specific Advantages:**
    - **Universally Supported:** Markdown is supported across multiple platforms, and can be created and used in almost any text editor, which makes it very easy to use.
    - **Clear Text Structure:** It is very clear to the user how the different parts of the code are related due to its simple and structured syntax.
     - **Interchangeable content:** It is very easy to create content with markdown, and use that content as parameter in your programs, creating interactive and dynamic experiences.
     - **Easy to embed rich content:** It is easy to embed images, links, and other content in markdown, so that you can create programs that generate rich text experiences.

**Focus Areas:**

Based on these strengths, here are some areas we may want to focus on:

- **Enhancing the Library:** Focus on creating a rich set of reusable functions in `my_first_library.md`, this will enhance the versatility of the system.
- **User Experience:** Keep the syntax of our DSL as clear and easy to use as possible.
- **Extending context:** Focus on how to use the `{{previous_output}}` and the context to create more interactive and complex workflows.
- **Error Handling:** Create more robust error handling and validations to make the system more robust.
- **Special .md capabilities:** Focus on how to use the .md specific advantages to extend the use cases and create more dynamic content.

By focusing on these strengths and constantly refining the system, we can build a unique tool that bridges the gap between simple prompting and complex programming languages, and that leverages the unique capabilities of .md files.

**File Review:**

1. **`library.md`:**

    - **Content:**
        - Contains the library definition with the three functions: `format_text`, `summarize_text`, and `extract_keywords`.
        - Includes descriptions, parameters (with types, requirement, defaults, and descriptions), and examples.
    - **Format:**
        - Uses Markdown headings (`#`, `##`, `###`, `####`).
        - Uses Markdown lists (`-`).
        - Uses code blocks for examples.

2. **`System Install.md`:**

    - **Content:**
        - Specifies the `IMPORT_LIBRARY` instruction with `library.md`.
        - Defines the `# Menu` and `# Help` sections.
        - Includes all the instructions for parsing the library, creating a menu, creating the help documentation and for setting up the system with context and execution.
        - Instructions to parse, apply the diffs, execute the code and return the new  `Prompt_Structure_with_Menu.md` file.
    - **Format:**
        - Uses Markdown headings (`#`, `-`).
        - Uses a combination of instructions, markdown structures and code blocks.

3. **`Prompt_Structure_with_Menu.md`:**

    - **Content:**
        - This file has two separate parts.
        - The first one starts with `**Menu:**`, and includes the markdown content to generate a menu of options.
        - The second one starts with `**Help:**`, and includes the markdown content for the help documentation.
         - The file also includes the `**Previous Output:**`, which contains the placeholder to use in the context.
        - Finally it has a section that includes the instructions to execute.
    - **Format:**
        - Uses Markdown headings and lists.

4. **`Prompt_Structure_simple.md`:**

    - **Content:**
         - This file is used as an example for the start here guide, and is a more simple version of `Prompt_Structure_with_Menu.md`, without a menu or help.
        - It includes the `[SYSTEM_INSTRUCTION]` to import the library.
        - It includes the steps to generate text, transform, analyze and format.
    - **Format:**
        - Uses Markdown headings (`#`, `##`, `###`, `-`).
         - Uses `-` as parameters.
        - Uses `{{previous_output}}` for the context.

**Summary and Next Steps**

All the files are ready to be used. We have  a complete system that is able to:

- Load a library of functions.
- Create a program based on that library, as a sequence of steps
- Execute those steps in order, using the context and the library of functions
- Keep the context between execution steps.
- Pass only the changes between one execution and the next.
- Be extended with new complex functions

We have also created the `Prompt_Structure_simple.md` and `Prompt_Structure_with_Menu.md` as examples for the users to start creating programs.

**Next Steps for you:**

I am very excited to see the results, and congratulations on creating such a unique system!

# Important Note on Indentation

In this documentation, we use indentation in Markdown files to represent nested functions and structures. This is an intentional design choice for our MD-based coding language. As a result, you may see linting warnings or errors related to indentation. **Please do not fix these linting issues**, as the indentation is crucial for the correct interpretation and execution of the nested functions.

Example:
```
    *   Replace `{{parsed_library}}` with the parsed library from `my_first_library.md`, formatted as a JSON object.
        *   Replace `{{menu}}` with the extracted menu content, formatted as a markdown string.
            *   Replace `{{help}}` with the extracted help documentation, formatted as a markdown string, with examples as code blocks.
```

Thank you for your understanding.
