
In VSC, with "Spring Initializr Java Support", menu "View" -> "Command Pallete...": 

"Spring Initializr: Create a Maven Project..."
2.4.4
Java
pe.samples
sample1
Jar
8
Spring Web
enter

In main: "java\pe\samples\sammple1" create folder "controller", and inside create HelloController.java file (HelloController class)

Add @RestController to class:

```java

@RestController
public class HelloController {
    
}

```

In class, add method type String hello, return "Hello world":
```java

@RestController
public class HelloController {
    public String hello(){
        return "Hello wordl!!!";
    }
    
}

```
convert method to get requet, add @GetMapping with url "/api/v1/hello"
```java
package pe.samples.sample1.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @GetMapping("/api/v1/hello")
    public String hello(){
        return "Hello wordl!!!";
    }
}
```

Run and test, in browser http://localhost:8080/api/v1/hello

Add docker file, using "View" -> "Command Palette ..." : "Docker: Add Docker Files to workspace ..." -> "Java" -> "" -> "NO"

For build docker image use .jar, then use maven for build .jar:

```console
mvnw package
```

Create image:

```console
docker build -t pe.samples.sample1 .
```

Create container

```console
docker run -d -p 81:8080 pe.samples.sample1
```

and test in http://localhost:81/api/v1/hello


for deploy in GCP Cloud Run, build and push to registry
```console
docker build -t gcr.io/workshop-gcp-305200/sample1 .
docker push gcr.io/workshop-gcp-305200/sample1
```

