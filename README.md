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
### Настройка Pipeline
## Установка плагинов (Manage Jenkins → Plugins):
```
GitHub Integration Plugin
Pipeline
Git plugin
Настройка Maven (Manage Jenkins → Tools):
```
## Установка Maven
```
Maven installations → Add Maven
Name: Maven
Install automatically: выбрать версию 
Создание Pipeline Job:
```
## Добавление pipeline
```
New Item → Pipeline
Имя: aos-pipeline
В разделе "Build Triggers":
GitHub hook trigger for GITScm polling
Poll SCM (Schedule: H/5 * * * *)
В разделе "Pipeline":
Definition: Pipeline script from SCM
SCM: Git
Repository URL: https://github.com/YOUR_USERNAME/adminka.git
Branch: */main
Script Path: Jenkinsfile
```
