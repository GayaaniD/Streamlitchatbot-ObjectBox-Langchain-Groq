# On-Device AI for Streamlit Applications with ObjectBox, Langchain, and Groq
![image](https://github.com/GayaaniD/Streamlitchatbot-ObjectBox-Langchain-Groq/assets/125920863/a1201310-4a2d-409f-a740-3fbe0de7f1c6)

In the realm of web applications, data is king. Efficient data management is crucial for seamless user experience, and this becomes especially pertinent when dealing with on-device AI applications. This project explores a powerful combination of technologies: ObjectBox, Langchain, and Groq, to empower Streamlit applications with efficient on-device data processing and retrieval.

## ObjectBox : The Speedy On-Device Database
[ObjectBox](https://objectbox.io/) is a lightweight, open-source database solution designed specifically for embedded devices, mobile applications, and the Internet of Things (IoT). It has integration with multiple coding programming languages. Any app is only as good as its data. The on device objectbox database ensures data is smoothly available when and where needed. No internet? No cloud? No worries. ObjectBox is a super fast database and synchronization solution, built uniquely for Embedded Devices, Mobile and IoT.

It shines in resource-constrained environments due to its compact size (under 1MB) and exceptional efficiency in CPU, memory, and battery usage. ObjectBox adheres to the ACID (Atomicity, Consistency, Isolation, Durability) properties, ensuring data integrity and reliability. Additionally, its developer-friendly nature makes integration and implementation a breeze.

## Project Flow : A Streamlit Application for On-Device Search
1. Data Ingestion and Preprocessing :
  - The ```PyPDFDirectoryLoader``` facilitates loading all PDFs from a designated directory.
  - The ```RecursiveCharacterTextSplitter``` divides the documents into manageable chunks for efficient processing.
    
2. Vector Embedding and ObjectBox Integration :
  - The ```OpenAIEmbeddings``` class is used to generate vector representations (embeddings) for the chunked text. It is quicker and accurate one.
  - The ```ObjectBox.from_documents``` function stores these embeddings within the ObjectBox database, enabling efficient retrieval based on semantic similarity.

3. User Input and Retrieval Chain Creation :
  - The Streamlit interface allows users to input their search queries.
  - A retrieval chain is constructed by combining the document chain (powered by Langchain and the Groq LLM) with a retriever object built on top of the ObjectBox vector store.

4. Search and Response :
  - Upon receiving a user query, the retrieval chain searches the ObjectBox database for relevant document chunks based on semantic similarity.
  - The most pertinent context and answer are retrieved and displayed within the Streamlit app.


## How to Run the Project
1. Clone the GitHub repository.
2. Rename the `.env.example` file to `.env` and add your API keys.
3. Install the project dependencies by running the `requirements.txt` file. You can do this by opening your terminal and typing:
    ```
    pip install -r requirements.txt
    ```
4. After the dependencies are installed, you can run the project using;
   ```
   streamlit run app.py
   ```
   
## User Interface
![image](https://github.com/GayaaniD/Streamlitchatbot-ObjectBox-Langchain-Groq/assets/125920863/b5b59b25-1d98-4100-921b-272ab40815e5)

## Response and Conclusion
![image](https://github.com/GayaaniD/Streamlitchatbot-ObjectBox-Langchain-Groq/assets/125920863/a9e638e4-2347-4569-a68d-b20eb6de71f3)
  - **Response time : 0.046875**

  - **Because of groq inferencing engine, the response is fast and best thing is that from document embedding how quickly we are able to get the relevant context. It is because of objectbox database.**

## The Beauty of On-Device AI :
This approach offers several advantages:

  - Offline Functionality : The application can function without an internet connection, as all data processing and retrieval occur on the device itself.
  - Privacy Preservation : Sensitive user data remains on the device, eliminating privacy concerns associated with cloud-based storage and processing.
  - Efficiency and Speed : On-device processing significantly reduces latency compared to cloud-based solutions.
