# Ontology-Based Search Engine Application

## Overview
This application is a web-based search engine that leverages an ontology (defined in `ontology.ttl`) to enable semantic searches for food, dishes, diseases, and related entities. It is built using Spring Boot with Thymeleaf for the frontend and Apache Solr as the backend for indexing and querying the ontology data. The application is containerized using Docker and Docker Compose for easy deployment and scalability.

## Prerequisites
- **Docker**: Ensure Docker is installed on your system.
- **Docker Compose**: Ensure Docker Compose is installed for managing multi-container setups.
- **Java**: Required for Spring Boot (included in the Docker container).
- **Apache Solr**: Used for indexing and searching ontology data (containerized).
- **Ontology File**: The `ontology.ttl` file containing the RDF/OWL ontology for food, dishes, diseases, and related entities.

## Setup and Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd <repository-directory>
```

### 2. Directory Structure
- `ontology.ttl`: The ontology file defining classes, properties, and individuals.
- `src/`: Spring Boot application source code.
- `docker-compose.yml`: Docker Compose configuration for the app and Solr.
- `Dockerfile`: Docker configuration for building the Spring Boot app image.

### 3. Configure Solr
- Ensure the `ontology.ttl` file is placed in a directory accessible to the Solr container.
- Solr is configured to index the ontology data. Update the Solr schema (e.g., `schema.xml` or managed schema) to include fields for entities like `Food`, `Dish`, `Disease`, `Symptoms`, `Prevention`, and properties like `composedOf`, `hasrecipe`, etc.

### 4. Build and Run with Docker Compose
Run the following command to build and start the application and Solr containers:
```bash
docker-compose up --build
```
- **Spring Boot App**: Runs on `http://localhost:8099`.
- **Solr Admin**: Accessible at `http://solr:8983/solr`.

### 5. Stop the Application
To stop the containers, run:
```bash
docker-compose down
```

## Usage
The application provides a web interface powered by Thymeleaf, allowing users to perform semantic searches on the ontology data stored in Solr. Enter search queries in the search bar to find foods, dishes, diseases, and related information.

## Example Searches
Below are examples of searches you can perform with this application:

### 1. Search for Dishes by Ingredient
- **Query**: "dishes with banana"
- **Description**: Finds dishes that contain banana as an ingredient.
- **Expected Results**:
      - Banana Porridge Plain
      - Banana Porridge with Fish
      - Banana Porridge with Meat
      - Banana Porridge with Meat Spinach
      - Banana with Cashew Nut
      - Banana with Coconut Milk
      - Banana with Kidney Beans
      - Banana with Meat

### 2. Search for Dishes by Region
- **Query**: "dishes from Africa"
- **Description**: Retrieves dishes associated with the "Africa" or "CoastalAfrica" regions.
- **Expected Results**:
      - Banana Porridge Plain
      - Banana Porridge with Fish
      - Banana Porridge with Meat
      - Banana Porridge with Meat Spinach
      - Banana with Cashew Nut
      - Banana with Kidney Beans
      - Sweet Potato Fresh-AP
      - Sweet Potato Fresh-EP
      - Sweet Potato Red-Orange
      - Taro - Raw
      - Watermelon Pulp Fresh
      - Yam

### 3. Search for Dishes by Nutrients
- **Query**: "dishes with protein and fiber"
- **Description**: Finds dishes composed of both protein and fiber nutrients.
- **Expected Results**:
      - Banana Porridge with Fish
      - Banana Porridge with Meat
      - Banana Porridge with Meat Spinach
      - Banana with Cashew Nut
      - Banana with Kidney Beans
      - Banana with Meat
      - Turkey Meat Only Raw
      - Whole Fresh Egg

### 4. Search for Disease Information
- **Query**: "breast cancer symptoms"
- **Description**: Retrieves symptoms associated with Breast Cancer.
- **Expected Results**:
      - A lump in the breast or underarm
      - Change in size or shape of the breast
      - Dimpling or puckering of the skin

### 5. Search for Prevention Strategies
- **Query**: "prevention for ovarian cancer"
- **Description**: Lists prevention methods for Ovarian Cancer.
- **Expected Results**:
      - Regular pelvic exams
      - Risk-reducing surgery for high-risk women

### 6. Search for Treatment Options
- **Query**: "treatment for endometrial cancer"
- **Description**: Finds treatment protocols for Endometrial Cancer.
- **Expected Results**:
      - Chemotherapy
      - Hormone therapy

### 7. Search for Recipes
- **Query**: "recipe for sweet potato"
- **Description**: Retrieves recipes for dishes involving sweet potatoes.
- **Expected Results**:
      - Sweet Potato Fresh-AP Recipe: "Wash sweet potatoes with skin, boil for 20-25 minutes until soft."
      - Sweet Potato Fresh-EP Recipe: "Peel sweet potatoes, cube edible portion, and roast at 200°C for 25 minutes."
      - Sweet Potato Red-Orange Recipe: "Peel sweet potatoes, cube, and boil for 15-20 minutes until tender."

## Notes
- **Search Tips**: Use keywords like "dishes," "recipe," "from," "with," "symptoms," "prevention," or "treatment" to refine your search.
- **Solr Indexing**: Ensure the ontology data is properly indexed in Solr. You may need to create a script to parse `ontology.ttl` and load it into Solr.
- **Customization**: Modify the Spring Boot controllers and Thymeleaf templates in `src/main/java` and `src/main/resources/templates` to adjust search functionality or UI as needed.

## Troubleshooting
- **Solr Not Responding**: Check if the Solr container is running (`docker ps`) and verify the port `8983` is accessible.
- **No Results**: Ensure the ontology data is correctly indexed in Solr and the search query matches the indexed fields.
- **Docker Issues**: Check logs with `docker-compose logs` for errors in the app or Solr containers.

## Contributing
Feel free to submit issues or pull requests to improve the application. Focus areas include enhancing search accuracy, adding new query types, or improving the UI.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.