Maven Full Course | Apache Maven Tutorial for Beginners

 ![Maven Full Course | Apache Maven Tutorial for Beginners - YouTube](https://www.youtube.com/watch?v=uAQs-YXnY-U&t=37s)

**NOTES**:

- Course Introduction:
	#maven is a build automation.
	- maven is a build tool (like make or ant).
	- Dependency management tool.
	- Project management tool. (include some information about the project)
	- Standardized approach to building software.
	- Command line tool.
	- IDE integration
	#build_tools 
	- Create deployable artifacts from source code
	- Automated builds
	- Deploying artifacts on servers
	- IDE independence
	- Integration with other build tools
	Dependency management
	- Download deps from centralized repo
	- auto resolve the libs required by project deps
	- dep scoping (dep == dependency)
	Project Management
	- Artifact versioning
	- Change logs
	- Documentation
	- Javadocs
	- Reports
	Standardized Software Builds
	- Uniformity across projects through patterns
	- Convention over configuration
	- Consistent path for all projects
	- Philosophy of maven
	Plugins and Goals
	- Plugin is a collection of goals
	- example compiler plugin
	- Goals perform the actions in maven builds
	- all work is done via plugins and goals
	- called independently or as part of a lifecycle phase
	Lifecycle And Phases
	- is a sequence of named phases
	- Phases are executed sequentially 
	- 3 lifecycles: clean, default, site (default is the largest)
	- Executing a phase executes all previous phases
random notes:
	- pow is xml file to configure maven projects.
	- Local repo takes precedence during dep resolution


**How does maven work :**

```bash
	$ maven install
```

![[Screen Shot 2023-11-18 at 12.33.16 PM.png]]


To create a simple site with the meta data (informal informations)
```bash
	$ maven site
```

Simple pom.xml
```xml
<project>
	<!-- a simple start -->
	<modelVersion>
		4.0.0
	</modelVersion>
	<artifactId>
		maven-examples
	</artifactId>
	<groupId>
		com.infiniteskill.maven
	</groupId>
	<version>
		1.0.0
	</version>
	<!-- packaging by default is jar -->
	<packaging>
		jar
	</packaging>

	<!-- informal informations -->
	<name>
		learning maven examples
	</name>
	<description>
		this project about learning maven
	</description>
	<url>
		http://www.example.com
	</url>

	<licenses>
		<license>
			<name>
				Apache license
			</name>
			<comments>
				comment
			</comments>
		</license>
	</licenses>

	<organization>
		<name>
			name
		</name>
		<url>
			http://www.example.com
		</url>
	</organization>

	<developers>
		<developer>
			<name>oussama rahmouni</name>
			<email>oussama.rahmouni@email.com</email>
		</developer>
	</developers>
</project>
```

Convention over configurations (maven standard directory layout) 
- [Maven – Introduction to the Standard Directory Layout (apache.org)](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)

|                      |                                                                            |
| -------------------- | -------------------------------------------------------------------------- |
| `src/main/java`      | Application/Library sources                                                |
| `src/main/resources` | Application/Library resources                                              |
| `src/main/filters`   | Resource filter files                                                      |
| `src/main/webapp`    | Web application sources                                                    |
| `src/test/java`      | Test sources                                                               |
| `src/test/resources` | Test resources                                                             |
| `src/test/filters`   | Test resource filter files                                                 |
| `src/it`             | Integration Tests (primarily for plugins)                                  |
| `src/assembly`       | Assembly descriptors                                                       |
| `src/site`           | Site                                                                       |
| `LICENSE.txt`        | Project's license                                                          |
| `NOTICE.txt`         | Notices and attributions required by libraries that the project depends on |
| `README.txt`         | Project's readme                                                           |

If you want to change the default source and target directories :
(the location of the pom.xml file is the root)
(not recommended)
```xml
<project>
	<sourceDirectory>
		src/nonstandard/java
	</sourceDirectory>
	<directory>
		myTarget
	</directory>
</project>
```

**Pom Inheritance:**

- Every pom inherit from a super pom

- to see the actual pom after `Effective POMs, after inheritance, interpolation, and profiles are applied` you should run :

```bash
	$ mvn help::effective-pom
```
- this simple pom.xml:
```xml
<project>
	<!-- a simple start -->
	<modelVersion>
		4.0.0
	</modelVersion>
	<artifactId>
		maven-examples
	</artifactId>
	<groupId>
		com.infiniteskill.maven
	</groupId>
	<version>
		1.0.0
	</version>
</project>
```
OUTPUT ==>
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.infiniteskill.maven</groupId>
  <artifactId>maven-examples</artifactId>
  <version>1.0.0</version>
  <repositories>
    <repository>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
      <id>central</id>
      <name>Central Repository</name>
      <url>https://repo.maven.apache.org/maven2</url>
    </repository>
  </repositories>
  <pluginRepositories>
    <pluginRepository>
      <releases>
        <updatePolicy>never</updatePolicy>
      </releases>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
      <id>central</id>
      <name>Central Repository</name>
      <url>https://repo.maven.apache.org/maven2</url>
    </pluginRepository>
  </pluginRepositories>
  <build>
    <sourceDirectory>/Users/orahmoun/maven/p1/maven-example/src/main/java</sourceDirectory>
    <scriptSourceDirectory>/Users/orahmoun/maven/p1/maven-example/src/main/scripts</scriptSourceDirectory>
    <testSourceDirectory>/Users/orahmoun/maven/p1/maven-example/src/test/java</testSourceDirectory>
    <outputDirectory>/Users/orahmoun/maven/p1/maven-example/target/classes</outputDirectory>
    <testOutputDirectory>/Users/orahmoun/maven/p1/maven-example/target/test-classes</testOutputDirectory>
    <resources>
      <resource>
        <directory>/Users/orahmoun/maven/p1/maven-example/src/main/resources</directory>
      </resource>
    </resources>
    <testResources>
      <testResource>
        <directory>/Users/orahmoun/maven/p1/maven-example/src/test/resources</directory>
      </testResource>
    </testResources>
    <directory>/Users/orahmoun/maven/p1/maven-example/target</directory>
    <finalName>maven-examples-1.0.0</finalName>
    <pluginManagement>
      <plugins>
        <plugin>
          <artifactId>maven-antrun-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-assembly-plugin</artifactId>
          <version>3.6.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-dependency-plugin</artifactId>
          <version>3.6.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-release-plugin</artifactId>
          <version>3.0.1</version>
        </plugin>
      </plugins>
    </pluginManagement>
    <plugins>
      <plugin>
        <artifactId>maven-clean-plugin</artifactId>
        <version>3.2.0</version>
        <executions>
          <execution>
            <id>default-clean</id>
            <phase>clean</phase>
            <goals>
              <goal>clean</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-resources-plugin</artifactId>
        <version>3.3.1</version>
        <executions>
          <execution>
            <id>default-testResources</id>
            <phase>process-test-resources</phase>
            <goals>
              <goal>testResources</goal>
            </goals>
          </execution>
          <execution>
            <id>default-resources</id>
            <phase>process-resources</phase>
            <goals>
              <goal>resources</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-jar-plugin</artifactId>
        <version>3.3.0</version>
        <executions>
          <execution>
            <id>default-jar</id>
            <phase>package</phase>
            <goals>
              <goal>jar</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.11.0</version>
        <executions>
          <execution>
            <id>default-compile</id>
            <phase>compile</phase>
            <goals>
              <goal>compile</goal>
            </goals>
          </execution>
          <execution>
            <id>default-testCompile</id>
            <phase>test-compile</phase>
            <goals>
              <goal>testCompile</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>3.1.2</version>
        <executions>
          <execution>
            <id>default-test</id>
            <phase>test</phase>
            <goals>
              <goal>test</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-install-plugin</artifactId>
        <version>3.1.1</version>
        <executions>
          <execution>
            <id>default-install</id>
            <phase>install</phase>
            <goals>
              <goal>install</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-deploy-plugin</artifactId>
        <version>3.1.1</version>
        <executions>
          <execution>
            <id>default-deploy</id>
            <phase>deploy</phase>
            <goals>
              <goal>deploy</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-site-plugin</artifactId>
        <version>3.12.1</version>
        <executions>
          <execution>
            <id>default-site</id>
            <phase>site</phase>
            <goals>
              <goal>site</goal>
            </goals>
            <configuration>
              <outputDirectory>/Users/orahmoun/maven/p1/maven-example/target/site</outputDirectory>
              <reportPlugins>
                <reportPlugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-project-info-reports-plugin</artifactId>
                </reportPlugin>
              </reportPlugins>
            </configuration>
          </execution>
          <execution>
            <id>default-deploy</id>
            <phase>site-deploy</phase>
            <goals>
              <goal>deploy</goal>
            </goals>
            <configuration>
              <outputDirectory>/Users/orahmoun/maven/p1/maven-example/target/site</outputDirectory>
              <reportPlugins>
                <reportPlugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-project-info-reports-plugin</artifactId>
                </reportPlugin>
              </reportPlugins>
            </configuration>
          </execution>
        </executions>
        <configuration>
          <outputDirectory>/Users/orahmoun/maven/p1/maven-example/target/site</outputDirectory>
          <reportPlugins>
            <reportPlugin>
              <groupId>org.apache.maven.plugins</groupId>
              <artifactId>maven-project-info-reports-plugin</artifactId>
            </reportPlugin>
          </reportPlugins>
        </configuration>
      </plugin>
    </plugins>
  </build>
  <reporting>
    <outputDirectory>/Users/orahmoun/maven/p1/maven-example/target/site</outputDirectory>
  </reporting>
</project>
```

- To inherit from another pom:
```xml
<project>
	<modelVersion> 4.0.0 </modelVersion>
	<artifactId> maven-examples </artifactId>
	
	<parent>
		<artifactId> maven-examples-parent </artifactId>
		<groupId> com.infiniteskill.maven </groupId>
		<version> 1.0.0 </version>
	</parent>
</project>
```

You can install the parent pom file to add it to the local repository
```bash
	$ mvn install
```

**Profiles:**
Maven profiles allow us to build our projects for different environment:

```xml
<project>
	<modelVersion>
		4.0.0
	</modelVersion>
	<artifactId>
		maven-examples
	</artifactId>
	<groupId>
		com.infiniteskill.maven
	</groupId>
	<version>
		1.0.0
	</version>

	<profiles>
		<profile>
			<id>production</id>
			<build>
				<directory>
					production
				</directory>
			</build>
		</profile>
	</profiles>

	<build>
		<directory>
			development
		</directory>
	</build>
	
</project>
```

to select the right profile :
```bash
	$ mvn -Pproduction compile
```

- Activations example using env :
```xml
<project>
	<modelVersion>
		4.0.0
	</modelVersion>
	<artifactId>
		maven-examples
	</artifactId>
	<groupId>
		com.infiniteskill.maven
	</groupId>
	<version>
		1.0.0
	</version>

	<profiles>
		<profile>
			<id>production</id>
			<activation>
				<property>
					<name>env.PACKAGE_ENV</name>
					<value>PROD</value>
				</property>
			</activation>
			<build>
				<directory>
					production
				</directory>
			</build>
		</profile>
	</profiles>

	<build>
		<directory>
			development
		</directory>
	</build>
	
</project>
```

- Plugin that speed up building a projects :
```bash
	$ mvn archetype:generate
```
- to make your project and intellj project you run:
```bash
	$ mvn idea:idea
```

## **Dependency Management**
**goals**:
- basic dependency management
- transitive dependency management
- connect to alternative remote repos
- understand dependency scope

- to pull down the dependencies:
```bash
	$ mvn dependency:copy-dependencies
```
- to add another repository:
	- modify the settings.xml, example:
```xml
<profile>
	<id>spring_remote</id>
	<repositories>
		<repository>
			<id>spring_repository</id>
			<url>http://repo.spring.io/release/</url>
		</repository>
	</repositories>
	<activeProfiles>
		<activeProfile>spring_remote</activeProfile>
	</activeProfiles>
</profile>
```

###  dependency scope: 

##### Maven dependency scope – compile

This is **maven default scope**. Dependencies with `compile` scope are needed to _build_, _test_, and _run_ the project.

Scope `compile` is to be required in most of the cases to resolve the import statements into your java classes sourcecode.
##### Maven dependency scope – provided

**Maven dependency scope provided** is used during **build and test** the project. They are also required to run, but **should not exported**, because the dependency will be provided by the runtime, for instance, by servlet container or application server.

##### Maven dependency scope – runtime

Dependencies with `maven dependency scope runtime` are not needed to build, but are part of the classpath to **test and run** the project.

##### Maven dependency scope – test

Dependencies with **maven dependency scope test** are not needed to build and run the project. They are needed to **compile and run the unit tests**.

##### Maven dependency scope – system

Dependencies with `system` are similar to ones with scope `provided`. The only difference is `system` dependencies are not retrieved from remote repository. They are present under project’s subdirectory and are referred from there. See [external dependency](https://howtodoinjava.com/maven/maven-dependency-management/#external-dependency) for more detail.

##### Maven dependency scope – import

`import` scope is only supported on a dependency of type `pom` in the `dependencyManagement` section. It indicates the dependency to be replaced with the effective list of dependencies in the specified POM’s `dependencyManagement` section.



- Conflict resolution:

	both `example_dep1` and `example_dep2` depend on the same thing but with different version of that, maven will select the newest version 
```xml
<dependencies>
	<dependency>
		<groupId>com.example.project1</groupId>
		<artifactId>example_dep1</artifactId>
		<version>1.0</version>
	</dependency>
	<dependency>
		<groupId>com.example.project2</groupId>
		<artifactId>example_dep2</artifactId>
		<version>1.0</version>
	</dependency>
</dependencies>
```

   lets assume that `example_dep1` depends on the newest version of that common dependency to make maven select the oldest you need to exclude the dep from  `example_dep1` 

```xml
<dependencies>
	<dependency>
		<groupId>com.example.project1</groupId>
		<artifactId>example_dep1</artifactId>
		<version>1.0</version>
		<exclusions>
			<exclusion>
				<groupId>com.example.common</groupId>
				<artifactId>common_dep</artifactId>
			</exclusion>
		</exclusions>
	</dependency>
	<dependency>
		<groupId>com.example.project2</groupId>
		<artifactId>example_dep2</artifactId>
		<version>1.0</version>
	</dependency>
</dependencies>
```

## Maven Lifecycle and Plugins
goals:
- Learn the basics of the maven lifecycle
- identify important maven phases
- invoke plugins explicitly and via lifecycle
- configure plugins to customize their behavior
- build a simple custom plugin
##### Lifecycle
you can use the help plugin to learn about the phase
example:
```bash 
	$ mv help:describe -Dcmd=clean
```
=> output
```terminal
'clean' is a lifecycle with the following phases:
- pre-clean: Not defined
- clean: org.apache.maven.plugins:maven-clean-plugin:2.5:clean
- post-clean: Not defined
```
##### Phases
Important phases:
- Compile: compile the source code of the project
- Test-compile: compile the test source code into the test destination directory
- Test: runs tests using a suitable unit testing framework. These tests should not require the code be to packaged or deployed:
	- to ignore the test in the case of failure
```xml
<build>
	<plugins>
		<plugin>
			<groupId>org.apache.maven.plugins</groupId>
			<artifactId>maven-surefire-plugin</artifactId>
			<configuration>
				<testFailureIgnore>true</testFailureIgnore>
			<configuration>
		</plugin>
	</plugins>
</build>
```
- Package: take the compiled code and package it in its distributable format, such as a jar
- install: install the package into the local repository, for use as a dependency in other projects locally.
- Deploy: done in an integration or release environment, copies the final package to the remote repository for sharing with other developers and projects
##### Plugins
- A plugin is a collection of goals:
- plugin is a prefix, ex: `mvn compiler:`, the second is a goal `mvn compiler:compiler`
##### Plugins properties
- Example: setting property via command line argument
```shell
	$ mvn compiler:compile -Dmaven.compiler.verbose=true
```
- Example: setting property using pom file `this is a better way`
```xml
<build>
	<pluginManagement>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.2</version>
				<configuration>
					<verbose>true</verbose>
				<configuration>
			</plugin>
		</plugins>
	</pluginManagement>
</build>
```

- RANDOM NOTE
	- `<plugins>` is for configuring plugins directly in a specific build.
	- `<pluginManagement>` is for defining default configurations for plugins that can be inherited by child POMs.
	- `<pluginManagement>` is often used in parent POMs to centralize plugin configurations and avoid duplication across multiple child projects.
	- By using `<pluginManagement>`, you provide a consistent set of default configurations that child projects can adopt or override as needed. It helps maintain a standardized build configuration across multiple projects within a multi-module project or organization.


- Custom Plugins
