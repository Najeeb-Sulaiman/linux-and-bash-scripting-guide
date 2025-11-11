## Python Project Environment Bootstrapper

You have just joined the Data Engineering team at **Beejan Technology**, a company that maintains several Python-based data pipelines and engineering projects.

Each time a new engineer joins, they spend hours manually setting up their development environment, creating virtual environments, upgrading pip, setting up `.gitignore` files, and installing essential tools.

The team lead wants you to **automate** this process using **Bash scripting** so that any new project can be set up instantly with one command.

### Project Requirements

Create a Bash script named `setup.sh` that performs the following actions:

1. Checks for an existing Python virtual environment
    - If one exists, activate it.
    - If not, create and activate a new one.
2. Upgrades pip
    - Ensure the latest version of pip is installed in the environment.
3. Generates a `.gitignore` file
    - The file should include standard ignore rules for a Python project (e.g .venv, ).
    - Skip creation if it already exists, but display a warning message.
4. Provides colorful, user-friendly feedback
    - Use color codes to display INFO, SUCCESS, WARNING, and ERROR messages.
5. Includes structured functions
    - Organize each task (virtual environment, pip upgrade, gitignore, etc.) into its own function.
    - Include a main function that calls these functions in sequence.
6. Handles errors gracefully
    - The script should stop immediately if any command fails.
7. Automatically install a few Python packages (like pandas or requests).
8. Write a comprehensive log of all setup actions to a file called `setup.log`.

### Script Functionality

When the script runs:

- It should **create or activate** a `.venv` folder in the project directory.
- It should **upgrade pip** and confirm success.
- It should check for `.gitignore` and create one if missing.
- It should **print progress messages** with different colors for clarity.
- It should end with a final message indicating that setup is complete.

### Note

- **Think about reusability:** if someone runs your script twice, it should not break or duplicate files.
- Use functions to organize your code logically.
- Use conditional checks to decide whether to create or skip actions.
- Include clear messages to help the user understand what is happening.
- Handle errors properly.
- Test with different scenario (No `.venv` directory exists, `.venv` already exists, `.gitignore` already exists etc.)

### Submission

You are to submit:
1. `setup.sh` — fully working script
2. `README.md` — explaining:
    - What the script does
    - How to execute it
    - Example outputs (copy your terminal messages here)
    - Challenges faced and lessons learned
