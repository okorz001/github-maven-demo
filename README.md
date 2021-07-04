# github-maven-demo

Demonstration of GitHub Actions, Packages, and Pages with Maven Project

## Features

* Builds every PR and every commit to master
* Manual release from master
  * Publish to GitHub Packages
  * Publish site to GitHub Pages
* Cache maven repository between builds

Both the library and site are intentionally trivial to avoid obfuscating the important parts.

## Usage

There's a sample project under `./sample` that demonstrates how to use the published artifact in another project.

Here's how to add the repository and the dependency in Maven:
```xml
  <repositories>
    <repository>
      <id>github</id>
      <url>https://maven.pkg.github.com/okorz001/github-maven-demo</url>
    </repository>
  </repositories>

  <dependencies>
    <dependency>
      <groupId>org.korz.demos</groupId>
      <artifactId>github-maven-demo</artifactId>
      <version>1.0.0</version>
    </dependency>
  </dependencies>
```

### Access Token

As far as I can tell, GitHub Packages requires an access token, even if the package is public. :disappointed:

Here's how to configure the access token in your `~/.m2/settings.xml`:

```xml
  <servers>
    <server>
      <id>github</id>
      <username><!-- your GitHub user name --></username>
      <password><!-- your GitHub access token --></password>
    </server>
  </servers>
```

Note that the repository id and server id must match for maven to use these credentials.
