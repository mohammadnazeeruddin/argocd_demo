FROM python:3.8.6-slim

ARG DAGSTER_VERSION=0.11.7

RUN apt-get update -yqq && \
    apt-get install -yqq cron

RUN pip install \
    dagster==${DAGSTER_VERSION} \
    dagster-graphql==${DAGSTER_VERSION} \
    dagster-postgres==${DAGSTER_VERSION} \
    dagster-cron==${DAGSTER_VERSION} \
    dagster-celery[flower,redis,kubernetes]==${DAGSTER_VERSION} \
    dagster-aws==${DAGSTER_VERSION} \
    dagster-k8s==${DAGSTER_VERSION} \
    dagster-celery-k8s==${DAGSTER_VERSION} \
    dagit==${DAGSTER_VERSION}
    
COPY pipeline.py . /

EXPOSE 3000

ENTRYPOINT ["dagit", "-h", "0.0.0.0", "-p", "3000"]
