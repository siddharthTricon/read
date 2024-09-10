Here's how you can create a Maven project with 4 sub-modules (add, subtract, multiply, divide), package them into JAR files, and then import those JAR files into a new Maven project named `calculator` to create a simple calculator application.
 
### Step-by-Step Guide:
 
#### 1. **Create the Parent Project**
 
First, create a **parent Maven project** with packaging type `pom`.
 
##### **Directory Structure:**
```
parent-project/
    pom.xml
    add/
        pom.xml
    subtract/
        pom.xml
    multiply/
        pom.xml
    divide/
        pom.xml
```
 
#### 2. **Create the Parent Project's `pom.xml`**
 
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
 
    <groupId>com.example</groupId>
<artifactId>parent-project</artifactId>
<version>1.0-SNAPSHOT</version>
<packaging>pom</packaging>
 
    <modules>
<module>add</module>
<module>subtract</module>
<module>multiply</module>
<module>divide</module>
</modules>
</project>
```
 
#### 3. **Create the Sub-modules**
 
For each sub-module (`add`, `subtract`, `multiply`, and `divide`), create a simple class that performs the corresponding operation and a `pom.xml` file to package it as a JAR.
 
### **Submodule 1: `add`**
 
##### **add/pom.xml:**
 
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
 
    <parent>
<groupId>com.example</groupId>
<artifactId>parent-project</artifactId>
<version>1.0-SNAPSHOT</version>
<relativePath>../pom.xml</relativePath>
</parent>
 
    <artifactId>add</artifactId>
<packaging>jar</packaging>
 
    <dependencies>
<!-- Add any dependencies if required -->
</dependencies>
</project>
```
 
##### **AddClass.java**:
```java
package com.example.add;
 
public class AddClass {
    public int add(int a, int b) {
        return a + b;
    }
}
```
 
Repeat this process for the other sub-modules (`subtract`, `multiply`, `divide`) but change the logic accordingly.
 
### **Submodule 2: `subtract`**
 
##### **subtract/pom.xml:**
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
 
    <parent>
<groupId>com.example</groupId>
<artifactId>parent-project</artifactId>
<version>1.0-SNAPSHOT</version>
<relativePath>../pom.xml</relativePath>
</parent>
 
    <artifactId>subtract</artifactId>
<packaging>jar</packaging>
 
    <dependencies>
<!-- Add any dependencies if required -->
</dependencies>
</project>
```
 
##### **SubtractClass.java**:
```java
package com.example.subtract;
 
public class SubtractClass {
    public int subtract(int a, int b) {
        return a - b;
    }
}
```
 
### **Submodule 3: `multiply`**
 
##### **multiply/pom.xml:**
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
 
    <parent>
<groupId>com.example</groupId>
<artifactId>parent-project</artifactId>
<version>1.0-SNAPSHOT</version>
<relativePath>../pom.xml</relativePath>
</parent>
 
    <artifactId>multiply</artifactId>
<packaging>jar</packaging>
 
    <dependencies>
<!-- Add any dependencies if required -->
</dependencies>
</project>
```
 
##### **MultiplyClass.java**:
```java
package com.example.multiply;
 
public class MultiplyClass {
    public int multiply(int a, int b) {
        return a * b;
    }
}
```
 
### **Submodule 4: `divide`**
 
##### **divide/pom.xml:**
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
 
    <parent>
<groupId>com.example</groupId>
<artifactId>parent-project</artifactId>
<version>1.0-SNAPSHOT</version>
<relativePath>../pom.xml</relativePath>
</parent>
 
    <artifactId>divide</artifactId>
<packaging>jar</packaging>
 
    <dependencies>
<!-- Add any dependencies if required -->
</dependencies>
</project>
```
 
##### **DivideClass.java**:
```java
package com.example.divide;
 
public class DivideClass {
    public int divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Division by zero");
        }
        return a / b;
    }
}
```
 
#### 4. **Build the Parent Project**
 
Now, build the parent project using the Maven command:
```bash
mvn clean install
```
This will generate JAR files for each of the sub-modules (`add`, `subtract`, `multiply`, and `divide`) in the `target` directories of each sub-module.
 
#### 5. **Create the Calculator Project**
 
Now create a new Maven project called `calculator` that will use the JAR files generated from the parent project.
 
##### **Directory Structure:**
```
calculator/
    pom.xml
    src/main/java/com/example/calculator/CalculatorApp.java
```
 
##### **calculator/pom.xml**:
Add dependencies for the modules `add`, `subtract`, `multiply`, and `divide` in the `pom.xml` of the calculator project.
 
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
<modelVersion>4.0.0</modelVersion>
 
    <groupId>com.example</groupId>
<artifactId>calculator</artifactId>
<version>1.0-SNAPSHOT</version>
<packaging>jar</packaging>
 
    <dependencies>
<dependency>
<groupId>com.example</groupId>
<artifactId>add</artifactId>
<version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
<groupId>com.example</groupId>
<artifactId>subtract</artifactId>
<version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
<groupId>com.example</groupId>
<artifactId>multiply</artifactId>
<version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
<groupId>com.example</groupId>
<artifactId>divide</artifactId>
<version>1.0-SNAPSHOT</version>
</dependency>
</dependencies>
</project>
```
 
##### **CalculatorApp.java**:
```java
package com.example.calculator;
 
import com.example.add.AddClass;
import com.example.subtract.SubtractClass;
import com.example.multiply.MultiplyClass;
import com.example.divide.DivideClass;
 
public class CalculatorApp {
    public static void main(String[] args) {
        AddClass add = new AddClass();
        SubtractClass subtract = new SubtractClass();
        MultiplyClass multiply = new MultiplyClass();
        DivideClass divide = new DivideClass();
 
        int a = 10;
        int b = 5;
 
        System.out.println("Addition: " + add.add(a, b));
        System.out.println("Subtraction: " + subtract.subtract(a, b));
        System.out.println("Multip
 
lication: " + multiply.multiply(a, b));
        System.out.println("Division: " + divide.divide(a, b));
    }
}
```
 
#### 6. **Run the Calculator Project**
 
Finally, you can build and run the calculator project:
 
```bash
mvn clean install
```
 
Then run the `CalculatorApp` class to see the results!