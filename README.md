# Python Django Elasticsearch
#### A PoC to integrate Django REST Framework (DRF) with Elasticsearch 

- Elasticsearch is a distributed, open-source search and analytics engine. 
It is designed for horizontal scalability, reliability, and easy management. Elasticsearch is used for full-text search, structured search, analytics, and all in real time. It stores and indexes data in a scalable way, and it can search and analyze that data at speed. Elasticsearch is typically used for log and event data analysis, full-text search, and operational intelligence use cases.
---

### Want to use this project?

1. Fork/Clone

2. [Install Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/8.11/docker.html) if you haven't already and make sure it is running on port `9200`. Make sure to update the `ELASTICSEARCH_DSL` config in *core/settings.py*.

    or 
   
   Run Elasticsearch on docker container:

    ```
    $ docker pull docker.elastic.co/elasticsearch/elasticsearch:7.15.2
    $ docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.15.2
    ```

3. Create and activate a virtual environment:

    ```sh
    $ python3.10 -m venv myenv && source venv/bin/activate
    ```

4. Install the requirements:

    ```sh
    (venv)$ pip install -r requirements.txt
    ```

5. Apply the migrations:

    ```sh
    (venv)$ python manage.py migrate
    ```

6. Populate the database with some test data by running the following command:

    ```sh
    (venv)$ python manage.py populate_db
    ```

7. Create and populate the Elasticsearch index and mapping:

    ```sh
    (venv)$ python manage.py search_index --rebuild
    ```

8. Run the server

    ```sh
    (venv)$ python manage.py runserver
    ```

9. Test Elasticsearch with the following queries:

     - [http://127.0.0.1:8000/search/user/mike/](http://127.0.0.1:8000/search/user/mike/) - should find the user 'mike13'
     - [http://127.0.0.1:8000/search/user/jess_/](http://127.0.0.1:8000/search/user/jess_/) - should find the user 'jess_'
     - [http://127.0.0.1:8000/search/category/seo/](http://127.0.0.1:8000/search/category/seo/) - should find the category 'SEO optimization'
     - [http://127.0.0.1:8000/search/category/progreming/](http://127.0.0.1:8000/search/category/progreming/) - should find the category 'Programming' (:warning: notice the typo)
     - [http://127.0.0.1:8000/search/article/linux/](http://127.0.0.1:8000/search/article/linux/) - should find the article 'Installing the latest version of Ubuntu'
     - [http://127.0.0.1:8000/search/article/java/](http://127.0.0.1:8000/search/article/java/) - should find the article 'Which programming language is the best?'
