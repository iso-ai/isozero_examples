# IsoZero Examples and Use Cases

This page provides various examples and use cases for IsoZero, demonstrating its versatility and power in different scenarios. We'll cover both code snippets and real-world applications, as well as point you to our repository of example Jupyter notebooks.

## Example Notebooks

We maintain a repository of Jupyter notebooks with comprehensive examples of running the IsoZero package. These notebooks are designed to give you hands-on experience with IsoZero's capabilities.

You can find these notebooks here: [IsoZero Examples Repository](https://github.com/iso-ai/isozero_examples/tree/main/notebooks)

We encourage you to clone this repository and run the notebooks locally to get a feel for how IsoZero works in practice.

## Code Examples

### 1. Complex Reasoning Task

Here's an example of using IsoZero for a complex reasoning task:

```python
from isozero.reason_sim import ClaudeAgent, ReasonSimulation, SimulationWrapper

agent = ClaudeAgent(api_key="your-api-key")
simulation = ReasonSimulation("Analyze the potential long-term effects of artificial intelligence on the job market", max_steps=5)
wrapper = SimulationWrapper(agent, simulation)

for step in range(5):
    state = wrapper.step()
    print(f"Step {state['text_data']['step']}:", state['text_data']['reasoning'][-1])
```

### 2. Multi-Document Analysis

This example shows how to use IsoZero for analyzing multiple documents:

```python
from isozero.reason_sim import OpenAIAgent, QuestionAnswerer, DocumentLoader

agent = OpenAIAgent(api_key="your-api-key")
loader = DocumentLoader()

documents = loader.load(["report1.pdf", "report2.pdf", "article.txt"])
qa = QuestionAnswerer(agent)

questions = [
    "What are the main themes across these documents?",
    "How do the conclusions of the reports compare to the article?"
]

results = qa.answer_questions(documents, questions)
for i, result in enumerate(results):
    print(f"Question {i+1}:", questions[i])
    print("Answer:", result['answer'])
    print()
```

### 3. Step-by-Step Math Problem Solving

Here's how you can use IsoZero to solve a complex math problem:

```python
from isozero.math_sim import HuggingFaceAgent, MathSimulation, SimulationWrapper

agent = HuggingFaceAgent(model="google/flan-t5-large")
simulation = MathSimulation("A company's profit increased by 20% in the first year and 15% in the second year. If the final profit was $138,000, what was the initial profit?", max_steps=6)
wrapper = SimulationWrapper(agent, simulation)

for step in range(6):
    state = wrapper.step()
    print(f"Step {state['text_data']['step']}:", state['text_data']['reasoning'][-1])
```

## Use Cases

1. **Academic Research**: IsoZero can assist researchers in literature review by analyzing multiple papers and extracting key themes or contradictions.

2. **Financial Analysis**: Use IsoZero to break down complex financial problems, such as valuation models or risk assessments, into step-by-step processes.

3. **Legal Document Review**: Law firms can leverage IsoZero to analyze large volumes of legal documents, extracting relevant information and answering specific questions.

4. **Educational Tools**: Create interactive learning experiences by using IsoZero to guide students through complex problem-solving processes in various subjects.

5. **Policy Analysis**: Government agencies can use IsoZero to analyze policy documents, predicting potential outcomes and identifying areas of conflict or synergy.

6. **Medical Diagnosis Assistance**: While not a replacement for professional medical advice, IsoZero can help medical professionals by breaking down complex symptom patterns and suggesting potential diagnoses for further investigation.

7. **Software Debugging**: Developers can use IsoZero to analyze error logs and code snippets, breaking down the debugging process into logical steps.

8. **Creative Writing**: Authors can use IsoZero to break down complex plot structures or character development processes, providing step-by-step guidance for storytelling.

## CLI Examples

Here are some examples of using IsoZero via the command line:

1. Analyzing a scientific concept:
   ```
   isozero --mode reasoning --task "Explain the concept and implications of quantum entanglement" --agent claude --steps 5 --save
   ```

2. Answering questions about a research paper:
   ```
   isozero --mode qa --documents research_paper.pdf --questions research_questions.txt --agent openai --steps 4
   ```

3. Solving a complex math word problem:
   ```
   isozero --mode math --task "A cylindrical water tank with a radius of 5 meters is being filled at a rate of 2 cubic meters per minute. How long will it take to fill the tank to a height of 8 meters?" --agent claude --steps 6 --save
   ```

Remember to check out the [example notebooks](https://github.com/iso-ai/isozero_examples/tree/main/notebooks) for more in-depth examples and use cases. These notebooks provide a hands-on way to explore IsoZero's capabilities and see how it can be applied to various real-world scenarios.

We encourage users to experiment with these examples and adapt them to their specific needs. If you develop an interesting use case or example, consider contributing it back to the community!