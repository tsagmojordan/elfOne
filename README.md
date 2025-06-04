# Food Search App

   This project is a food search application using Spring Boot and Solr for indexing and searching food items.

   ## Prerequisites
   - Docker and Docker Compose installed
   - Ports 8086 and 8999 available

   ## Setup Instructions
   1. Extract the submission archive:
      ```bash
      tar -zxvf food-search-app-soumission.tar.gz
      cd food-search-app-soumission
      ```
   2. Load the Docker images:
      ```bash
      docker load -i food-search-app-solr3.tar
      docker load -i food-search-app-app2.tar
      ```
   3. Run the application:
      ```bash
      docker-compose up
      ```
   4. Access the application:
      - Web app: `http://localhost:8086`
      - Solr admin: `http://localhost:8996`

   ## Testing
   - Search for "UHT Whole Milk" on `http://localhost:8086` to test the search functionality or search one the foods of my food list in my ontology 
   - Check Solr collection at `http://localhost:8995/solr/#/~cores/food_collection/query` with query `q=*:*`.

   ## Directory Structure
   - `docker-compose.yml`: Docker Compose configuration
   - `food-search-app-solr3.tar`: Solr Docker image
   - `food-search-app-app2.tar`: Spring Boot application Docker image
   - `dishes.json`: Data file for indexing
   - `solr-config/`: Solr configuration files
   - `init-solr.sh`: Solr initialization script
   - `images/`: Directory containing image files# food-searchapp
