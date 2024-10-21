# MAVEN MANUAL

> Taken from [this repository](https://github.com/jabedhasan21/java-hello-world-with-maven)

In the end, the ***user-made*** file structure (that is, not including the
generated one) must be like this

```
.
├── pom.xml
├── src
│   └── main
│       └── java
│           └── hello
│               ├── Greeter.java
│               └── HelloWorld.java
```

## Tutorial


### Initiating files

Beginning:
```bash
mkdir -p src/main/java/hello
touch src/main/java/hello/HelloWorld.java
touch src/main/java/hello/Greeter.java
```

File `src/main/java/hello/HelloWorld.java`:

```java
package hello;
public class HelloWorld {
    public static void main(String[] args) {
        Greeter greeter = new Greeter();
        System.out.println(greeter.sayHello());
    }
}
```

File `src/main/java/hello/Greeter.java`:

```java
package hello;
public class Greeter {
    public String sayHello() {
        return "Hello world!";
    }
}
```

File `pom.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>org.springframework</groupId>
    <artifactId>jb-hello-world-maven</artifactId>
    <packaging>jar</packaging>
    <version>0.1.0</version>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-shade-plugin</artifactId>
                <version>2.1</version>
                <executions>
                    <execution>
                        <phase>package</phase>
                        <goals>
                            <goal>shade</goal>
                        </goals>
                        <configuration>
                            <transformers>
                                <transformer
                                    implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                    <mainClass>hello.HelloWorld</mainClass>
                                </transformer>
                            </transformers>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>
```

### Compiling, building & running

***In the project root directory***!

- Compile: `mvn compile`
- Package: `mvn package`
- Run: `java -jar target/jb-hello-world-maven-0.1.0.jar`
