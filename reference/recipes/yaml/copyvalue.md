# Copy YAML value

**org.openrewrite.yaml.CopyValue**

_Copies a YAML value from one key to another. The existing key/value pair remains unaffected by this change. If either the source or destination key path does not exist, no value will be copied. Furthermore, copies are limited to scalar values, not whole YAML blocks._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-yaml/src/main/java/org/openrewrite/yaml/CopyValue.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-yaml/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-yaml
* version: 7.40.6

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Aurélien Mino](aurelien.mino@gmail.com)
* [Aaron Gershman](5619476+aegershman@users.noreply.github.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | oldKeyPath | A JsonPath expression to locate a YAML key/value pair to copy. |
| `String` | newKey | A JsonPath expression for where the new value should be copied to. |
| `String` | fileMatcher | *Optional*. Matching files will be modified. This is a glob expression. |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.CopyValueExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.CopyValueExample
displayName: Copy YAML value example
recipeList:
  - org.openrewrite.yaml.CopyValue:
      oldKeyPath: $.source.kind
      newKey: $.dest.kind
      fileMatcher: '**/application-*.yml'
```
{% endcode %}

Now that `com.yourorg.CopyValueExample` has been defined activate it in your build file:
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("com.yourorg.CopyValueExample")
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
            <recipe>com.yourorg.CopyValueExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.yaml.CopyValue)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
