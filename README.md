# MLflow tracking server с нормальными хранилищами  

> Вдохновлено [этим](https://github.com/9dogs/mlflow-minio-test)

**Ссылочки:**
- [MinIO docs](https://docs.min.io/)
- [MLflow docs](https://mlflow.org/docs/latest/index.html)
- [PostgreSQL on DockerHub](https://hub.docker.com/_/postgres)

**Что делаем:**
1. `docker-compose up -d`  
2. на MinIO создать bucket с именем `mlflow-artifacts`. Можно в браузере, на [127.0.0.1:9000](http://127.0.0.1:9000) (один раз нужно, дальше сохранится в volume)  
3. при обращении к MLflow из питона нужно определять переменные среды:  
    * MLFLOW_S3_ENDPOINT_URL=http://127.0.0.1:9000  
    * ARTIFACT_ROOT=s3://mlflow-artifacts/  
    * AWS_ACCESS_KEY_ID=mlflow_access_key  
    * AWS_SECRET_ACCESS_KEY=mlflow_secret_key  

> _Шаг 3 нужен потому, что клиент напрямую в MinIO долбится. А MLflow-сервер туда смотрит только потом, для отображения всякого_

**Получаем:**
* [MinIO](http://127.0.0.1:9000)  
* [MLflow](http://127.0.0.1:5000)  
