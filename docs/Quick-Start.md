# IsoZero Quick Start Guide

This guide will help you get up and running with IsoZero quickly. We'll cover installation, basic setup, and a simple example for each main functionality.

## Installation

1. Install IsoZero using pip:
   ```
   pip install isozero
   ```

2. Set up your API keys (if using OpenAI or Anthropic):
   ```
   export OPENAI_API_KEY='your-openai-api-key'
   export ANTHROPIC_API_KEY='your-anthropic-api-key'
   ```

## Basic Usage

### 1. General Reasoning

Here's a simple example of using IsoZero for a general reasoning task:

```python
from isozero.reason_sim import ClaudeAgent, ReasonSimulation, SimulationWrapper

# Initialize the agent
agent = ClaudeAgent(api_key="your-anthropic-api-key")

# Set up a reasoning task
simulation = ReasonSimulation("Explain the importance of renewable energy", max_steps=3)
wrapper = SimulationWrapper(agent, simulation)

# Run the simulation
for step in range(3):
    state = wrapper.step()
    print(f"Step {state['text_data']['step']}:", state['text_data']['reasoning'][-1])
```

### 2. Document Analysis

For document analysis, you can use the QuestionAnswerer:

```python
from isozero.reason_sim import ClaudeAgent, QuestionAnswerer, DocumentLoader

# Initialize the agent and loader
agent = ClaudeAgent(api_key="your-anthropic-api-key")
loader = DocumentLoader()

# Load documents
documents = loader.load(["path/to/document.txt"])

# Set up the question answerer
qa = QuestionAnswerer(agent)

# Ask questions
results = qa.answer_questions(documents, ["What are the main themes in this document?"])
print(results[0]['answer'])
```

### 3. Math Problem Solving

For mathematical problems, use the MathSimulation:

```python
from isozero.math_sim import OpenAIAgent, MathSimulation, SimulationWrapper

# Initialize the agent
agent = OpenAIAgent(api_key="your-openai-api-key")

# Set up a math problem
simulation = MathSimulation("Calculate the area of a circle with radius 5 cm", max_steps=4)
wrapper = SimulationWrapper(agent, simulation)

# Run the simulation
for step in range(4):
    state = wrapper.step()
    print(f"Step {state['text_data']['step']}:", state['text_data']['reasoning'][-1])
```

## Using the CLI

IsoZero also provides a command-line interface for quick tasks:

1. General Reasoning:
   ```
   isozero --mode reasoning --task "Explain the water cycle" --agent claude --steps 3 --save
   ```

2. Document Analysis:
   ```
   isozero --mode qa --documents article.txt --questions questions.txt --agent openai --steps 3
   ```

3. Math Problem Solving:
   ```
   isozero --mode math --task "Solve for x: 2x + 5 = 15" --agent claude --steps 3 --save
   ```

## Next Steps

- Explore the [Core Concepts](./Core-Concepts) to understand IsoZero's architecture
- Check out more [Examples and Use Cases](./Examples) for advanced usage
- Refer to the [CLI Commands](./CLI-Commands) page for a full list of command-line options

Congratulations! You've taken your first steps with IsoZero. Happy reasoning!