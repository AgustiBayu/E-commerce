FROM apache/spark:3.5.0

USER root

WORKDIR /app

RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*

RUN curl -L -o /opt/spark/jars/postgresql-42.7.10.jar \
    https://repo1.maven.org/maven2/org/postgresql/postgresql/42.7.10/postgresql-42.7.10.jar

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN chown -R spark:spark /app

USER spark

CMD ["spark-submit","--jars","/opt/spark/jars/postgresql-42.7.10.jar","src/cmd/main.py"]