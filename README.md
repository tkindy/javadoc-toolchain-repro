# javadoc-toolchain-repro

Minimal reproduction for [maven-javadoc-plugin#1244](https://github.com/apache/maven-javadoc-plugin/issues/1244)

## Steps to reproduce

1. Set up [a `toolchains.xml` configuration file](https://maven.apache.org/guides/mini/guide-using-toolchains.html) on your local machine containing at least a toolchain for Java 21.
2. Run `mvn javadoc:javadoc` from the root of this repo using JDK 23 or higher.

## Expected result

The Javadoc site is produced.

## Actual result

Javadoc generation fails with the following error:

```
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-javadoc-plugin:3.12.0:javadoc (default-cli) on project javadoc-toolchain-repro: An error has occurred in Javadoc report generation:
[ERROR] Exit code: 1
[ERROR] error: invalid flag: --no-fonts
```

<details>

<summary>Full logs</summary>

```
$ mvn -V javadoc:javadoc
Apache Maven 3.9.11 (3e54c93a704957b63ee3494413a2b544fd3d825b)
Maven home: /opt/homebrew/Cellar/maven/3.9.11/libexec
Java version: 25, vendor: Oracle Corporation, runtime: /Library/Java/JavaVirtualMachines/openjdk-25.jdk/Contents/Home
Default locale: en_US, platform encoding: UTF-8
OS name: "mac os x", version: "15.7.1", arch: "aarch64", family: "mac"
WARNING: A terminally deprecated method in sun.misc.Unsafe has been called
WARNING: sun.misc.Unsafe::staticFieldBase has been called by com.google.inject.internal.aop.HiddenClassDefiner (file:/opt/homebrew/Cellar/maven/3.9.11/libexec/lib/guice-5.1.0-classes.jar)
WARNING: Please consider reporting this to the maintainers of class com.google.inject.internal.aop.HiddenClassDefiner
WARNING: sun.misc.Unsafe::staticFieldBase will be removed in a future release
[INFO] Build Prism is Active.
[INFO] Scanning for projects...
[INFO]
[INFO] ---------------< com.tylerkindy:javadoc-toolchain-repro >---------------
[INFO] Building javadoc-toolchain-repro 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] >>> javadoc:3.12.0:javadoc (default-cli) > generate-sources @ javadoc-toolchain-repro >>>
[INFO]
[INFO] --- toolchains:3.2.0:toolchain (default) @ javadoc-toolchain-repro ---
[INFO] Required toolchain: jdk [ version='21' ]
[INFO] Found matching toolchain for type jdk: JDK[/Library/Java/JavaVirtualMachines/openjdk-21.jdk/Contents/Home]
[INFO]
[INFO] <<< javadoc:3.12.0:javadoc (default-cli) < generate-sources @ javadoc-toolchain-repro <<<
[INFO]
[INFO]
[INFO] --- javadoc:3.12.0:javadoc (default-cli) @ javadoc-toolchain-repro ---
[INFO] Toolchain in maven-javadoc-plugin: JDK[/Library/Java/JavaVirtualMachines/openjdk-21.jdk/Contents/Home]
[INFO]
Usage:
    javadoc [options] [packagenames] [sourcefiles] [@files]
where options include:
    @<file>       Read options and filenames from file
    --add-modules <module>(,<module>)*
                  Root modules to resolve in addition to the initial modules,
                  or all modules on the module path if <module> is
                  ALL-MODULE-PATH.
    -bootclasspath <path>
                  Override location of platform class files used for non-modular
                  releases
    -breakiterator
                  Compute first sentence with BreakIterator
    --class-path <path>, -classpath <path>, -cp <path>
                  Specify where to find user class files
    -doclet <class>
                  Generate output via alternate doclet
    -docletpath <path>
                  Specify where to find doclet class files
    --enable-preview
                  Enable preview language features. To be used in conjunction with
                  either -source or --release.
    -encoding <name>
                  Source file encoding name
    -exclude <pkglist>
                  Specify a list of packages to exclude
    --expand-requires <value>
                  Instructs the tool to expand the set of modules to be
                  documented. By default, only the modules given explicitly on
                  the command line will be documented. A value of "transitive"
                  will additionally include all "requires transitive"
                  dependencies of those modules. A value of "all" will include
                  all dependencies of those modules.
    -extdirs <dirlist>
                  Override location of installed extensions
    --help, -help, -?, -h
                  Display command-line options and exit
    --help-extra, -X
                  Print a synopsis of nonstandard options and exit
    -J<flag>      Pass <flag> directly to the runtime system
    --limit-modules <module>(,<module>)*
                  Limit the universe of observable modules
    -locale <name>
                  Locale to be used, e.g. en_US or en_US_WIN
    --module <module>(,<module>)*
                  Document the specified module(s)
    --module-path <path>, -p <path>
                  Specify where to find application modules
    --module-source-path <path>
                  Specify where to find input source files for multiple modules
    -package
                  Show package/protected/public types and members. For
                  named modules, show all packages and all module details.
    -private
                  Show all types and members. For named modules,
                  show all packages and all module details.
    -protected
                  Show protected/public types and members (default). For
                  named modules, show exported packages and the module's API.
    -public
                  Show only public types and members. For named modules,
                  show exported packages and the module's API.
    -quiet        Do not display status messages
    --release <release>
                  Provide source compatibility with specified release
    --show-members <value>
                  Specifies which members (fields, methods, etc.) will be
                  documented, where value can be one of "public", "protected",
                  "package" or "private". The default is "protected", which will
                  show public and protected members, "public" will show only
                  public members, "package" will show public, protected and
                  package members and "private" will show all members.
    --show-module-contents <value>
                  Specifies the documentation granularity of module
                  declarations. Possible values are "api" or "all".
    --show-packages <value>
                  Specifies which modules packages will be documented. Possible
                  values are "exported" or "all" packages.
    --show-types <value>
                  Specifies which types (classes, interfaces, etc.) will be
                  documented, where value can be one of "public", "protected",
                  "package" or "private". The default is "protected", which will
                  show public and protected types, "public" will show only
                  public types, "package" will show public, protected and
                  package types and "private" will show all types.
    --source <release>, -source <release>
                  Provide source compatibility with specified release
    --source-path <path>, -sourcepath <path>
                  Specify where to find source files
    -subpackages <subpkglist>
                  Specify subpackages to recursively load
    --system <jdk>
                  Override location of system modules used for modular releases
    --upgrade-module-path <path>
                  Override location of upgradeable modules
    -verbose      Output messages about what Javadoc is doing
    --version     Print version information
    -Werror       Report an error if any warnings occur

Provided by the Standard doclet:
    --add-script <file>
                  Add a script file to the generated documentation
    --add-stylesheet <file>
                  Add a stylesheet file to the generated documentation
    --allow-script-in-comments
                  Allow JavaScript in options and comments
    -author       Include @author paragraphs
    -bottom <html-code>
                  Include bottom text for each page
    -charset <charset>
                  Charset for cross-platform viewing of generated documentation
    -d <directory>
                  Destination directory for output files
    -docencoding <name>
                  Specify the character encoding for the output
    -docfilessubdirs
                  Recursively copy doc-file subdirectories
    -doctitle <html-code>
                  Include title for the overview page
    -excludedocfilessubdir <name>,<name>,...
                  Exclude any doc-files subdirectories with given name.
                  ':' can also be used anywhere in the argument as a separator.
    -footer <html-code>
                  Include footer text for each page
    -group <name> <g1>,<g2>...
                  Group specified elements together in overview page.
                  ':' can also be used anywhere in the argument as a separator.
    -header <html-code>
                  Include header text for each page
    -helpfile <file>
                  Include file that help link links to
    -html5        Generate HTML 5 output. This option is no longer required.
    --javafx, -javafx
                  Enable JavaFX functionality
    -keywords     Include HTML meta tags with package, class and member info
    -link <url>   Create links to javadoc output at <url>
    --link-modularity-mismatch (warn|info)
                  Report external documentation with wrong modularity with either
                  a warning or informational message. The default behaviour is to
                  report a warning.
    -linkoffline <url1> <url2>
                  Link to docs at <url1> using package list at <url2>
    --link-platform-properties <url>
                  Link to platform documentation URLs declared in properties file at <url>
    -linksource   Generate source in HTML
    --main-stylesheet <file>, -stylesheetfile <file>
                  File to change style of the generated documentation
    -nocomment    Suppress description and tags, generate only declarations
    -nodeprecated
                  Do not include @deprecated information
    -nodeprecatedlist
                  Do not generate deprecated list
    -nohelp       Do not generate help link
    -noindex      Do not generate index
    -nonavbar     Do not generate navigation bar
    --no-platform-links
                  Do not generate links to the platform documentation
    -noqualifier <name1>,<name2>,...
                  Exclude the list of qualifiers from the output.
                  ':' can also be used anywhere in the argument as a separator.
    -nosince      Do not include @since information
    -notimestamp  Do not include hidden time stamp
    -notree       Do not generate class hierarchy
    --override-methods (detail|summary)
                  Document overridden methods in the detail or summary sections.
                  The default is 'detail'.
    -overview <file>
                  Read overview documentation from HTML file
    -serialwarn   Generate warning about @serial tag
    --since <release>(,<release>)*
                  Document new and deprecated API in the specified releases
    --since-label <text>
                  Provide text to use in the heading of the "New API" page
    --snippet-path <path>
                  The path for external snippets
    -sourcetab <tab length>
                  Specify the number of spaces each tab takes up in the source
    --spec-base-url
                  Specify a base URL for relative URLs in @spec tags
    -splitindex   Split index into one file per letter
    -tag <name>:<locations>:<header>
                  Specify single argument custom tags
    -taglet       The fully qualified name of Taglet to register
    -tagletpath   The path to Taglets
    -top <html-code>
                  Include top text for each page
    -use          Create class and package usage pages
    -version      Include @version paragraphs
    -windowtitle <text>
                  Browser window title for the documentation

GNU-style options may use = instead of whitespace to separate the name of an
option from its value.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.479 s
[INFO] Finished at: 2025-10-22T14:48:47-04:00
[INFO] ------------------------------------------------------------------------
[INFO] Sending build prism data (93.6 KB)...
[INFO] Ingested build prism (508ms): https://tools.hubteam.com/build-prism-ui/build/019a0d40-9742-7893-b50c-0b39be6994ea
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-javadoc-plugin:3.12.0:javadoc (default-cli) on project javadoc-toolchain-repro: An error has occurred in Javadoc report generation:
[ERROR] Exit code: 1
[ERROR] error: invalid flag: --no-fonts
[ERROR] 1 error
[ERROR] Command line was: /Library/Java/JavaVirtualMachines/openjdk-21.jdk/Contents/Home/bin/javadoc -J-Duser.language= -J-Duser.country= @options @packages
[ERROR]
[ERROR] Refer to the generated Javadoc files in '/Users/tkindy/temp/javadoc-toolchain-repro/target/reports/apidocs' dir.
[ERROR]
[ERROR] -> [Help 1]
[ERROR]
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
```

</details>
