# Replace `HttpSecurity.authorizeRequests(...)` with `HttpSecurity.authorizeHttpRequests(...)` and `ExpressionUrlAuthorizationConfigurer`, `AbstractInterceptUrlConfigurer` with `AuthorizeHttpRequestsConfigurer`, etc

**org.openrewrite.java.spring.boot2.AuthorizeHttpRequests**

_Replace `HttpSecurity.authorizeRequests(...)` deprecated in Spring Security 6 with `HttpSecurity.authorizeHttpRequests(...)` and all method calls on the resultant object respectively. Replace deprecated `AbstractInterceptUrlConfigurer` and its deprecated subclasses with `AuthorizeHttpRequestsConfigurer` and its corresponding subclasses._

## Source

[GitHub](https://github.com/openrewrite/rewrite-spring/blob/main/src/main/java/org/openrewrite/java/spring/boot2/AuthorizeHttpRequests.java), [Issue Tracker](https://github.com/openrewrite/rewrite-spring/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-spring/4.36.0/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-spring
* version: 4.36.0

## Contributors
* [Alex Boyko](aboyko@vmware.com)
* [Jonathan Schnéider](jkschneider@gmail.com)
* [Knut Wannheden](knut@moderne.io)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-spring:4.36.0` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.spring.boot2.AuthorizeHttpRequests")
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
            <recipe>org.openrewrite.java.spring.boot2.AuthorizeHttpRequests</recipe>
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

{% tab title="Maven Command Line" %}
{% code title="shell" %}
You will need to have [Maven](https://maven.apache.org/download.cgi) installed on your machine before you can run the following command.

```shell
mvn -U org.openrewrite.maven:rewrite-maven-plugin:run \
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-spring:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.spring.boot2.AuthorizeHttpRequests
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer.ExpressionInterceptUrlRegistry`
  * newFullyQualifiedTypeName: `org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer.AuthorizationManagerRequestMatcherRegistry`
  * ignoreDefinition: `false`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer`
  * newFullyQualifiedTypeName: `org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer`
  * ignoreDefinition: `false`
* [Change type](../../../java/changetype.md)
  * oldFullyQualifiedTypeName: `org.springframework.security.config.annotation.web.configurers.AbstractInterceptUrlConfigurer`
  * newFullyQualifiedTypeName: `org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer`
  * ignoreDefinition: `false`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.spring.boot2.AuthorizeHttpRequests
displayName: Replace `HttpSecurity.authorizeRequests(...)` with `HttpSecurity.authorizeHttpRequests(...)` and `ExpressionUrlAuthorizationConfigurer`, `AbstractInterceptUrlConfigurer` with `AuthorizeHttpRequestsConfigurer`, etc
description: Replace `HttpSecurity.authorizeRequests(...)` deprecated in Spring Security 6 with `HttpSecurity.authorizeHttpRequests(...)` and all method calls on the resultant object respectively. Replace deprecated `AbstractInterceptUrlConfigurer` and its deprecated subclasses with `AuthorizeHttpRequestsConfigurer` and its corresponding subclasses.
recipeList:
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer.ExpressionInterceptUrlRegistry
      newFullyQualifiedTypeName: org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer.AuthorizationManagerRequestMatcherRegistry
      ignoreDefinition: false
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer
      newFullyQualifiedTypeName: org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer
      ignoreDefinition: false
  - org.openrewrite.java.ChangeType:
      oldFullyQualifiedTypeName: org.springframework.security.config.annotation.web.configurers.AbstractInterceptUrlConfigurer
      newFullyQualifiedTypeName: org.springframework.security.config.annotation.web.configurers.AuthorizeHttpRequestsConfigurer
      ignoreDefinition: false

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.spring.boot2.AuthorizeHttpRequests)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
