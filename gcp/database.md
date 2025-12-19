# Avro, Parquet, and ORC File Format Comparison

*Based on insights by Ganesh Verma*

One of the most important steps in big-data projects is selecting the right file format. When dealing with MapReduce and Spark, the primary concern is the time it takes to locate the relevant/proper information/data. This may have an effect on the overall performance of the job.

Because Hadoop uses replication to store data redundantly in order to achieve fault tolerance, the storage cost is increased as a result of this replication. Processing costs, including CPU, network, and I/O, should also be considered.

Using the correct file format for a given scenario may help us reduce these costs while improving performance.

## The Benefits of Using Appropriate File Formats
*   Faster read
*   Faster write
*   Split table files support
*   Schema evolution can be supported
*   Advanced compression can be achieved

---

## File Formats

### 1. CSV (Comma-Separated Values)
CSV files are comma-delimited files that hold data in a row-based file format. They are typically used for transmitting tabular data in CSV files, with each header/value delimited by a comma (`,`), pipe(`|`), and so on. In most cases, the first row comprises header names.

**Example Data:**
```
CustId, First Name, Last Name, City
9563218, Ganesh, Verma, Mumbai
9558120, Sanjay, Shukla, Mumbai
9558122, Vishal, Mourya, Thane
9558124, Adarsh, Singh, Thane
9558126, Pratik, Thakur, Thane
```

**Use Case:** Suitable options for using tabular data are for spreadsheet processing and human reading. Use this format for analysis, POCs, or small data sets.

### 2. PARQUET File Format
Parquet is an open-source file format for Hadoop. Parquet helps to achieve efficient storage and performance. This is a **column-oriented format**, where the values of each column of the same type in the records are stored together.

**Concept:**
If a table has `CustId`, `First_Name`, `Last_Name`, and `City`, Parquet stores all `CustId` values together, all `First_Name` values together, etc.

*   **Row-wise storage:** `9563218GaneshVermaMumbai9558120SanjayShuklaMumbai...`
*   **Column-oriented storage:** Stores columns adjacent to each other.

**Benefits:**
*   Relatively more efficient when the requirement is to fetch column-based data by querying a few columns from a table.
*   Increases query performance as it takes less time to fetch the required column value.
*   Less I/O is required as the required columns are adjacent to each other.

### 3. AVRO File Format
Avro is a popular **row-based storage format** for serialization. Avro is dependent on the schema, which is stored in JSON format, making it easy for any software to read and comprehend. Because the data is stored in binary format, it is small and efficient.

**Benefits:**
*   **Schema Evolution:** Supports dynamic data formats that change over time. It can readily manage schema changes such as missing, added, or modified fields.
*   **Data Ingestion:** Avro format is chosen for importing data lake landing because downstream systems can quickly obtain table schemas from files.
*   Good performance due to efficient serialization and deserialization properties.

### 4. ORC (Optimized Row Columnar) File Format
The Optimized Row Columnar (ORC) file format provides a highly efficient way to store data. It improves the overall performance when Hive (a SQL interface on top of Hadoop) reads, writes, and processes the data.

**Structure:**
*   **Stripes:** ORC stores collections of rows in one file, and within the collection, the row data is stored in a columnar format (default stripe size is 250 MB).
*   **Postscript:** Consists of compression parameters and compressed footer size.
*   **Stripe Footer:** Stores a directory of stream locations.
*   **Index Data:** Consists of min and max values for each column and row positions.

**Benefits:**
*   Large stripe sizes help in achieving large, efficient reads from HDFS.
*   Relatively more compression-efficient than other file formats.

### 5. Feather File Format
This is a portable file format used for storing Arrow tables or data frames (Python/R) which utilizes the Arrow IPC format.

**Key Features:**
*   Designed for transporting large quantities of data in chunks.
*   Fast, lightweight, and easy-to-use binary file format.
*   **Compression:** Feather V2 supports LZ4 and ZSTD compression.
*   **Performance:** High read and write performance, bound by local disk performance. Supports random access and slicing from the middle.

---

## Comparison Summary

| Feature | CSV | Parquet | ORC | Avro | Feather |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Type** | Row-based (Text) | Column-oriented | Hybrid (Row/Column) | Row-based | Column-oriented (Arrow) |
| **Schema Evolution** | Poor | Good | Good | **Excellent** | Good |
| **Compression** | Poor | **Excellent** | **Excellent** | Good | Good (LZ4/ZSTD) |
| **Read Performance** | Slow | Fast (Columnar queries) | Fast (Hive) | Good | **Very Fast** (Local) |
| **Best Use Case** | Human readable, small data | Spark, Analytical queries | Hive, HDFS Storage | Kafka, Data Ingestion | Python/R Data Frames |

*   **CSV:** Easier to use, human-readable, widely used for small tabular data. Too slow for data lakes.
*   **Parquet/ORC:** Widely used in Hadoop. ORC is mostly used in **Hive**, Parquet is the default for **Spark**.
*   **Avro:** Best for **schema evolution** and ingestion (e.g., Kafka).
*   **Feather:** Faster read/write with SSDs; standard for data science (Python/R) intermediates.

---
### References
*   [Apache Hive LanguageManual ORC](https://cwiki.apache.org/confluence/display/hive/languagemanual+orc)
*   [Wikipedia: Comma-separated values](https://en.wikipedia.org/wiki/Comma-separated_values)
*   Feather V2 with Compression Support in Apache Arrow 0.17.0 (Ursa Labs)
