# Nexus-learning-repo

This repo is maintained by [Devops with Mike](https://www.youtube.com/@DevOpsWithMike0/videos/)

**Nexus Repository**

Apache Maven integrates with Nexus Repository Manager to host and manage artifacts, allowing teams to share and access project dependencies efficiently. Using Maven’s distribution Management configuration, artifacts (e.g., JAR/WAR files) can be deployed to a Nexus repository and made accessible to other projects or team members. This setup is particularly useful for managing versioned builds and for facilitating dependency sharing in CI/CD workflows.

## Configuring Nexus Deployment
To configure Maven for deployment to Nexus, specify the repository in your `pom.xml` as follows:

```
<distributionManagement>
    <repository>
        <id>nexus</id>
        <url>http://localhost:8081/repository/maven-releases/</url>
    </repository>
    <snapshotRepository>
        <id>nexus-snapshots</id>
        <url>http://localhost:8081/repository/maven-snapshots/</url>
    </snapshotRepository>
</distributionManagement>
```

*Example settings.xml Configuration for Nexus Authentication*

To enable secure deployment to Nexus, configure authentication details in your Maven settings.xml file, typically located in `${MAVEN_HOME}/conf` or `${USER_HOME}/.m2`:

```
<settings>
    <servers>
        <server>
            <id>nexus</id>
            <username>your-nexus-username</username>
            <password>your-nexus-password</password>
        </server>
        <server>
            <id>nexus-snapshots</id>
            <username>your-nexus-username</username>
            <password>your-nexus-password</password>
        </server>
    </servers>
</settings>
```

## Deploying Artifacts to Nexus
With this setup, you can deploy your artifacts to Nexus by running the following Maven command:

```mvn deploy
```

This command will upload the built artifacts to the Nexus repository specified in the distributionManagement section of your pom.xml. Using Nexus Repository Manager alongside Maven simplifies dependency management and enhances the scalability of your CI/CD pipelines.