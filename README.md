# VictoriaMetricsTest
## Running



## Testing
There are 5 dashboards Kubernetes Cluster Monitoring (via Prometheus), Name Gauge Dashboard, Ordered Bucket Histogram Dashboard, Random Gauge Dashboard, VictoriaMetrics

Custom dashboards are built from the metrics scraped from the `/metrics` endpoint of the app.
### VictoriaMetrics
This dashboard is configured with default scrape_config from Victoria Metrics single helm chart.
```yaml
- job_name: victoriametrics
    static_configs:
     - targets: [ "localhost:8428" ]
```
![image](https://github.com/user-attachments/assets/537d6d49-22ee-4fbe-aebd-35ff7e59fce6)

### Random Gauge Dashboard
Used the next metrics `random_gauge_1`, `random_gauge_2`, and `random_gauge_3`. An all-in-one dashboard is used to demonstrate the filtration mechanism. However, I figured out later that some labels such as email have different values from metric to metric so the better approach would be separating these charts into individual dashboards for better filtration.
![image](https://github.com/user-attachments/assets/8ff657e2-1d58-40a7-8c3e-099716920f96)

Demonstration of filtration mechanism:

![image](https://github.com/user-attachments/assets/99558091-dc63-4377-915d-030c6a38bc1f)

We selected two countries here and got their results. We could also select one more field:

![image](https://github.com/user-attachments/assets/d69fade0-eabd-414e-bf36-80ca4133e342)

### Name gauge Dashboard
This is simple dashboard for showing the current values of each metric:
![image](https://github.com/user-attachments/assets/22d4efeb-ac65-4cfb-90b6-7fa96986a321)

### Kubernetes Cluster Monitoring (via Prometheus)
Kubernetes dashboard for monitoring the current cluster state:
![image](https://github.com/user-attachments/assets/9a1f0b9b-fb51-411c-b2d3-de3e6e635aed)
![image](https://github.com/user-attachments/assets/4a9bace4-a772-43a9-b7fb-2dda56cb8751)

### Ordered Bucket Histogram Dashboard

Dashboard demonstrates the histogram of ordered buckets metrics(supports filtering by name):
![image](https://github.com/user-attachments/assets/4c6fad6f-f14f-4bc8-8f6d-4ea714ce2c4a)

It also has the chart for sum and count:
![image](https://github.com/user-attachments/assets/a938ee39-8b75-41d9-b30d-d8da406ca5d5)
