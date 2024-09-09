# IsoZero CLI Commands

IsoZero provides a flexible Command Line Interface (CLI) for various tasks. This page outlines the available commands and their usage.

## Basic Command Structure

The basic structure of an IsoZero CLI command is:

```
isozero --mode <mode> --task <task> --agent <agent> --steps <steps> [additional options]
```

## Available Modes

IsoZero supports three main modes:

1. `reasoning`: For general reasoning tasks
2. `qa`: For document analysis and question answering
3. `math`: For mathematical problem-solving

## Common Options

- `--mode`: Specifies the operation mode (reasoning, qa, or math)
- `--task`: Defines the task or question to be processed
- `--agent`: Specifies the LLM backend to use (claude, openai, or huggingface)
- `--steps`: Sets the number of reasoning steps (default is 4)
- `--save`: Saves the results to a JSON file in the `logs` folder

## Mode-Specific Options

### Reasoning Mode

```
isozero --mode reasoning --task "Explain the process of photosynthesis" --agent claude --steps 4 --save
```

### Question Answering (QA) Mode

```
isozero --mode qa --documents https://en.wikipedia.org/wiki/Artificial_intelligence https://en.wikipedia.org/wiki/Machine_learning --questions questions.txt --agent huggingface --model google/flan-t5-large --steps 4
```

Additional options for QA mode:
- `--documents`: Specifies the documents to analyze (can be URLs or file paths)
- `--questions`: Path to a text file containing questions

### Math Mode

```
isozero --mode math --task "A train travels at 60 km/h for 2 hours, then at 90 km/h for 3 hours. What's the total distance?" --agent openai --steps 4 --save
```

## Examples

1. General Reasoning with Claude:
   ```
   isozero --mode reasoning --task "Explain the implications of Moore's Law in computing" --agent claude --steps 5 --save
   ```

2. Document Analysis with Hugging Face model:
   ```
   isozero --mode qa --documents research_paper.pdf --questions research_questions.txt --agent huggingface --model google/flan-t5-large --steps 3
   ```

3. Math Problem Solving with OpenAI:
   ```
   isozero --mode math --task "Calculate the compound interest on $1000 invested for 5 years at 5% per annum" --agent openai --steps 4 --save
   ```

## Tips

- Use quotation marks around complex tasks or questions.
- When using the `--documents` option in QA mode, you can specify multiple documents by separating them with spaces.
- The `--save` option is useful for storing results for later analysis or comparison.

For more detailed information on each command and its options, use the `--help` flag:

```
isozero --help
```

This will display a comprehensive help message with all available options and their descriptions.