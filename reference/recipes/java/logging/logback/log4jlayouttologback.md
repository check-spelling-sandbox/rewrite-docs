# Migrate Log4j 2.x Layout to logback-classic equivalents

**org.openrewrite.java.logging.logback.Log4jLayoutToLogback**

_Migrates custom Log4j 2.x Layout components to `logback-classic`. This recipe operates on the following assumptions: 1. A logback-classic layout must extend the `LayoutBase<ILoggingEvent>` class. 2. log4j's `format()` is renamed to `doLayout()` in a logback-classic layout. 3. LoggingEvent `getRenderedMessage()` is converted to LoggingEvent `getMessage()`. 4. The log4j ignoresThrowable() method is not needed and has no equivalent in logback-classic. 5. The activateOptions() method merits further discussion. In log4j, a layout will have its activateOptions() method invoked by log4j configurators, that is PropertyConfigurator or DOMConfigurator just after all the options of the layout have been set. Thus, the layout will have an opportunity to check that its options are coherent and if so, proceed to fully initialize itself. 6. In logback-classic, layouts must implement the LifeCycle interface which includes a method called start(). The start() method is the equivalent of log4j's activateOptions() method. For more details, see this page from logback: [`Migration from log4j`](http://logback.qos.ch/manual/migrationFromLog4j.html)._

## Source

[GitHub](https://github.com/openrewrite/rewrite-logging-frameworks/blob/main/src/main/java/org/openrewrite/java/logging/logback/Log4jLayoutToLogback.java), [Issue Tracker](https://github.com/openrewrite/rewrite-logging-frameworks/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-logging-frameworks/1.20.1/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-logging-frameworks
* version: 1.20.1

## Contributors
* [Aaron Gershman](5619476+aegershman@users.noreply.github.com)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Patrick Way](pway99@users.noreply.github.com)
* [traceyyoshima](tracey.yoshima@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-logging-frameworks:1.20.1` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.logging.logback.Log4jLayoutToLogback")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-logging-frameworks:1.20.1")
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
            <recipe>org.openrewrite.java.logging.logback.Log4jLayoutToLogback</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-logging-frameworks</artifactId>
            <version>1.20.1</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-logging-frameworks:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.logging.logback.Log4jLayoutToLogback
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.logging.logback.Log4jLayoutToLogback)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
