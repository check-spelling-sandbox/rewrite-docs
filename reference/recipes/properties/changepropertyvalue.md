# Change property value

**org.openrewrite.properties.ChangePropertyValue**

_Change a property value leaving the key intact._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-properties/src/main/java/org/openrewrite/properties/ChangePropertyValue.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-properties/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-properties
* version: 7.40.6

## Contributors
* [Jonathan Leitschuh](jonathan.leitschuh@gmail.com)
* [Nick McKinney](mckinneynicholas@gmail.com)
* [Jonathan Schneider](jkschneider@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | propertyKey | The name of the property key whose value is to be changed. |
| `String` | newValue | The new value to be used for key specified by `propertyKey`. |
| `String` | oldValue | *Optional*. Only change the property value if it matches the configured `oldValue`. |
| `Boolean` | regex | *Optional*. Default false. If enabled, `oldValue` will be interpreted as a Regular Expression, and capture group contents will be available in `newValue` |
| `Boolean` | relaxedBinding | *Optional*. Whether to match the `propertyKey` using [relaxed binding](https://docs.spring.io/spring-boot/docs/2.5.6/reference/html/features.html#features.external-config.typesafe-configuration-properties.relaxed-binding) rules. Default is `true`. Set to `false`  to use exact matching. |
| `String` | fileMatcher | *Optional*. Matching files will be modified. This is a glob expression. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.ChangePropertyValueExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.ChangePropertyValueExample
displayName: Change property value example
recipeList:
  - org.openrewrite.properties.ChangePropertyValue:
      propertyKey: management.metrics.binders.files.enabled
      newValue: null
      oldValue: null
      regex: null
      relaxedBinding: null
      fileMatcher: '**/application-*.properties'
```
{% endcode %}

Now that `com.yourorg.ChangePropertyValueExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.ChangePropertyValueExample")
}

repositories {
    mavenCentral()
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
            <recipe>com.yourorg.ChangePropertyValueExample</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.properties.ChangePropertyValue)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
