## Information


```bash
pip install -r requirements.txt

```

## Steps

`write_csv_to_postgres.py`-> gets a csv file from a URL. Saves it into the local working directory as [churn_modelling.csv](https://raw.githubusercontent.com/dogukannulu/datasets/master/Churn_Modelling.csv). After reading the csv file, it writes it to a local PostgreSQL table

`create_df_and_modify.py` -> reads the same Postgres table and creates a pandas dataframe out of it, modifies it. Then, creates 3 separate dataframes.

`write_df_to_postgres.py` -> writes these 3 dataframes to 3 separate tables located in Postgres server. 



## Apache Airflow:

Run the following command to clone the necessary repo on your local

```bash
git clone https://github.com/dogukannulu/docker-airflow.git
```
After cloning the repo, run the following command only once:

```bash
docker build --rm --build-arg AIRFLOW_DEPS="datadog,dask" --build-arg PYTHON_DEPS="flask_oauthlib>=0.9" -t puckel/docker-airflow .
```

Then change the docker-compose-LocalExecutor.yml file with the one in this repo and add requirements.txt file in the folder. This will bind the Airflow container with Kafka container and necessary modules will automatically be installed:

```bash
docker-compose -f docker-compose-LocalExecutor.yml up -d
```

Now you have a running Airflow container and you can reach out to that on `https://localhost:8080`

## PostgreSQL

I am using a local Postgres Server and installed `PgAdmin` to control the tables instead of using `psql`. I defined the necessary info to access to Postgres server in .zshrc (if MacOS).
