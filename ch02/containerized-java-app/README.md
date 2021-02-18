# Building the Docker Image

Run the following command to compile the code and build the JAR file.

```
$ ./mvnw package spring-boot:repackage
```

**Please Note**
This Example is based on JAVA-11.
On RHEL8, you need to follow the steps to generate jar file below because the default java version is JDK-8
```
$ sudo dnf install java-11-openjdk-devel.x86_64 java-1.8.0-openjdk-devel.x86_64
$ rpm -ql java-11-openjdk-devel
// we can see "/usr/lib/jvm/java-11-openjdk-11.0.9.11-2.el8_3.x86_64/bin" is the folder for binaries, so I will mark its upper level to JAVA_HOME, as JAVA_HOME is needed for mvnw script.

$ export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.9.11-2.el8_3.x86_64/
$ ./mvnw package spring-boot:repackage
$ ls target/
classes  generated-sources  generated-test-sources  java-hello-world-0.0.1.jar  java-hello-world-0.0.1.jar.original  maven-archiver  maven-status  surefire-reports  test-classes
// you can see file "java-hello-world-0.0.1.jar" is generated.

```


Then build the image with the following command:

```
$ docker build -t java-hello-world:1.0.0 .
```
