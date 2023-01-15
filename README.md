# Reddit text data
This pipeline -
1. Scraps a given reddit sub and stores it into a document store.
2. Cleans the scrapped data and stores it in a relational table.
3. Extracts sentiment analysis of the text.
4. Displays sentiment score of a given comment on a streamlit app.

## Tools used
- Apache Spark
- Streamlit
- MongoDB
- HDFS

## Issues
- After running docker compose file to create spark container if you are unable to open spark UI, then it is 
because port mapping has not been set up correctly in the docker compose file. You need to set 1 port for master
and 1 for spark UI. Refer to this link - https://stackoverflow.com/questions/70891552/why-is-my-spark-web-interface-not-active