
- source: [Lesson: Packaging Programs in JAR Files (The Java™ Tutorials > Deployment) (oracle.com)](https://docs.oracle.com/javase/tutorial/deployment/jar/)

The JAR file format provides many benefits:

- _Security_: You can digitally sign the contents of a JAR file. Users who recognize your signature can then optionally grant your software security privileges it wouldn't otherwise have.
- _Decreased download time_: If your applet is bundled in a JAR file, the applet's class files and associated resources can be downloaded to a browser in a single HTTP transaction without the need for opening a new connection for each file.
- _Compression_: The JAR format allows you to compress your files for efficient storage.
- _Packaging for extensions_: The extensions framework provides a means by which you can add functionality to the Java core platform, and the JAR file format defines the packaging for extensions. By using the JAR file format, you can turn your software into extensions as well.
- _Package Sealing_: Packages stored in JAR files can be optionally sealed so that the package can enforce version consistency. Sealing a package within a JAR file means that all classes defined in that package must be found in the same JAR file.
- _Package Versioning_: A JAR file can hold data about the files it contains, such as vendor and version information.
- _Portability_: The mechanism for handling JAR files is a standard part of the Java platform's core API.


**Common JAR file operations**

|Operation|Command|
|---|---|
|To create a JAR file|jar cf _jar-file input-file(s)_|
|To view the contents of a JAR file|jar tf _jar-file_|
|To extract the contents of a JAR file|jar xf _jar-file_|
|To extract specific files from a JAR file|jar xf _jar-file archived-file(s)_|
|To run an application packaged as a JAR file (requires the [Main-class](https://docs.oracle.com/javase/tutorial/deployment/jar/appman.html) manifest header)|java -jar _app.jar_|

# Working with Manifest Files:

The manifest is a special file that can contain information about the files packaged in a JAR file.
##### default manifest :

When you create a JAR file, it automatically receives a default manifest file. There can be only one manifest file in an archive, and it always has the pathname

META-INF/MANIFEST.MF

When you create a JAR file, the default manifest file simply contains the following:

Manifest-Version: 1.0
Created-By: 1.7.0_06 (Oracle Corporation)

#### to use a custom manifest: 

You use the m command-line option to add custom information to the manifest during creation of a JAR file. This section describes the m option.

```bash
	$ jar cfm _jar-file manifest-addition input-file(s)
```

Let's look at the options and arguments used in this command:

- The c option indicates that you want to _create_ a JAR file.
- The m option indicates that you want to merge information from an existing file into the manifest file of the JAR file you're creating.
- The f option indicates that you want the output to go to a _file_ (the JAR file you're creating) rather than to standard output.

#### Setting an Application's Entry Point

If you have an application bundled in a JAR file, you need some way to indicate which class within the JAR file is your application's entry point. You provide this information with the `Main-Class` header in the manifest, which has the general form:

```
	Main-Class: _classname_
```

After you have set the `Main-Class` header in the manifest, you then run the JAR file using the following form of the `java` command:
```bash
	 $java -jar _JAR-name_
```


**Warning:** The text file must end with a new line or carriage return. The last line will not be parsed properly if it does not end with a new line or carriage return.

**Alternatively**: you can use -e option (for entrypoint) 
```bash
	$ jar cfe Main.jar foo.Main foo/Main.class
```

#### Adding Classes to the JAR File's Classpath

You may need to reference classes in other JAR files from within a JAR file.

You specify classes to include in the Class-Path header field in the manifest file of an applet or application. The Class-Path header takes the following form:
```
	Class-Path: _jar1-name jar2-name directory-name/jar3-nam_
```

#### Setting Package Version Information

You may need to include package version information in a JAR file's manifest. You provide this information with the following headers in the manifest:

**Headers in a manifest**

|Header|Definition|
|---|---|
|Name|The name of the specification.|
|Specification-Title|The title of the specification.|
|Specification-Version|The version of the specification.|
|Specification-Vendor|The vendor of the specification.|
|Implementation-Title|The title of the implementation.|
|Implementation-Version|The build number of the implementation.|
|Implementation-Vendor|The vendor of the implementation.|

One set of such headers can be assigned to each package. The versioning headers should appear directly beneath the Name header for the package. This example shows all the versioning headers:

Name: java/util/
Specification-Title: Java Utility Classes
Specification-Version: 1.2
Specification-Vendor: Example Tech, Inc.
Implementation-Title: java.util
Implementation-Version: build57
Implementation-Vendor: Example Tech, Inc.