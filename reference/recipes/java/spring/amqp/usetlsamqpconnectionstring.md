# Use TLS for AMQP connection strings

**org.openrewrite.java.spring.amqp.UseTlsAmqpConnectionString**

_Use TLS for AMQP connection strings._

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/java/org/openrewrite/java/spring/amqp/UseTlsAmqpConnectionString.java), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.37.0-SNAPSHOT/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.37.0-SNAPSHOT

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | propertyKey | The Spring property key to perform updates against. If this value is specified, the specified property will be used for searching, otherwise a default of `spring.rabbitmq.addresses` will be used instead. |
| `Integer` | oldPort | The non-TLS enabled port number to replace with the TLS-enabled port. If this value is specified, no changes will be made to amqp connection strings which do not contain this port number.  |
| `Integer` | port | The TLS-enabled port to use. |
| `String` | tlsPropertyKey | The Spring property key to enable default TLS mode against. If this value is specified, the specified property will be used when updating the default TLS mode, otherwise a default of `spring.rabbitmq.ssl.enabled` will be used instead. |
| `List` | pathExpressions | *Optional*. Each value in this list represents a glob expression that is used to match which files will be modified. If this value is not present, this recipe will query the execution context for reasonable defaults. ("**/application.yml", "**/application.yml", and "**/application.properties". |

## Contributors
* [Shannon Pamperl](shanman190@gmail.com)


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UseTlsAmqpConnectionStringExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UseTlsAmqpConnectionStringExample
displayName: Use TLS for AMQP connection strings example
recipeList:
  - org.openrewrite.java.spring.amqp.UseTlsAmqpConnectionString:
      propertyKey: spring.rabbitmq.addresses
      oldPort: 1234
      port: 1234
      tlsPropertyKey: null
      pathExpressions: **/application.yml
```
{% endcode %}

Now that `com.yourorg.UseTlsAmqpConnectionStringExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-spring:4.37.0-SNAPSHOT in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.5")
}

rewrite {
    activeRecipe("com.yourorg.UseTlsAmqpConnectionStringExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:4.37.0-SNAPSHOT")
}
```
{% endcode %}
{% endtab %}
{% tab title="Maven" %}
{% code title="pom.xml" %}
```markup
<project>
  <build>
    <plugins>
      <plugin>
        <groupId>org.openrewrite.maven</groupId>
        <artifactId>rewrite-maven-plugin</artifactId>
        <version>4.45.3</version>
        <configuration>
          <activeRecipes>
            <recipe>com.yourorg.UseTlsAmqpConnectionStringExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>4.37.0-SNAPSHOT</version>
          </dependency>
        </dependencies>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.amqp.UseTlsAmqpConnectionString)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
