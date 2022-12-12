# stian-mlab-speedtest 


Goals: \
Predict throughput (speed) \
Predict RTT (ping / latency) \
Predict lossrate 


SELECT
  client.Geo.Latitude AS Lat, \
  client.Geo.Longitude AS Long, \
  client.Geo.City AS City,\
  client.Geo.PostalCode AS PostalCode,\
  client.Geo.AccuracyRadiusKm AS Accuracy,\
  client.Geo.CountryCode, \
  a.MeanThroughputMbps AS Mbps,\
  raw.StartTime AS StartTime,\
  raw.EndTime AS Endtime,\
  a.*\
FROM\
  `measurement-lab.ndt.ndt7`\
WHERE\
  date BETWEEN "2017-04-11"\
  AND "2022-04-11"\
  AND client.Geo.CountryCode = "NO"\
  AND client.Geo.AccuracyRadiusKm <= 5\
  --AND a.CongestionControl = "cubic"\
  --AND a.CongestionControl = "bbr"\
  ORDER BY Endtime asc 