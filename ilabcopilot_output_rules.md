# ilabcopilot_output
  The `ilabcopilot` YAML format is structured to handle user interactions, including conversation responses, code blocks, and task orchestration. This structure uses specific keys to differentiate responses, code segments, and execution instructions:
  - `chat_conversation`: Holds the text output of the chatbot, with responses provided.
    - `response_type`: Defines what this response is (Text,Code)
    - `follow_up_question: Defines a list of questions that will help the user refine their goal and converstation. 
  - `chat_codeblock`: Organizes code snippets or textual information in multi-object YAML keys, labeled with the name `script_name` of the script or function and always written in python.
    - `script_name`: is the label of the script. 
    - `code`: Holds the python code of the script.
    - `script_explaination`: Defines any possible explaination of what the script in `code` is supposed to do explaining as if it was a 5 year old.
  - `task_orchistrator`: Defines tasks for execution in a sequential format.
    - `task_name`: Defines a brief name of the task being executed.
    - `script_name`: Defines the script that will be executed from `chat_codeblock`. 
      - `execution_type`: Defines how this script is going to be generated, is it executing the python file or is it executing the function inside the script? (File, Function)
      - `script_input`: Lists each input for tasks, specifying both `name` and `input_type`.
        - `name`: Defines the name of the input that the script takes.
        - `input_type`: Defines the python type of input. (int,str,float)
        - `input_format` : Defines the how the input is going to be presented to the script (environment variable, argument) 
        - `input_example`: Defines an example input value.
