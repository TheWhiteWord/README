# TESTING READMEs

## **Understanding the `README.md` Structure**

Here's a recap of the key sections in the `README.md` file:

1.  **`## System Configuration`:**
    *   This section contains the YAML metadata for the system.
    *   It includes the `version`, `context`, `variables`, and `parser` settings.
    *   **Required for all steps:** This section is essential and should always be present.

2.  **`## Parser Implementation`:**
    *   This section includes the JavaScript code for parsing the `README.md`.
    *   **Required for all steps:** The system needs this to understand the other sections.

3.  **`## Function Library`:**
    *   This section defines the available functions: `system_init`, `system_execute`, `format_text`, `summarize_text`, and `extract_keywords`.
    *   **Required for all steps:** This is how the LLM knows which functions it can execute.

4.  **`## Program Templates`:**
    *   This section defines reusable templates for different tasks (e.g., `Bootstrap`, `Text Analysis`, `Text Analysis Pipeline`).
    *  **Required for Steps 2, 3 and 4**: These templates are needed to use `system_execute`.
        *   For step 1, since we are only testing the `system_init` function, it is not required.

5.  **`## Execution Context`:**
    *   This section defines the default structure of the execution context.
    *   **Required for all steps:** This is the initial context.

6.  **`## Help Documentation`:**
    *   This section is used for documentation purposes, and it is not strictly required for any of the execution steps.

It's important to understand how to test individual components within our system, especially with this new `README.md`-centric approach. Let's break down how to test each part:


## **Testing Methodology**

The core idea is to test each part of the system in isolation as much as possible, by sending different versions of the `README.md` file with different templates.

**1. Testing `system_init` (Initialization)**

*   **Purpose:** To verify that the `system_init` function correctly parses the `README.md` file, loads the library functions, and sets up the initial context.
*   **How to Test:**
    1.  **Send the Complete `README.md` File:** In a *new conversation*, send the complete `README.md` file to the "other" me.
    2.  **Initial Execution:** The `system_init` function is called automatically, and it should parse the file and return the file as is.
    3.  **Observe:** Check if the `README.md` content is returned correctly, meaning that the system has been initialized.
*   **Expected Output:** The "other" me should return the `README.md` file as a Markdown code block, and a confirmation that the system is ready.

**2. Testing `system_execute` with `Text Analysis` template**

*   **Purpose:** To verify that the `system_execute` function can correctly use the `text_analysis` template, use a context variable and return the output.
*   **How to Test:**
    1.  **Send the Initial `README.md` File:** Start by sending the `README.md` file (the output of the previous step) to the "other" me.
    2.  **Add the template Execution:** Modify the file, and add the section to execute the template.
        ```markdown
        # Execute
         - function: system_execute
         - template: text_analysis
         - input: "This is a test for the text_analysis template"
         - context: "{{system_state}}"
        ```
    3.  **Observe the Output:** Check that the "other" me returns the output of the execution, including the previous output, the library, the help and the menu.
*   **Expected Output:** The output should include the execution of the template, including the transformed text.

**3. Testing `system_execute` with `Text Analysis Pipeline` template**

*   **Purpose:** To verify that the `system_execute` function can correctly use the `Text Analysis Pipeline`, use `previous_output` and a variable and return the output.
*   **How to Test:**
    1.  **Send the Modified `README.md` File:** Send the output from the last test to the "other" me again.
     2. **Modify the input to `system_execute`:**
          ```markdown
          # Execute
            - function: system_execute
            - template: text_analysis_pipeline
            - topic: "Testing the pipeline template"
         ```
    3.  **Observe the Output:** Check that the "other" me returns the output of the execution, including the generated text, the summarization, the extracted keywords, the formatted output and the `{{previous_output}}`.
*   **Expected Output:** The output should include the result of all the steps, including the new value of `{{previous_output}}`.

## **4. Testing Examples in Documentation**

*   **Purpose:** Verify that the examples provided in the `README.md` file can be directly executed.
*   **How to Test:**
    1.  **Start with a modified version of the `README.md` file:** Use the output of one of the previous tests, and send it to the LLM.
    2.  **Add the example execution:** Add the example inside the `README.md` file using the correct tag, and send it to the LLM.
        ```markdown
          ## Summarize Current Document

          ```RM
          # Transform
          - input: "{{readme_content}}"
          - function: summarize_text
          - length: 100
        ```
    3.  **Observe the Output:** Check that the "other" me correctly executes the live example and adds the output to the file.
*   **Expected Output:** The output should contain the result of the example execution.

**5. Testing Variations**

After testing the core functionalities, you can add more tests that change parameters or add steps to check more complex executions and error conditions.

**Key Points for Testing:**

*   **Start with a Clean State:** Always begin with the `README.md` file in a new conversation when testing `system_init`.
*   **One Change at a Time:** When testing different parts, try to change only one thing to isolate the source of any problems.
*   **Observe Carefully:** Pay close attention to the LLM's output to see if it's following the steps correctly.
*   **Iterate:** If you find issues, modify the code and retest until the issue is solved.

By following this approach, you can test each part of our system thoroughly and identify any potential issues early on.

# **Testing Steps and Required Components**

Now, let's clarify what you should include in `README.md` for each of the testing steps:

**Step 1: Testing `system_init` (Initialization)**

*   **Purpose:** To verify the system can parse the `README.md` file.
*   **Required Components:**
    *   `## System Configuration`
    *   `## Parser Implementation`
    *   `## Function Library` (specifically, the `system_init` function definition)
    *   `## Execution Context`
*   **What to Remove:** You can remove `## Program Templates` and `## Help Documentation` for this test as it will not be used.
*   **What to Send:** The minimum version of the `README.md` for this step would be:

    ```markdown
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

*   **Expected Result:** The LLM should return a confirmation message and the same file you sent.

**Step 2: Testing `system_execute` with `Text Analysis` template**

*   **Purpose:** Verify the system can parse the context and execute the template.
*   **Required Components:**
    *   `## System Configuration`
    *   `## Parser Implementation`
    *   `## Function Library` (including `system_execute`)
    *   `## Program Templates` (specifically, the `Text Analysis` template)
     *   `## Execution Context`
*   **What to Remove:** You can remove `## Help Documentation` for this test as it will not be used.
*   **What to Add:**
       *  You need to add the `Text Analysis` template in the `## Program Templates` section.
        * You also need to add the ` # Execute`  command at the end, referencing the `Text Analysis` template, the input and context.
*   **What to Send:** The minimum version of the `README.md` for this step would be:

    ```markdown
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

    ## Program Templates

    ### Bootstrap
    # Execute
    - function: system_init
    - input: "{{readme_content}}"
    - outputs:
        - system_state
        - functions
        - templates

    ### Text Analysis
    # Execute
    - function: system_execute
    - template: text_analysis
    - input: "This is a test for the text_analysis template"
    - context: "{{system_state}}"

    ## Execution Context

    ```json
    {
    "previous_output": "",
    "variables": {},
    "state": "ready"
    }
    ```
*   **Expected Result:** The output should include the results of the execution of the `text_analysis` template.

**Step 3: Testing `system_execute` with `Text Analysis Pipeline` template**

*   **Purpose:** Verify the system can parse and use the variables, context and execute multiple functions in sequence.
*    **Required Components:**
        *   `## System Configuration`
        *   `## Parser Implementation`
        *   `## Function Library` (including `system_execute`, `summarize_text` and `extract_keywords`)
        *   `## Program Templates` (specifically, the `Text Analysis Pipeline` template)
         *   `## Execution Context`
*    **What to Remove:** You can remove `## Help Documentation` and the `Text Analysis` template for this test as it will not be used.
*   **What to Add:**
       *  You need to add the `Text Analysis Pipeline` template in the `## Program Templates` section.
        * You also need to add the ` # Execute`  command at the end, referencing the `Text Analysis Pipeline` template, and setting the topic.
*   **What to Send:** The minimum version of the `README.md` for this step would be:

    ```markdown
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

    ## Program Templates

    ### Bootstrap
    # Execute
    - function: system_init
    - input: "{{readme_content}}"
    - outputs:
        - system_state
        - functions
        - templates

    ### Text Analysis Pipeline

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

    ## Execution Context

    ```json
    {
    "previous_output": "",
    "variables": {},
    "state": "ready"
    }
    ```
*  **Expected Result:** The output should include the generated text, then the summary and then the extracted keywords.

**Step 4: Testing Live Examples**

*   **Purpose:** Verify that the examples provided can be directly executed.
*    **Required Components:**
        *   `## System Configuration`
        *   `## Parser Implementation`
        *   `## Function Library` (including `summarize_text` and `extract_keywords`)
         *   `## Execution Context`
        *   The rest of the components are not required
*   **What to Remove:** You can remove the templates in this example.
*   **What to Add:**
        * Add the live example at the end of the file using the `RM` tag:
           ```markdown
             ## Summarize Current Document

              ```RM
              # Transform
              - input: "{{readme_content}}"
              - function: summarize_text
              - length: 100
           ```
*  **What to Send:** The minimum version of the `README.md` for this step would be:

    ```markdown
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
    ## Summarize Current Document

    ```RM
    # Transform
    - input: "{{readme_content}}"
    - function: summarize_text
    - length: 100
    ```
*   **Expected Output:** The output should include the summarization of the `README.md` file.

By following these guidelines, you can test the system in a modular and controlled way, ensuring that each component is working as expected. This will make it easier to debug and improve our system.

