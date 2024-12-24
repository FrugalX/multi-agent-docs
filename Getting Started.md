# Getting Started with Your Multi-Agent AI System Project

This document will help you set up a foundation for working with multi-agent AI systems using LLMs (Large Language Models). It’s designed for undergrad students who may be new to LLM APIs and AI agents. The scope of this guide is limited to Google’s Gemini AI and Llama 2 via Hugging Face APIs, both of which offer free-tier access for experimentation.

## Prerequisites

Before starting, ensure you have the following:
- **Basic Programming Knowledge**: Familiarity with JavaScript and Node.js.
- **Git and GitHub**: For version control and collaboration.
- **An IDE or Code Editor**: Such as VS Code.
- **Google Cloud Account**: For accessing Gemini AI APIs.
- **Hugging Face Account**: For experimenting with Llama 2 APIs.

## Key Concepts to Understand

- **LLMs (Large Language Models)**: These are AI systems trained to understand and generate human-like text.
- **Agents**: Programs that perform tasks autonomously, often powered by LLMs.
- **Task Decomposition**: Breaking a high-level goal into smaller sub-tasks for agents to execute.

## Step 1: Set Up Your Environment

1. **Install Node.js and npm**:
   - Download and install Node.js from [https://nodejs.org/](https://nodejs.org/).
   - Verify installation:
     ```bash
     node -v
     npm -v
     ```

2. **Set Up a Project Directory**:
   - Create a folder for your project and initialize it:
     ```bash
     mkdir multi-agent-ai
     cd multi-agent-ai
     npm init -y
     ```

3. **Install Required Packages**:
   - Install `axios` for making API requests:
     ```bash
     npm install axios
     ```
   - Install `dotenv` for managing environment variables:
     ```bash
     npm install dotenv
     ```

4. **Set Up Environment Variables**:
   - Create a `.env` file in your project directory:
     ```plaintext
     GOOGLE_API_KEY=your-google-api-key
     HF_API_KEY=your-hugging-face-api-key
     ```

## Step 2: Choose an LLM Provider

You can choose between Google’s Gemini AI or Hugging Face’s Llama 2 API.

### Option 1: Google Gemini AI

1. **Set Up Google Cloud**:
   - Create a Google Cloud account and activate the free trial with $300 credits.
   - Enable the Vertex AI API.

2. **Access the Gemini Model**:
   - Use the Vertex AI Generative AI Studio to experiment with the Gemini model.

3. **Example: Using Gemini with Node.js**:
   ```javascript
   const axios = require('axios');

   const apiKey = process.env.GOOGLE_API_KEY;
   const endpoint = 'https://us-central1-aiplatform.googleapis.com/v1/projects/your-project-id/locations/us-central1/models/text-bison@001:predict';

   async function generateText(prompt) {
       const response = await axios.post(endpoint, {
           instances: [{ content: prompt }],
       }, {
           headers: {
               'Authorization': `Bearer ${apiKey}`,
               'Content-Type': 'application/json',
           },
       });
       console.log(response.data.predictions[0].content);
   }

   generateText('What is AI?');
   ```

### Option 2: Llama 2 on Hugging Face

1. **Set Up Hugging Face Account**:
   - Create a Hugging Face account and generate a free API key.

2. **Access the Llama 2 Model**:
   - Use the Hugging Face Inference API to send requests to the Llama 2 model.

3. **Example: Using Llama 2 with Node.js**:
   ```javascript
   const axios = require('axios');

   const apiKey = process.env.HF_API_KEY;
   const endpoint = 'https://api-inference.huggingface.co/models/meta-llama/Llama-2-7b-chat-hf';

   async function generateText(prompt) {
       const response = await axios.post(endpoint, {
           inputs: prompt,
       }, {
           headers: {
               'Authorization': `Bearer ${apiKey}`,
               'Content-Type': 'application/json',
           },
       });
       console.log(response.data.generated_text);
   }

   generateText('Explain machine learning in simple terms.');
   ```

## Step 3: Experiment with Similar Systems

Before diving deep into your project, take time to understand how similar multi-agent systems work. Here are some examples:

- **AutoGPT**: An open-source project that uses LLMs to autonomously perform tasks based on a given goal.
- **HuggingGPT**: A framework integrating LLMs with tools for task execution.

## Step 4: Start Small

- Begin by creating simple programs that make API requests to LLMs and process their responses.
- For example, build a chatbot that takes user input, sends it to the API, and displays the AI-generated response.

## Step 5: Expand Towards the Project Goals

Once you’re comfortable with basic API usage:
- Implement a task manager to handle task creation and decomposition.
- Use event-driven workflows to trigger agent actions based on task completion.
- Gradually integrate the components into a cohesive multi-agent system.

## Resources

- [Google Cloud Vertex AI](https://cloud.google.com/vertex-ai)
- [Hugging Face Llama3](https://huggingface.co/docs/transformers/en/model_doc/llama3)
- [Hugging Face JS Libraries](https://huggingface.co/docs/huggingface.js/en/index)
- [AutoGPT GitHub Repository](https://github.com/Torantulino/Auto-GPT)

---

Feel free to reach out if you have questions or need clarification!
