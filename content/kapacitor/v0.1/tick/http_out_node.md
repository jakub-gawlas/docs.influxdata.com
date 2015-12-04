---
title: HTTPOutNode
note: Auto generated by tickdoc
---

An [HTTPOutNode](/docs/kapacitor/v0.1/tick/http_out_node.html) caches the most recent data for each group it has received. 

The cached data is available at the given endpoint. 
The endpoint is the relative path from the API endpoint of the running task. 
For example if the task endpoint is at &#34;/api/v1/task/&lt;task_name&gt;&#34; and endpoint is 
&#34;top10&#34;, then the data can be requested from &#34;/api/v1/task/&lt;task_name&gt;/top10&#34;. 

Example: 


```javascript
    stream
        .window()
            .period(10s)
            .every(5s)
        .mapReduce(influxql.top('value', 10))
        //Publish the top 10 results over the last 10s updated every 5s.
        .httpOut('top10')
```

