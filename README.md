# IsoZero Example Repository

This repository contains a collection of Jupyter notebooks demonstrating the usage of IsoZero, a powerful SDK designed to enhance Large Language Model (LLM) zero-shot responses through multi-step reasoning and document analysis.

## About IsoZero

IsoZero helps improve the accuracy and depth of LLM outputs, especially in scenarios where the model hasn't been specifically fine-tuned for the task at hand. It leverages a step-by-step reasoning process to break down complex tasks.

### Features

* Multi-step reasoning process to break down complex tasks
* Support for multiple LLM backends:
   * Claude (Anthropic)
   * GPT (OpenAI)
   * Transformer models (Hugging Face)
* Document analysis capabilities for context-aware responses
* Mathematical problem-solving simulation
* Flexible CLI with progress bars and result saving
* Customizable number of reasoning steps

### Package Structure

The IsoZero package consists of two main modules:
1. `reason_sim`: General reasoning and document analysis
2. `math_sim`: Mathematical problem-solving simulation

## Installation

To use these notebooks, you'll need to install IsoZero. You can install it directly from PyPI:

```
pip install isozero
```

For the latest development version:

```
pip install git+https://github.com/iso-ai/isozero.git
```

## Notebooks in this Repository

1. `01_General_Reasoning.ipynb`: Demonstrates general reasoning tasks using IsoZero
2. `02_Document_Analysis.ipynb`: Shows how to perform document analysis and question answering
3. `03_Math_Problem_Solving.ipynb`: Illustrates mathematical problem-solving capabilities
4. `04_Custom_Agent_Usage.ipynb`: Examples of using custom agents with IsoZero

## Usage Example

Here's a brief example of how to use IsoZero in a Jupyter notebook:

```python
from isozero.reason_sim import ClaudeAgent, ReasonSimulation, SimulationWrapper

# Initialize the agent (replace with your actual API key)
agent = ClaudeAgent(api_key="your_api_key_here")

# Set up a reasoning task
simulation = ReasonSimulation("Explain the process of photosynthesis", max_steps=4)
wrapper = SimulationWrapper(agent, simulation)

# Run the simulation
for step in range(4):
    state = wrapper.step()
    print(f"Step {state['text_data']['step']}:", state['text_data']['reasoning'][-1])
```

## Getting Started with the Notebooks

1. Clone this repository to your local machine or Google Drive.
2. Open the notebooks in Jupyter or Google Colab.
3. Make sure you have installed IsoZero (see Installation section).
4. Follow the instructions in each notebook to explore IsoZero's capabilities.

## Note on API Keys

Some notebooks may require API keys for services like OpenAI or Anthropic. Make sure to keep your API keys secure and never share notebooks containing your keys.

Happy exploring with IsoZero!
