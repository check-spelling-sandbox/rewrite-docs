# Change the key of a spring application property

**org.openrewrite.java.spring.ChangeSpringPropertyKey**

_Change spring application property keys existing in either Properties or Yaml files._

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/java/org/openrewrite/java/spring/ChangeSpringPropertyKey.java), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.36.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.36.0

## Contributors
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Patrick](patway99@gmail.com)
* [Kyle Scully](scullykns@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | oldPropertyKey | The property key to rename. Supports glob |
| `String` | newPropertyKey | The new name for the property key. |
| `List` | except | *Optional*. If any of these property keys exist as direct children of `oldPropertyKey`, then they will not be moved to `newPropertyKey`. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangeSpringPropertyKeyExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangeSpringPropertyKeyExample
displayName: Change the key of a spring application property example
recipeList:
  - org.openrewrite.java.spring.ChangeSpringPropertyKey:
      oldPropertyKey: management.metrics.binders.*.enabled
      newPropertyKey: management.metrics.enable.process.files
      except: null
```
{% endcode %}

Now that `com.yourorg.ChangeSpringPropertyKeyExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-spring:4.36.0 in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.ChangeSpringPropertyKeyExample")
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
            <recipe>com.yourorg.ChangeSpringPropertyKeyExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.ChangeSpringPropertyKey)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
