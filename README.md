## Information

```bash
pip install -r requirements.txt

```

This repo does the following steps:

1. The script write_csv_to_postgres.py gets a csv file from a URL. Saves it into the local working directory [churn_modelling.csv](https://raw.githubusercontent.com/dogukannulu/datasets/master/Churn_Modelling.csv). After reading the csv file, it writes it to a local PostgreSQL table
2. The script create_df_and_modify.py reads the same Postgres table and creates a pandas dataframe out of it, modifies it. Then, creates 3 separate dataframes.
3. The last script write_df_to_postgres.py writes these 3 dataframes to 3 separate tables located in Postgres server. 


### Airflow

The Airflow script is located under dags folder (dags/airflow_dag.py) and it runs the scripts in order.

### Docker

The Airflow and Postgres services run as containers. In the working directory, the following should run:

```bash
docker-compose up -d

```