# stian-mlab-speedtest 




**Personal Goals:**
  * Learn about machine learning using python (Jupyter Notebook)
  * Learn basic python
  

**Task**
  - Use data from M-Lab (Measurement Lab) to predict various network related data
    * MinRTT (Ping / Latency)
    * Throughput (Packets that arrive (Mbps))
    * LossRate
  - As well as trying to do some predictions about city locations using Longitude and Latitude, weighted with Mbps



**Sql Query**

This is the sql query i used to get the data from M-Lab

```sql
SELECT
  client.Geo.Latitude AS Lat,
  client.Geo.Longitude AS Long, 
  client.Geo.City AS City,
  client.Geo.PostalCode AS PostalCode,
  client.Geo.AccuracyRadiusKm AS Accuracy,
  client.Geo.CountryCode, 
  a.MeanThroughputMbps AS Mbps,
  raw.StartTime AS StartTime,
  raw.EndTime AS Endtime,
  a.*
FROM
  `measurement-lab.ndt.ndt7`
WHERE
  date BETWEEN "2017-04-11"
  AND "2022-04-11"
  AND client.Geo.CountryCode = "NO"
  AND client.Geo.AccuracyRadiusKm <= 5
  --AND a.CongestionControl = "cubic"
  --AND a.CongestionControl = "bbr"
  ORDER BY Endtime asc 
```


## Running the code

1. Python
2. Jupyter

Included in this repository is a [requirements.txt](https://github.com/Stisor/5974-22H-Spesialpensum/blob/main/requirements.txt) file that has all the dependencies used, but i will list the main ones here.

1. Scikit-learn
2. Matplotlib
3. Numpy
4. Scipy
5. Pandas


I have also chosen to use the [Feather](https://arrow.apache.org/docs/python/feather.html) file format, as it has various advantages over CSV, such as faster reads and writes, aswell as smaller files sizes.



### Sources

[^1]: Aurelien A. (2019) Hands-on Machine Learing with Scikit-Learn, Keras and TensorFlow. O’Reilly 
Media, 2. edition

[^2]: Mueller Andreas C. (2016) Introduction to Machine Learning with Python. O’Reilly Media, 4. 
edition

