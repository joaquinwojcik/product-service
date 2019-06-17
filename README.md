# Microservicio con Jacoco y Sonar
### Plugins para Eclipse (opcional):
Para Jacoco:
https://www.eclemma.org/

Para SonarLint, buscarlo en el Eclipse Marketplace
### Ejecucion:
Ejecucion de tests que incluyen la cobertura con Jacoco:

mvn clean test

Ejecucion de Sonar:

mvn sonar:sonar

https://reflectoring.io/unit-testing-spring-boot/

https://howtodoinjava.com/spring-boot2/spring-boot-mockmvc-example/

https://memorynotfound.com/unit-test-spring-mvc-rest-service-junit-mockito/

### Spring Profiles:

.\mvnw package -DskipTests

Profile Default:

java -jar target/product-service-0.0.1-SNAPSHOT.jar

Profile dev:

java -jar target/product-service-0.0.1-SNAPSHOT.jar --spring.profiles.active=dev

### Extras:
DevTools: Acceder a http://localhost:8082/h2-console/ para ver consola de base en memoria

Actuator: Ver Apis de Acturator: http://localhost:8082/actuator

Prometheus: Ver API: http://localhost:8082/actuator/prometheus

Levantar Prometheus y Graphana:

docker run -p 9090:9090 -v /c/Users/cha14309/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus

 docker run -d --name=grafana -p 3000:3000 grafana/grafana
 
 https://www.callicoder.com/spring-boot-actuator-metrics-monitoring-dashboard-prometheus-grafana/
 
 http://micrometer.io/docs/registry/prometheus
 
 https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#production-ready-metrics-export-prometheus

Kubernetes Horizonthal Pod Autoescaler:

minikube start

minikube addons enable heapster

Esperar algunos minutos y:

kubectl top node

kubectl top pod --all-namespaces

Ver Grafana en un browser:

minikube service monitoring-grafana -n kube-system
 
& minikube docker-env | Invoke-Expression

mvn clean install

docker build -t diegochavezcarro/product-app:1.0.0 .

kubectl create -f .\product-app-k8s-template.yaml

kubectl create -f .\product-hpa.yaml

Ir viendo que pasa:

kubectl get hpa,deployment

kubectl run -it --rm --restart=Never prueba --image=busybox -- sh -c "wget -O - -q http://product-service:8082"

### Reference Documentation
For further reference, please consider the following sections:

https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/
https://spotinst.com/blog/collecting-kubernetes-pod-metrics-heapster-is-dead/

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* https://www.baeldung.com/sonar-qube
### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service with Spring Boot Actuator](https://spring.io/guides/gs/actuator-service/)
* [Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa/)
* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [Building REST services with Spring](https://spring.io/guides/tutorials/bookmarks/)

