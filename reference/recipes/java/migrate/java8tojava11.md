# Migrate to Java 11

**org.openrewrite.java.migrate.Java8toJava11**

_This recipe will apply changes commonly needed when upgrading to Java 11. Specifically, for those applications that are built on Java 8, this recipe will update and add dependencies on J2EE libraries that are no longer directly bundled with the JDK. This recipe will also replace deprecated API with equivalents when there is a clear migration strategy. Build files will also be updated to use Java 11 as the target/source and plugins will be also be upgraded to versions that are compatible with Java 11._

### Tags

* jaxb
* deprecated
* java11
* jaxws
* jakarta

## Source

[GitHub](https://github.com/openrewrite/rewrite-migrate-java/blob/main/src/main/resources/META-INF/rewrite/java-version-11.yml), [Issue Tracker](https://github.com/openrewrite/rewrite-migrate-java/issues), [Maven Central](https://central.sonatype.com/artifact/org.openrewrite.recipe/rewrite-migrate-java/1.21.1/jar)

* groupId: org.openrewrite.recipe
* artifactId: rewrite-migrate-java
* version: 1.21.1

## Contributors
* [Tim te Beek](tim.te.beek@jdriven.com)
* [Jonathan Schneider](jkschneider@gmail.com)
* [Tyler Van Gorder](tkvangorder@users.noreply.github.com)
* [Sam Snyder](sam@moderne.io)
* [Jonathan Schnéider](jkschneider@gmail.com)
* [Knut Wannheden](knut@moderne.io)
* [Patrick](patway99@gmail.com)


## Usage

This recipe has no required configuration options. It can be activated by adding a dependency on `org.openrewrite.recipe:rewrite-migrate-java:1.21.1` in your build file or by running a shell command (in which case no build changes are needed): 
{% tabs %}
{% tab title="Gradle" %}
{% code title="build.gradle" %}
```groovy
plugins {
    id("org.openrewrite.rewrite") version("5.40.4")
}

rewrite {
    activeRecipe("org.openrewrite.java.migrate.Java8toJava11")
}

repositories {
    mavenCentral()
}

dependencies {
    rewrite("org.openrewrite.recipe:rewrite-migrate-java:1.21.1")
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
            <recipe>org.openrewrite.java.migrate.Java8toJava11</recipe>
          </activeRecipes>
        </configuration>
        <dependencies>
          <dependency>
            <groupId>org.openrewrite.recipe</groupId>
            <artifactId>rewrite-migrate-java</artifactId>
            <version>1.21.1</version>
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
  -Drewrite.recipeArtifactCoordinates=org.openrewrite.recipe:rewrite-migrate-java:RELEASE \
  -Drewrite.activeRecipes=org.openrewrite.java.migrate.Java8toJava11
```
{% endcode %}
{% endtab %}
{% endtabs %}

## Definition

{% tabs %}
{% tab title="Recipe List" %}
* [Prefer `java.util.Base64` instead of `sun.misc`](../../java/migrate/usejavautilbase64.md)
* [Add explicit JAXB dependencies](../../java/migrate/javax/addjaxbdependencies.md)
* [Add explicit JAX-WS dependencies](../../java/migrate/javax/addjaxwsdependencies.md)
* [Add explicit Inject dependencies](../../java/migrate/javax/addinjectdependencies.md)
* [`BigDecimal` rounding constants to `RoundingMode` enums](../../java/cleanup/bigdecimalroundingconstantstoenums.md)
* [Use primitive wrapper `valueOf` method](../../java/cleanup/primitivewrapperclassconstructortovalueof.md)
* [Use modernized `java.util.concurrent` APIs](../../java/migrate/concurrent/javaconcurrentapis.md)
* [Use modernized `java.lang` APIs](../../java/migrate/lang/javalangapis.md)
* [Use modernized `java.util.logging` APIs](../../java/migrate/logging/javaloggingapis.md)
* [Use modernized `java.net` APIs](../../java/migrate/net/javanetapis.md)
* [Use modernized `java.sql` APIs](../../java/migrate/sql/javasqlapis.md)
* [Use modernized `javax.lang.model.util` APIs](../../java/migrate/javax/javaxlangmodelutil.md)
* [Use modernized `javax.management.monitor` APIs](../../java/migrate/javax/javaxmanagementmonitorapis.md)
* [Use modernized `javax.xml.stream` APIs](../../java/migrate/javax/javaxxmlstreamapis.md)
* [Remove Cobertura Maven plugin](../../java/migrate/cobertura/removecoberturamavenplugin.md)
* [Upgrade Wro4j plugin version](../../java/migrate/wro4j/upgradewro4jmavenpluginversion.md)
* [Upgrade JaCoCo Maven plugin version](../../java/migrate/jacoco/upgradejacocomavenpluginversion.md)
* [Change Maven Java version property values to 11](../../java/migrate/javaversion11.md)
* [Use modernized `java.util` APIs](../../java/migrate/util/javautilapis.md)
* [Prefer `Optional.isEmpty()`](../../java/migrate/util/optionalnotpresenttoisempty.md)
* [Prefer `Optional.isPresent()`](../../java/migrate/util/optionalnotemptytoispresent.md)
* [Upgrade `actions/setup-java` `java-version`](../../github/setupjavaupgradejavaversion.md)
  * minimumJavaMajorVersion: `11`

{% endtab %}

{% tab title="Yaml Recipe List" %}
```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: org.openrewrite.java.migrate.Java8toJava11
displayName: Migrate to Java 11
description: This recipe will apply changes commonly needed when upgrading to Java 11. Specifically, for those applications that are built on Java 8, this recipe will update and add dependencies on J2EE libraries that are no longer directly bundled with the JDK. This recipe will also replace deprecated API with equivalents when there is a clear migration strategy. Build files will also be updated to use Java 11 as the target/source and plugins will be also be upgraded to versions that are compatible with Java 11.

tags:
  - jaxb
  - deprecated
  - java11
  - jaxws
  - jakarta
recipeList:
  - org.openrewrite.java.migrate.UseJavaUtilBase64
  - org.openrewrite.java.migrate.javax.AddJaxbDependencies
  - org.openrewrite.java.migrate.javax.AddJaxwsDependencies
  - org.openrewrite.java.migrate.javax.AddInjectDependencies
  - org.openrewrite.java.cleanup.BigDecimalRoundingConstantsToEnums
  - org.openrewrite.java.cleanup.PrimitiveWrapperClassConstructorToValueOf
  - org.openrewrite.java.migrate.concurrent.JavaConcurrentAPIs
  - org.openrewrite.java.migrate.lang.JavaLangAPIs
  - org.openrewrite.java.migrate.logging.JavaLoggingAPIs
  - org.openrewrite.java.migrate.net.JavaNetAPIs
  - org.openrewrite.java.migrate.sql.JavaSqlAPIs
  - org.openrewrite.java.migrate.javax.JavaxLangModelUtil
  - org.openrewrite.java.migrate.javax.JavaxManagementMonitorAPIs
  - org.openrewrite.java.migrate.javax.JavaxXmlStreamAPIs
  - org.openrewrite.java.migrate.cobertura.RemoveCoberturaMavenPlugin
  - org.openrewrite.java.migrate.wro4j.UpgradeWro4jMavenPluginVersion
  - org.openrewrite.java.migrate.jacoco.UpgradeJaCoCoMavenPluginVersion
  - org.openrewrite.java.migrate.JavaVersion11
  - org.openrewrite.java.migrate.util.JavaUtilAPIs
  - org.openrewrite.java.migrate.util.OptionalNotPresentToIsEmpty
  - org.openrewrite.java.migrate.util.OptionalNotEmptyToIsPresent
  - org.openrewrite.github.SetupJavaUpgradeJavaVersion:
      minimumJavaMajorVersion: 11

```
{% endtab %}
{% endtabs %}

## See how this recipe works across multiple open-source repositories

[![Moderne Link Image](/.gitbook/assets/ModerneRecipeButton.png)](https://public.moderne.io/recipes/org.openrewrite.java.migrate.Java8toJava11)

The community edition of the Moderne platform enables you to easily run recipes across thousands of open-source repositories.

Please [contact Moderne](https://moderne.io/product) for more information about safely running the recipes on your own codebase in a private SaaS.
