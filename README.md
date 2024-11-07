# LangChain LLM Application: Translation Service

This repository contains a laboratory on how to build a basic natural language processing application using LangChain. The application aims to translate text from English to another language using an OpenAI API-based language model.

## Description

The application performs text translation using the following steps:
1. **Language Model Creation**: Uses the OpenAI GPT-4 API to perform text translation..
2. **Prompt Templates Usage**:  A prompt template is used to structure the application's inputs and outputs.
3. **Component Chaining with LCEL**: LangChain Expression Language (LCEL) allows combining the language model, prompt templates, and parsers to generate the translation.
4. **Deployment with LangServe**: The application is served as a REST API using LangServe.

## Requirements

To run this project locally, you'll need to have the following packages installed:
- Python 3.x
- Pip o Conda
- LangChain
- LangServe
- OpenAI API Key

### Installation

```bash
pip install langchain
pip install langserve[all]
```

### Functional Testing

![image](https://github.com/user-attachments/assets/081a6bd4-cead-495c-9396-3c6432dadd9c)

![image](https://github.com/user-attachments/assets/16e47f16-b198-48d0-a8bc-0081361578e8)


### Architecture

![image](https://github.com/user-attachments/assets/6e397a21-795e-4784-ad3a-10db81e0aa0c)


1. **User**: Starts the application by sending an HTTP request with the text in English and the language to which they wish to translate it.

2. **API (FastAPI + LangServe)**:
   - The **FastAPI** server exposes a route to receive requests (`/chain`).
   - LangServe is responsible for serving the processing chain.

3. **LangChain (Translation Component)**:
   - **ChatPromptTemplate**: Creates the structured prompt to translate the text.
   - **ChatOpenAI (GPT-4)**: The OpenAI model used to perform the translation.
   - **StrOutputParser**: Extracts the model's response and returns it as text.

4. **LangSmith (Optional)**: A tool to track and debug the steps of the processing chain.

5. **Remote Client**: Can invoke the translation service programmatically, obtaining the response through the LangServe API.


