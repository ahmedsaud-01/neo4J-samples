# IMDB Data Extraction and Neo4j Integration and Querying Neo4J using OpenAI

This project demonstrates the process of extracting data from IMDB's online databases, transforming it into a CSV file, uploading the data into a Neo4j graph database, and querying the database using a Large Language Model (LLM).

## Features

1. **Data Extraction**:  
    Extracted relevant data from IMDB's online datasets, including movies, actors, genres, and relationships available for non-commercial use from the link (https://developer.imdb.com/non-commercial-datasets/)

2. **CSV Creation**:  (Notebook: prepare-movie-data.ipynb)
    Processed and structured the extracted data into a CSV format suitable.

3. **Neo4j Integration**:  (/notebooks/prepare-movie-data.ipynb)
    - Uploaded the CSV file into a Neo4j database.  
    - Created nodes and relationships to represent the data as a graph.

4. **Querying with LLM**:  (/notebooks/query-neo4j-db-usingLLM.ipynb)
    Leveraged a Large Language Model to generate and execute Cypher queries for exploring the graph database.

## Prerequisites

- Python 3.x
- Neo4j Desktop or Neo4j Aura
- IMDB datasets (available online)
- OpenAI or similar LLM API (for querying)

## Setup Instructions

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/ahmedsaud-01/neo4J-samples.git
    cd connect-explore-graph-db-python
    ```

2. **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Extract Data**:
    - The provided notebook (prepare-movie-data.ipynb) which copies data from IMDB online files into CSV.
    - The extracted data will be saved as a CSV file in the `data/` directory.

5. **Upload to Neo4j**:
    -  The provided notebook (upload-movie-data-to-neo4j.ipynb) uploads the CSV file and creates the graph schema.

6. **Query the Database**:
    - The provided notebook (query-neo4j-db-usingLLM.ipynb) explores the LLM integration to query the database.


## Example Queries

- Find all movies directed by a specific director:
  ```cypher
  MATCH (d:Director)-[:DIRECTED]->(m:Movie)
  WHERE d.name = "Christopher Nolan"
  RETURN m.title
  ```

- List actors who acted in a specific genre:
  ```cypher
  MATCH (a:Actor)-[:ACTED_IN]->(m:Movie)-[:BELONGS_TO]->(g:Genre)
  WHERE g.name = "Sci-Fi"
  RETURN a.name
  ```

## Acknowledgments

- IMDB for providing the datasets.
- Neo4j for the graph database platform.
- OpenAI for LLM capabilities.
