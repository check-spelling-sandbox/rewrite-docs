# Print Maven dependency hierarchy in DOT format

**org.openrewrite.maven.utilities.PrintMavenAsDot**

_The DOT language format is specified [here](https://graphviz.org/doc/info/lang.html)._

## Source

[GitHub](https://github.com/openrewrite/rewrite/blob/main/rewrite-maven/src/main/java/org/openrewrite/maven/utilities/PrintMavenAsDot.java), [Issue Tracker](https://github.com/openrewrite/rewrite/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite/rewrite-maven/7.40.6/jar)

* groupId: org.openrewrite
* artifactId: rewrite-maven
* version: 7.40.6

## Example
* Example 1: 

## Contributors
* [Jonathan Schneider](jkschneider@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Patrick](patway99@gmail.com)


## Usage

This recipe has no required configuration parameters and comes from a rewrite core library. It can be activated directly without adding any dependencies.
{% tabs %}

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
            <recipe>org.openrewrite.maven.utilities.PrintMavenAsDot</recipe>
          </activeRecipes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```
{% endcode %}
{% endtab %}

{% tab title="Maven Command Line" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.
{% code title="shell" %}
```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.activeRecipes=org.openrewrite.maven.utilities.PrintMavenAsDot
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.maven.utilities.PrintMavenAsDot)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
