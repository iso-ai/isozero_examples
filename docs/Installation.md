# IsoZero Installation Guide

This guide will walk you through the process of installing IsoZero on your system.

## Prerequisites

Before installing IsoZero, ensure you have the following:

- Python 3.7 or higher
- pip (Python package installer)

## Installation Steps

### 1. Install from PyPI

The simplest way to install IsoZero is directly from PyPI using pip:

```bash
pip install isozero
```

### 2. Install from GitHub (for latest development version)

If you want the latest development version, you can install IsoZero directly from the GitHub repository:

```bash
pip install git+https://github.com/iso-ai/isozero.git
```

### 3. Verify Installation

After installation, you can verify that IsoZero was installed correctly by running:

```bash
python -c "import isozero; print(isozero.__version__)"
```

This should print the version number of IsoZero.

## Setting Up API Keys

IsoZero supports multiple LLM backends, some of which require API keys. After installation, you'll need to set up your API keys:

1. For OpenAI GPT:
   ```bash
   export OPENAI_API_KEY='your-api-key-here'
   ```

2. For Anthropic Claude:
   ```bash
   export ANTHROPIC_API_KEY='your-api-key-here'
   ```

3. For Hugging Face models, you typically don't need an API key for open-source models.

Remember to replace 'your-api-key-here' with your actual API keys.

## Troubleshooting

If you encounter any issues during installation, please check our [Troubleshooting Guide](./Troubleshooting) or open an issue on our [GitHub repository](https://github.com/iso-ai/isozero/issues).

Next Steps: Once you've successfully installed IsoZero, head over to our [Quick Start Guide](./Quick-Start) to begin using the SDK!