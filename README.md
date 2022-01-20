# Getting Started

## Windows

### Compile, Test, Jar Code
* gradle build

### Run Jar
* Local:      gradle bootRun
* Background: nohup bash mvnw.cmd spring-boot:run &

### Testing Application
* Abrir navegador: http://localhost:8081/rest/mscovid/test?msg=testing

## Linux

### Compile, Test, Jar Code
* gradle build

### Run Jar
* Local:      gradle bootRun
* Background: nohup bash mvnw.cmd spring-boot:run &

### Testing Application
* curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'
