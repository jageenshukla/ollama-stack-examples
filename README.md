# Custom Tool Integration with Llama Stack

This sample code demonstrates how to integrate a custom tool into the Llama Stack and configure an agent. For this demo, we use a custom tool called `StoryTeller`, which takes one parameter, `story_name`, and returns a mock response "mock response from tool story_teller for test_story".

## Prerequisites

- Python 3.13.1
- Docker (Refer to [Docker Installation Guide](https://docs.docker.com/get-started/get-docker/))
- Llama Stack (Refer to [Llama Stack GitHub Repository](https://github.com/meta-llama/llama-stack))
- Ollama Tool (Refer to [Ollama Tool Download](https://ollama.com/download/mac))

## Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd ollama-stack-examples
```

### 2. Create and Activate a Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Install and Run Ollama Tool

Download and install the Ollama tool from [Ollama Tool Download](https://ollama.com/download/mac).

Run the model using the following command:

```bash
ollama run llama3.2:1b-instruct-fp16
```

### 5. Run Llama Stack in Docker

```bash
docker run \
  -d \
  -p 5001:5001 \
  -v ~/.llama:/root/.llama \
  -v ./run.yaml:/root/run.yaml \
  llamastack/distribution-ollama \
  --yaml-config /root/run.yaml \
  --port 5001 \
  --env INFERENCE_MODEL=meta-llama/Llama-3.2-1B-Instruct \
  --env OLLAMA_URL=http://host.docker.internal:11434
```

## Running the Example

### 1. Execute the Script

```bash
python ollama_custom_tool.py
```

### 2. Expected Output

You should see a mock response from the `StoryTeller` tool, similar to:

```
mock response from tool story_teller for test_story
```

## About

This project demonstrates how to integrate a custom tool into the Llama Stack and configure an agent. The custom tool `StoryTeller` takes a parameter `story_name` and returns a mock response. This example is tested on:

- Python 3.13.1
- Device: Apple M3 Pro
- macOS: Sonoma 14.6.1

For any questions or issues, please refer to the [Llama Stack GitHub Repository](https://github.com/meta-llama/llama-stack) or raise an issue in this repository.