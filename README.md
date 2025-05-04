# Knowledge Graph-Enhanced RAG System for Crime Film Insights and Analysis

## 1. Project Title and Abstract

**Project Title:** Knowledge Graph-Enhanced RAG System for Crime Film Insights and Analysis

**Abstract:** This project introduces a Knowledge Graph and Retrieval-Augmented Generation (KG-RAG) system designed for question answering (QA) in crime movies. By applying KG-RAG to crime film scripts, the system enables in-depth understanding of crime cinema, supporting nuanced, open-ended, and non-factual questioning beyond simple fact retrieval. The system integrates structured knowledge graphs with advanced generative retrieval techniques to provide a framework for rich, context-driven film analysis.


## 2. Table of Contents

1. [Project Title and Abstract](#1-project-title-and-abstract)  
2. [Table of Contents](#2-table-of-contents)  
3. [Introduction](#3-introduction)  
4. [Problem Statement](#4-problem-statement)  
5. [Proposed Solution / Methodology](#5-proposed-solution--methodology)  
6. [Dataset](#6-dataset-if-any)  
7. [Installation Instructions](#7-installation-instructions)  
8. [Project Structure](#8-project-structure)  
9. [Code Workflow](#9-code-workflow)  
10. [Results and Analysis](#10-results-and-analysis)  
11. [Limitations and Future Work](#11-limitations-and-future-work)  
12. [Contributors](#12-contributors)


## 3. Introduction

Large Language Models (LLMs) have revolutionized Natural Language Processing (NLP) by enabling generative reasoning and sophisticated text generation. However, LLMs often generate hallucinations and require costly retraining to update knowledge Retrieval-Augmented Generation (RAG) has emerged as a promising approach to mitigate these issues by incorporating external knowledge retrieval. This project aims to enhance semantic understanding in movie narratives by integrating structured Knowledge Graphs with RAG. This integration is designed to capture intricate character dynamics, evolving plot arcs, and implicit themes typical in crime films, providing a flexible, context-driven framework for film analysis.

Traditional NLP methods struggle with complex narrative domains like crime films due to:
- Nuanced character dynamics
- Evolving plot structures
- Implicit themes and symbolism

Our KG-RAG system combines:
- **Knowledge Graphs** for structured relationship mapping
- **Vector Retrieval** for semantic understanding
- **LLM Reasoning** for contextual answer generation

## 4. Problem Statement

Traditional methods for question answering fall short when applied to complex narrative domains like crime films. These approaches struggle to capture the nuanced character dynamics, evolving plot structures, implicit themes, and emotional undertones central to cinematic storytelling. The project addresses these limitations by integrating a structured Knowledge Graph with a Retrieval-Augmented Generation (KG-RAG) framework, enabling richer, context-driven narrative analysis that goes beyond surface-level fact retrieval and supports open-ended, nuanced exploration of film content.

## 5. Proposed Solution / Methodology

Our project employs a Knowledge Graph-Retrieval Augmented Generation (KG-RAG) system. This approach is specifically designed to enhance how we can ask questions about and understand the intricate details within crime movies. It works by combining the strengths of two powerful techniques: Knowledge Graphs and Retrieval-Augmented Generation. Let's break down the steps involved:

1.  **Entity Extraction:**
    * The process begins by identifying the most important elements within the movie script. These "entities" are the key players, locations, objects, and significant events that drive the story.
    * A Large Language Model (LLM) is used to scan the script and pinpoint these entities. For example, in "The Godfather Part I," entities like "Michael Corleone," "Vito Corleone," "New York City," and "the Corleone family" would be identified.

2.  **Context Retrieval - A Dual Approach:**
    * Once the relevant entities from a user's question are known, the system searches for related information from two distinct but complementary sources: the Knowledge Graph and a Vector Database.
    * **2.1. Knowledge Graph Retrieval:** The Knowledge Graph is a structured network of information where entities are connected by relationships. For instance, it might store facts like "Michael Corleone is the son of Vito Corleone" or "The Corleone family operates in New York City." When a question touches upon these relationships, the system queries the Knowledge Graph to retrieve these precise, structured facts.
    * **2.2. Vector Database Retrieval:** The Vector Database contains the movie script broken down into smaller segments or chunks. Each of these chunks is converted into a numerical representation called an "embedding," which captures its semantic meaning. When a user asks a question, the same process is applied to the question, and the Vector Database is searched for script chunks that have similar embeddings. This allows the system to retrieve broader contextual information from the script that might not be explicitly stated as a direct fact in the Knowledge Graph.
    * **2.3. Context Fusion:** The information retrieved from both the Knowledge Graph (structured facts) and the Vector Database (contextual script snippets) is then combined. This merged information provides a more comprehensive understanding for the next step.

3.  **Reasoning and Generation with an LLM:**
    * The combined context is then fed into a Large Language Model (LLM).
    * The LLM's role is to analyze this information in relation to the original question and generate a well-informed answer. By having access to both structured knowledge and broader textual context, the LLM can produce more accurate, detailed, and nuanced responses compared to systems that only use one of these information sources.
    * The LLM can also provide a rationale for its answer, often by referencing the specific pieces of information it used from the retrieved context.

In summary, our KG-RAG system aims to provide a deeper level of understanding and more insightful answers when analyzing crime films by intelligently integrating structured knowledge with relevant textual context and leveraging the reasoning capabilities of Large Language Models.

## 6. Dataset

The dataset utilized in this project is derived from the full movie script of *The Godfather Part I*.

-   **Source:** The complete screenplay of the film *The Godfather Part I* served as the primary data source.
-   **Structure:** To evaluate the system's capabilities across different types of reasoning, a set of 50 question-answer (QA) pairs was manually created and annotated. These QA pairs are categorized into the following five types:
    -   **Factual Analysis:** Questions requiring direct retrieval of information explicitly stated in the script.
    -   **Inferential:** Questions that necessitate reasoning and drawing conclusions based on the information provided in the script.
    -   **Comparative/Relational:** Questions that ask for comparisons between entities or the identification of relationships between them.
    -   **Causal/Temporal:** Questions concerning cause-and-effect relationships and the sequence of events within the narrative.
    -   **Dialogue Analysis:** Questions focusing on the meaning, context, and implications of specific lines of dialogue.
-   **Sample QA Pair:**

    ```
    Category: Dialogue Analysis
    Question: Meaning of "I'm gonna make him an offer he can't refuse"?
    Answer: Implies force/threats will ensure compliance.
    ```

-   **Access:** The annotated dataset is publicly available on [Zenodo](https://zenodo.org/records/14894805).
  
## 7. Installation Instructions

1.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt  # or use your preferred package manager
    ```
3.  **Set up environment variables:**
    * Create a `.env` file in the project root.
    * Add the following variables:
        ```
        NEO4J_URI=<Your_Neo4j_URI>
        NEO4J_USERNAME=<Your_Neo4j_Username>
        NEO4J_PASSWORD=<Your_Neo4j_Password>
        ```
4.  **Run Ollama (if required):**
    * Ensure Ollama is installed and running.  You might need to pull the required models:
        ```bash
        ollama pull llama3.1
        ollama pull mxbai-embed-large
        ```
5.  **Run the code:**
    ```bash
    python code.py  # or however you execute the script
    ```

## 8. Project Structure
```
├── README.md          <- This file
├── code.ipynb         <- The main Python Notebpok containing the KG-RAG implementation.
├── code.py            <- The main Python script containing the KG-RAG implementation.
├── plot.txt           <- Movie script (dataset)
├── requirements.txt   <- Python dependencies
├── images             <- folder containing screenshots
└── .env               <- Environment variables (not committed)
```

## 9. Code Workflow

1.  **Load and Split Documents:** The movie script is loaded and split into smaller chunks.
2.  **Initialize LLM and Graph Transformer:** A Large Language Model (LLM) and a graph transformer are initialized.
3.  **Convert Documents to Graph Format:** The script is converted into a graph-compatible format.
4.  **Add Graph Documents to Neo4j:** The graph data is added to a Neo4j graph database.
5.  **Create Fulltext Index:** A fulltext index is created in Neo4j for efficient entity searching.
6.  **Define Entity Extraction Model and Prompt:** A model and prompt are defined to extract entities from questions.
7.  **Fulltext Query Generation and Graph Retrieval:** Functions are defined to generate fulltext queries and retrieve information from the graph.
8.  **RAG Pipeline:** The RAG pipeline is set up to retrieve relevant context and generate answers using the LLM.
9.  **Evaluation:** The system's performance is evaluated using predefined metrics.

## 10. Results and Analysis

The evaluation was carried out on 50 queries across several categories, including Factual Analysis, Inferential, Comparative and Relational, Causal and Temporal, and Dialogue Analysis. The KG-RAG system demonstrates strengths in hybrid retrieval power, effectiveness on complex queries, and hallucination mitigation.  Specific metrics and detailed analysis can be found in the research paper and presentation.

## 11.Graph Visualization

You can visualize the graph present in the `images` folder using the [yEd Live](https://www.yworks.com/yed-live/) website.

Alternatively, experience it live by clicking the link below:

👉 [View Graph Live on yEd](https://www.yworks.com/yed-live/?file=https://gist.githubusercontent.com/MusadiqPasha/783e702c4055dee3e6cd62427b28a6be/raw/488ecfbe31008744317604cfdc94820f1acff12c/viz)


## 12. Limitations and Future Work

-   Further improvement in retrieval mechanisms.
-   Broader application testing across different film genres.
-   Addressing challenges in handling highly ambiguous queries.
-   Exploring more advanced graph analysis techniques.

## 13. Contributors

-   K Musadiq Pasha 
-   Tejas V Bhat 
-   K Bhavish Raju 
-   Ayush Muralidharan 
