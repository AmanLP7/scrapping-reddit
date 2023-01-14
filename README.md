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