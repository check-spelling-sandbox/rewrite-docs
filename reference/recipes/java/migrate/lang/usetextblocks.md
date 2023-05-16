# Use text blocks

**org.openrewrite.java.migrate.lang.UseTextBlocks**

_Text blocks are easier to read than concatenated strings._

## Source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/java/org/openrewrite/java/migrate/lang/UseTextBlocks.java), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.21.1/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 1.21.1

## Examples


Example layout Style 1

> - **Example 1 : SQL query**
>> ***Test.java***
>>> *Before*
>>> ```java
>>> class Test {
>>>     String query = "SELECT * FROM\n" +
>>>             "my_table\n" +
>>>             "WHERE something = 1;";
>>> }
>>> ```
>>> *After*
>>> ```java
>>> class Test {
>>>    String query = """
>>>           SELECT * FROM
>>>           my_table
>>>           WHERE something = 1;\
>>> """;
>>> }
>>> ```
> ---
>> ***Test2.java***
>>> *Before*
>>> ```java
>>> class Test2 {
>>>     String query = "SELECT * FROM\n" +
>>>             "my_table\n" +
>>>             "WHERE something = 1;";
>>> }
>>> ```
>>> *After*
>>> ```java
>>> class Test2 {
>>>    String query = """
>>>           SELECT * FROM
>>>           my_table
>>>           WHERE something = 1;\
>>> """;
>>> }
>>> ```
> ---
> - **Example 2**
>> ***Test2.java***
>>> *Before*
>>> ```java
>>> class Test2 {
>>>     String query = "SELECT * FROM\n" +
>>>             "my_table\n" +
>>>             "WHERE something = 1;";
>>> }
>>> ```
>>> *After*
>>> ```java
>>> class Test2 {
>>>    String query = """
>>>           SELECT * FROM
>>>           my_table
>>>           WHERE something = 1;\
>>> """;
>>> }
>>> ```
>

---

Example layout Style 2

##### - Example 1:
###### - Before
{% code title="A.java" %}
```java
class Test {
    String query = "SELECT * FROM\n" +
            "my_table\n" +
            "WHERE something = 1;";
}
```
{% endcode %}


###### After
{% code title="A.java" %}
```java
class Test {
    String query = """
            SELECT * FROM
            my_table
            WHERE something = 1;\
            """;
}
```
{% endcode %}
---
##### Example 2:
###### Before
{% code title="A.java" %}
```java
class A {
    void welcome() {
        log("\n========================================================="
            + "\n                                                         "
            + "\n          Welcome to Spring Integration!                 "
            + "\n                                                         "
            + "\n    For more information please visit:                   "
            + "\n    https://www.springsource.org/spring-integration      "
            + "\n                                                         "
            + "\n=========================================================");
    }
    void log(String s) {}
}
```
{% endcode %}


###### After
{% code title="A.java" %}
```java
class A {
    void welcome() {
        log("""
            
            =========================================================
                                                                    \s
                      Welcome to Spring Integration!                \s
                                                                    \s
                For more information please visit:                  \s
                https://www.springsource.org/spring-integration     \s
                                                                    \s
            =========================================================\
            """);
    }
    void log(String s) {}
}
```
{% endcode %}

---
##### Example 3:
###### Before
{% code title="Test.java" %}
```java
class Test {
    String eightQuotes = "\"\"\"\"\"\"\"\"" +
                   "after 8 quotes";
}
```
{% endcode %}

###### After
{% code title="Test.java" %}
```java
class Test {
    String eightQuotes = """
                   ""\"""\"""\
                   after 8 quotes\
                   """;
}

```
{% endcode %}

## Contributors
* [Kun Li](kun@moderne.io)
* [Jonathan Schneider](jkschneider@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `boolean` | convertStringsWithoutNewlines | *Optional*. Whether or not strings without newlines should be converted to text block when processing code. The default value is true. |


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:1.21.1` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.lang.UseTextBlocks")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:1.21.1")
}
```
{% endcode %}
{% endtab %}
{% tab title="Maven POM" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>4.45.0</version>
        <configuration>
          <activeRecipes>
            <recipe>org.openrewrite.java.migrate.lang.UseTextBlocks</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>1.21.1</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.lang.UseTextBlocks
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.lang.UseTextBlocks)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
