# Fix CWE-338 with `SecureRandom`

**org.openrewrite.java.jhipster.FixCwe338**

_Use a cryptographically strong pseudo-random number generator (PRNG)._

## Source

[GitHub](https://github.com/openrewrite/rewrite-jhipster/blob/main/src/main/java/org/openrewrite/java/jhipster/FixCwe338.java), [Issue Tracker](https://github.com/openrewrite/rewrite-jhipster/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-jhipster/1.20.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-jhipster
* version: 1.20.0

## Contributors
* [Sam Snyder](sam@moderne.io)
* [Aaron Gershman](aegershman@gmail.com)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Scott Jungling](scott.jungling@gmail.com)
* [Patrick](patway99@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-jhipster:1.20.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.jhipster.FixCwe338")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-jhipster:1.20.0")
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
            <recipe>org.openrewrite.java.jhipster.FixCwe338</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-jhipster</artifactId>
            <version>1.20.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-jhipster:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.jhipster.FixCwe338
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.jhipster.FixCwe338)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
