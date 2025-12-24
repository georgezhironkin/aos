# aos app
w

Swagger: http://localhost:8080/swagger-ui/index.html
Prometheus: http://localhost:9090
Grafana:http://localhost:3000
Jenkins: http://localhost:8081

### Prometheus:

**Скорость HTTP запросов:**
```
rate(http_server_requests_seconds_count[5m])
```
**Использование памяти heap:**
```
jvm_memory_used_bytes{area="heap"}
```
**Среднее время ответа:**
```
rate(http_server_requests_seconds_sum[5m]) / rate(http_server_requests_seconds_count[5m])
```
