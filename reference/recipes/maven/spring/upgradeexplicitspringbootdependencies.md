# Upgrade un-managed spring project dependencies

**org.openrewrite.maven.spring.UpgradeExplicitSpringBootDependencies**

_Upgrades un-managed spring-boot project dependencies according to the specified spring-boot version._

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/java/org/openrewrite/maven/spring/UpgradeExplicitSpringBootDependencies.java), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.36.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.36.0

## Contributors
* [Andrei Shakirin](andrei.shakirin@gmail.com)
* [Patrick Way](pway99@users.noreply.github.com)
* [Patrick](patway99@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Kyle Scully](scullykns@gmail.com)

## Options

| Type | Name | Description |
| -- | -- | -- |
| `String` | fromVersion | XRage pattern for spring version used to limit which projects should be updated |
| `String` | toVersion | Upgrade version of `org.springframework.boot` |


## Usage

This recipe has required configuration parameters. Recipes with required configuration parameters cannot be activated directly. To activate this recipe you must create a new recipe which fills in the required parameters. In your `rewrite.yml` create a new recipe with a unique name. For example: `com.yourorg.UpgradeExplicitSpringBootDependenciesExample`.
Here's how you can define and customize such a recipe within your rewrite.yml:

{% code title="rewrite.yml" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.UpgradeExplicitSpringBootDependenciesExample
displayName: Upgrade un-managed spring project dependencies example
recipeList:
  - org.openrewrite.maven.spring.UpgradeExplicitSpringBootDependencies:
      fromVersion:  2.7.+
      toVersion: 3.0.0-M3
```
{% endcode %}

Now that `com.yourorg.UpgradeExplicitSpringBootDependenciesExample` has been defined activate it and take a dependency on org.openrewrite.recipe:rewrite-spring:4.36.0 in your build file:
{% tabs %}

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
            <recipe>com.yourorg.UpgradeExplicitSpringBootDependenciesExample</recipe>
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

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.maven.spring.UpgradeExplicitSpringBootDependencies)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
