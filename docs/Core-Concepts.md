# IsoZero Core Concepts

This page explains the fundamental concepts and architecture of IsoZero. Understanding these concepts will help you use IsoZero more effectively and extend its capabilities for your specific needs.

## 1. Multi-Step Reasoning

At the heart of IsoZero is the concept of multi-step reasoning. Instead of trying to solve complex problems in one go, IsoZero breaks them down into smaller, more manageable steps. This approach mimics human problem-solving strategies and often leads to more accurate and insightful results.

## 2. Agents

Agents in IsoZero are wrappers around different LLM backends. They provide a unified interface for interacting with various language models. IsoZero supports three types of agents:

- ClaudeAgent: For Anthropic's Claude model
- OpenAIAgent: For OpenAI's GPT models
- HuggingFaceAgent: For various models from Hugging Face

## 3. Simulations

Simulations are the core logic handlers in IsoZero. They manage the state of the reasoning process and determine how to proceed at each step. IsoZero provides two main types of simulations:

- ReasonSimulation: For general reasoning tasks and document analysis
- MathSimulation: Specialized for mathematical problem-solving

## 4. SimulationWrapper

The SimulationWrapper acts as a bridge between the Agent and the Simulation. It manages the interaction between these components, ensuring that the agent's outputs are properly formatted and fed back into the simulation.

## 5. Document Analysis

For tasks involving document analysis, IsoZero provides additional components:

- DocumentLoader: Handles loading and preprocessing of documents from various sources
- QuestionAnswerer: Manages the process of answering questions based on loaded documents

## 6. State Management

IsoZero maintains a state throughout the reasoning process. This state includes:

- The current step number
- The history of reasoning steps
- Any intermediate results or calculations

This state management allows for complex, multi-step reasoning processes and enables the system to build upon previous steps.

## 7. CLI Interface

IsoZero provides a command-line interface (CLI) that allows users to quickly run simulations without writing Python code. The CLI supports all major functionalities of IsoZero and provides options for customization.

## 8. Extensibility

IsoZero is designed to be extensible. Users can create custom agents for new LLM backends, design specialized simulations for specific types of problems, or extend existing components to add new functionalities.

## Putting It All Together

In a typical IsoZero workflow:

1. An Agent is initialized with the appropriate API key.
2. A Simulation is created with the problem statement and parameters.
3. These are combined in a SimulationWrapper.
4. The wrapper's `step()` method is called repeatedly to progress through the reasoning steps.
5. At each step, the Agent generates a response based on the current state, and the Simulation updates the state based on this response.
6. This process continues until the maximum number of steps is reached or the problem is solved.

Understanding these core concepts will allow you to leverage the full power of IsoZero in your projects, whether you're using the provided components or extending them for custom use cases.