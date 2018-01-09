# Big Data Pipeline

* Implemented a high-performance ingestion layer that extracts and transforms data at 200 kmsg/s. (Apache Kafka, Zookeeper)
* Built a back-end server that processes and analyzes stock data in real time. (Python)
* Imported stock information from Google Finance using the googlefinance Python module.
* Stored time series data using Apache Cassandra, and Redis as Cache when queried.
* Developed a data stream pipeline that streams data from Kafka, performs computations, and writes back to Kafka. (Spark)
* Built a front-end dashboard to visualize stock prices and moving averages in real time. (Redis, Node.js, and smoothie.js)
* Created a scalable cloud deployment environment using Docker, Apache Mesos.


# Final Webpage
![goog](https://user-images.githubusercontent.com/15081532/34710180-1763b4fa-f4cf-11e7-8539-caab561d9dea.png)
![amzn](https://user-images.githubusercontent.com/15081532/34710184-19378b44-f4cf-11e7-98d4-857d84535839.png)

# How to run ?

Run flask-data-producer.py
```
export ENV_CONFIG_FILE=`pwd`/config/dev.cfg
python flask-data-producer.py
```
Run stream-processing.py
```
spark-submit --jars spark-streaming-kafka-0-8-assembly_2.11-2.0.0.jar stream-processing.py stock-analyzer average-stock-price 192.168.99.100:9092
```
Run redis-publisher.py
```
python redis-publisher.py average-stock-price 192.168.99.100:9092 average-stock-price 192.168.99.100 6379
```
Start the webpage server
```
node index.js --port=3000 --redis_host=192.168.99.100 --redis_port=6379 --subscribe_topic=average-stock-price
```
