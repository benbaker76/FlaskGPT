# FlaskGPT

FlaskGPT is a minimal ChatGPT clone that leverages the `langchain` library to provide an interactive graphical user interface (GUI) for querying a JSON file, specifically the `resume.json` file from the [resume.json](https://jsonresume.org) project. This project is indebted to [Thomas Davis](https://github.com/thomasdavis) for the use of his `resume.json` file.

The main objective of FlaskGPT is to enable users to ask questions interactively using a Large Language Model (LLM) in combination with the `resume.json` file, which has been converted into a vector database. The project is implemented using Flask and is designed to work with an OpenAI model or a Llama2-based LLM model (gguf file format).

## Credits

FlaskGPT is inspired by the work of [Himanshu Sekhar Das](https://github.com/himanshu662000) on [InfoGPT](https://github.com/himanshu662000/InfoGPT), a similar project built using Streamlit. While InfoGPT offers a more extensive feature set and supports a wider range of file formats, FlaskGPT aims to provide a minimalistic and Flask-based alternative.

## Features

- Interactive GUI for querying the `resume.json` file.
- Utilizes a Large Language Model (LLM) to generate responses.
- Supports the OpenAI API and the Llama2-based LLM model (gguf files only).
- Real-time token output using Server-Sent Events (SSE).

## Screenshot

![FlaskGPT](/images/FlaskGPT.png)

## Getting Started

1. Clone the repository:

   ```shell
   git clone https://github.com/benbaker76/FlaskGPT.git
   cd FlaskGPT
   ```

2. I recommend using a virtual environment:

   ```shell
   python -m venv .venv
   source .venv/bin/activate
   ```

3. Install the required dependencies:

   ```shell
   pip install -r requirements.txt
   ```

4. Set up your OpenAI API credentials by following the instructions in the [OpenAI documentation](https://platform.openai.com/docs/guides/authentication). Make sure your `OPENAI_API_KEY` environment variable is set.

   ```shell
   export OPENAI_API_KEY=<your secret key>
   ```

5. Start the Flask server:

   ```shell
   python3 FlaskGPT.py
   ```

6. Access the FlaskGPT GUI by opening a web browser and navigating to `http://localhost:5000`.

## Usage

1. Launch the FlaskGPT GUI as described in the "Getting Started" section.
2. Use the interface to ask questions based on the `resume.json` file.
3. Enjoy real-time token output and responses from the Large Language Model.

## How Does it Work?

This work is based on the principle of Retrieval Augmentation Generation (RAG) which is an approach in the field of Natural Language Processing (NLP) that combines three key components: retrieval, augmentation, and generation. This approach is designed to improve the performance and capabilities of language models.

![RAG Diagram](/images/RAG_diagram.png)

Token Limits: Vector databases play a crucial role in enabling large language models (LLMs) to manage extensive data within token constraints. These databases store and index vector representations of text, allowing LLMs to retrieve relevant segments efficiently. For instance, in this demo, the default OpenAI model, `gpt-3.5-turbo`, has a maximum context length of 4097 tokens. Vector databases facilitate optimal data utilization by helping LLMs produce coherent responses while working within these limitations.

Text Splitting and Embedding: In this process, we break down the document's content into smaller units that encapsulate document metadata. After dividing the document into these smaller chunks, we employ a vector embedding model to convert them into representations stored in the vector database.

Retrieval: Retrieval refers to the process of accessing and obtaining specific information or data from a database. It involves searching for and returning relevant items or documents based on user queries or criteria. 

Output Generation: Output Generation occurs after obtaining relevant context from the retriever component. This context is then used as input for the Language Model (LLM), which generates an appropriate response or answer based on the user's query. This step is crucial in providing accurate and contextually relevant responses to user queries. Langchain plays a role in chaining the llm, retriever and prompts to give the final answer which we stream through Flask ui.

## Contributing

Contributions to FlaskGPT are welcome! If you'd like to contribute, please fork the repository and create a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Links
- [baker76.com](https://baker76.com)
- [InfoGPT](https://github.com/himanshu662000/InfoGPT)
- [jsonresume.org](https://jsonresume.org)
