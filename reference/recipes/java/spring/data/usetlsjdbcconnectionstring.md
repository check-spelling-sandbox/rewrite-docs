# Use TLS for JDBC connection strings

**org.openrewrite.java.spring.data.UseTlsJdbcConnectionString**

_Increasingly, for compliance reasons (e.g. [NACHA](https://www.nacha.org/sites/default/files/2022-06/End_User_Briefing_Supplementing_Data_Security_UPDATED_FINAL.pdf)), JDBC connection strings should be TLS-enabled. This recipe will update the port and optionally add a connection attribute to indicate that the connection is TLS-enabled._

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/java/org/openrewrite/java/spring/data/UseTlsJdbcConnectionString.java), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.36.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.36.0

## Contributors
* [Shannon Pamperl](shanman190@gmail.com)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | propertyKey | The Spring property key to perform updates against. If this value is specified, the specified property will be used for searching, otherwise a default of `spring.datasource.url` will be used instead. |
| `Integer` | oldPort | The non-TLS enabled port number to replace with the TLS-enabled port. If this value is specified, no changes will be made to jdbc connection strings which do not contain this port number.  |
| `Integer` | port | The TLS-enabled port to use. |
| `String` | attribute | A connection attribute, if any, indicating to the JDBC provider that this is a TLS connection. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UseTlsJdbcConnectionStringExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UseTlsJdbcConnectionStringExample
displayName: Use TLS for JDBC connection strings example
recipeList:
  - org.openrewrite.java.spring.data.UseTlsJdbcConnectionString:
      propertyKey: spring.datasource.url
      oldPort: 1234
      port: 1234
      attribute: sslConnection=true
```
{% endcode %}

Now that `com.yourorg.UseTlsJdbcConnectionStringExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-spring:4.36.0 in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.UseTlsJdbcConnectionStringExample")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-spring:4.36.0")
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
        <version>4.45.0</version>
        <configuration>
          <activeRecipes>
            <recipe>com.yourorg.UseTlsJdbcConnectionStringExample</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-spring</artifactId>
            <version>4.36.0</version>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.data.UseTlsJdbcConnectionString)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
