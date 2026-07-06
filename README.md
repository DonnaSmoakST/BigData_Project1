Flight Delay Analytics with Apache Spark (RDD vs. DataFrame)


A Big Data coursework project (University of Macedonia, Applied Informatics) analyzing a flight-delay dataset (flights_2000.csv) using PySpark. The project benchmarks two Spark APIs on the same aggregation task and then explores the data further through visual analysis.


Overview

The project is organized into 5 parts:


Spark RDD API: Parses raw flight records into (origin_airport, delay) pairs and computes the average departure delay per airport using low-level RDD transformations (map, filter, combineByKey).
Spark DataFrame API: Repeats the same analysis using Spark's structured DataFrame API (groupBy, agg, avg) for a more declarative, higher-level implementation.
Comparative Analysis (RDD vs. DataFrame): Benchmarks both approaches over 5 runs each (trimmed mean, excluding min/max) and discusses the results:

RDD: ~2.03 sec average, more verbose (manual combineByKey), full control but no built-in optimization.
DataFrame: ~0.50 sec average, more concise and readable, benefits from Spark's Catalyst optimizer for automatic query planning, making it the more scalable choice for large datasets and production use, though RDDs remain useful for complex, unstructured, low-level operations.



Visualization & Analysis:  Identifies the top 10 routes by average departure delay (e.g., DFW→JFK at 23.3 min), highlighting how major hub airports (JFK, MIA) and long-haul routes are disproportionately affected.
Extended Analysis: Digs deeper into delay patterns using:

Average delay by hour of day (delays build up through the day, peaking in the evening).
Average delay by airline (comparing operational reliability across carriers).
A route-pair delay heatmap (top 15 airports) to geographically surface problem routes.




Tech Stack

PySpark (RDD API & DataFrame API, Spark SQL functions)
Pandas: post-processing for visualization
Matplotlib / Seaborn - charts (bar charts, line plot, heatmap)
Run in Google Colab



Repository Contents


flights_delay.ipynb (full notebook with code, benchmarks, and visualizations)
flights_2000.csv (input dataset (flight records))
Report (PDF) with write-up, execution tables, and analysis



Key Takeaway


The DataFrame API outperformed the RDD API by a significant margin (total pipeline time: ~3.1 sec vs. ~12.3 sec) thanks to Catalyst's query optimization, reinforcing DataFrames as the preferred approach for structured, large-scale data processing in Spark, while RDDs still have their place for lower-level, unstructured workloads.


Authors

Theodora Stamoglou

Georgiana Petridou

Coursework project for the Big Data module, Applied Informatics, University of Macedonia.
