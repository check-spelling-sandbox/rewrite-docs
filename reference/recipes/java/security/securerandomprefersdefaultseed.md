# SecureRandom seeds are not constant or predictable

**org.openrewrite.java.security.SecureRandomPrefersDefaultSeed**

_Remove `SecureRandom#setSeed(*)` method invocations having constant or predictable arguments._

### Tags

* RSPEC-4347

## Source

[GitHub](https://github.com/openrewrite/rewrite-java-security/blob/main/src/main/java/org/openrewrite/java/security/SecureRandomPrefersDefaultSeed.java), [Issue Tracker](https://github.com/openrewrite/rewrite-java-security/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-java-security/1.25.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-java-security
* version: 1.25.0

## Contributors
* [Patrick](patway99@gmail.com)
* [Sam Snyder](sam@moderne.io)
* [Jonathan Schnéider](jkschneider@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-java-security:1.25.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.security.SecureRandomPrefersDefaultSeed")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-java-security:1.25.0")
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
            <recipe>org.openrewrite.java.security.SecureRandomPrefersDefaultSeed</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-java-security</artifactId>
            <version>1.25.0</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-java-security:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.security.SecureRandomPrefersDefaultSeed
```
{% endcode %}
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.security.SecureRandomPrefersDefaultSeed)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
