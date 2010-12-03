Maven Archetype for Hadoop
==========================

This project is a small template to quickly create a new Maven based project that creates Hadoop MapReduce job jars.

It uses the Cloudera Maven repository to access the dependencies for Hadoop related artifacts.

Building
--------

The process is very simple, you clone this project and create an archetype jar from it like so::

    $ cd /tmp
    $ git clone git@github.com:larsgeorge/maven-archetype-hadoop.git
    Initialized empty Git repository in /private/tmp/maven-archetype-hadoop/.git/
    remote: Counting objects: 13, done.
    remote: Compressing objects: 100% (8/8), done.
    remote: Total 13 (delta 2), reused 0 (delta 0)
    Receiving objects: 100% (13/13), done.
    Resolving deltas: 100% (2/2), done.

    $ cd maven-archetype-hadoop/
    $ $ mvn archetype:create-from-project
    [INFO] Scanning for projects...
    [INFO] Searching repository for plugin with prefix: 'archetype'.
    [INFO] ------------------------------------------------------------------------
    [INFO] Building mapred
    [INFO]    task-segment: [archetype:create-from-project] (aggregator-style)
    [INFO] ------------------------------------------------------------------------
    [INFO] Preparing archetype:create-from-project
    [INFO] ------------------------------------------------------------------------
    [INFO] Building mapred
    [INFO] ------------------------------------------------------------------------
    [INFO] No goals needed for project - skipping
    [INFO] [archetype:create-from-project {execution: default-cli}]
    [INFO] Setting default groupId: com.larsgeorge
    [INFO] Setting default artifactId: mapred
    [INFO] Setting default version: 1.0-SNAPSHOT
    [INFO] Setting default package: com.larsgeorge
    [INFO] Scanning for projects...
    [INFO] ------------------------------------------------------------------------
    [INFO] Building mapred-archetype
    [INFO]    task-segment: [package]
    [INFO] ------------------------------------------------------------------------
    [INFO] [resources:resources {execution: default-resources}]
    [INFO] Copying 5 resources
    [INFO] [resources:testResources {execution: default-testResources}]
    [INFO] Copying 2 resources
    [INFO] [archetype:jar {execution: default-jar}]
    [INFO] [archetype:add-archetype-metadata {execution: default-add-archetype-metadata}]
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESSFUL
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 2 seconds
    [INFO] Finished at: Fri Dec 03 01:10:16 CET 2010
    [INFO] Final Memory: 20M/81M
    [INFO] ------------------------------------------------------------------------
    [INFO] Archetype created in /private/tmp/maven-archetype-hadoop/target/generated-sources/archetype
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESSFUL
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 6 seconds
    [INFO] Finished at: Fri Dec 03 01:10:16 CET 2010
    [INFO] Final Memory: 17M/81M
    [INFO] ------------------------------------------------------------------------

With that you have build the archetype you now need to install into your local repository::

    $ cd target/generated-sources/archetype/
    $ mvn install
    [INFO] Scanning for projects...
    [INFO] ------------------------------------------------------------------------
    [INFO] Building mapred-archetype
    [INFO]    task-segment: [install]
    [INFO] ------------------------------------------------------------------------
    [INFO] [resources:resources {execution: default-resources}]
    [INFO] Copying 5 resources
    [INFO] [resources:testResources {execution: default-testResources}]
    [INFO] Copying 2 resources
    [INFO] [archetype:jar {execution: default-jar}]
    [INFO] [archetype:add-archetype-metadata {execution: default-add-archetype-metadata}]
    [INFO] [archetype:integration-test {execution: default-integration-test}]
    [INFO] [install:install {execution: default-install}]
    [INFO] Installing /private/tmp/maven-archetype-hadoop/target/generated-sources/archetype/target/mapred-archetype-1.0-SNAPSHOT.jar to /Users/larsgeorge/.m2/repository/com/larsgeorge/mapred-archetype/1.0-SNAPSHOT/mapred-archetype-1.0-SNAPSHOT.jar
    [INFO] [archetype:update-local-catalog {execution: default-update-local-catalog}]
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESSFUL
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 6 seconds
    [INFO] Finished at: Fri Dec 03 01:11:34 CET 2010
    [INFO] Final Memory: 21M/81M
    [INFO] ------------------------------------------------------------------------

Now you can create a new project using this archetype::

    $ cd /tmp
    $ mvn archetype:generate -DarchetypeCatalog=local
    [INFO] Scanning for projects...
    [INFO] Searching repository for plugin with prefix: 'archetype'.
    [INFO] ------------------------------------------------------------------------
    [INFO] Building Maven Default Project
    [INFO]    task-segment: [archetype:generate] (aggregator-style)
    [INFO] ------------------------------------------------------------------------
    [INFO] Preparing archetype:generate
    [INFO] No goals needed for project - skipping
    [INFO] [archetype:generate {execution: default-cli}]
    [INFO] Generating project in Interactive mode
    [INFO] No archetype defined. Using maven-archetype-quickstart (org.apache.maven.archetypes:maven-archetype-quickstart:1.0)
    Choose archetype:
    1: local -> mapred-archetype (mapred-archetype)
    Choose a number: : 1
    Define value for property 'groupId': : com.foobar
    Define value for property 'artifactId': : mapred
    Define value for property 'version': 1.0-SNAPSHOT:
    Define value for property 'package': com.foobar:
    Confirm properties configuration:
    groupId: com.foobar
    artifactId: mapred
    version: 1.0-SNAPSHOT
    package: com.foobar
    Y: Y
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESSFUL
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 1 minute 3 seconds
    [INFO] Finished at: Fri Dec 03 01:13:34 CET 2010
    [INFO] Final Memory: 16M/81M
    [INFO] ------------------------------------------------------------------------

Looking into the directory we got::

    larsgeorge@de1-app-mbp-2:/tmp$ ls -laR mapred
    total 24
    drwxr-xr-x   6 larsgeorge  wheel   204 Dec  3 00:43 .
    drwxrwxrwt  19 root        wheel   646 Dec  3 00:43 ..
    -rw-r--r--   1 larsgeorge  wheel    21 Dec  3 00:43 .gitignore
    -rw-r--r--   1 larsgeorge  wheel   268 Dec  3 00:43 README.rst
    -rw-r--r--   1 larsgeorge  wheel  1673 Dec  3 00:43 pom.xml
    drwxr-xr-x   3 larsgeorge  wheel   102 Dec  3 00:43 src

    mapred/src:
    total 0
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 .
    drwxr-xr-x  6 larsgeorge  wheel  204 Dec  3 00:43 ..
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 main

    mapred/src/main:
    total 0
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 .
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 ..
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 java

    mapred/src/main/java:
    total 0
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 .
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 ..
    drwxr-xr-x  3 larsgeorge  wheel  102 Dec  3 00:43 com.larsgeorge

    mapred/src/main/java/com.larsgeorge:
    total 8
    drwxr-xr-x  3 larsgeorge  wheel   102 Dec  3 00:43 .
    drwxr-xr-x  3 larsgeorge  wheel   102 Dec  3 00:43 ..
    -rw-r--r--  1 larsgeorge  wheel  2365 Dec  3 00:43 WordCount.java

Let's check if it compiles on its own::

    $ cd mapred
    $ mvn package
    [INFO] Scanning for projects...
    [INFO] ------------------------------------------------------------------------
    [INFO] Building mapred
    [INFO]    task-segment: [package]
    [INFO] ------------------------------------------------------------------------
    [INFO] [resources:resources {execution: default-resources}]
    [INFO] Using 'UTF-8' encoding to copy filtered resources.
    [INFO] skip non existing resourceDirectory /private/tmp/mapred/src/main/resources
    [INFO] [compiler:compile {execution: default-compile}]
    [INFO] Compiling 1 source file to /private/tmp/mapred/target/classes
    [INFO] [resources:testResources {execution: default-testResources}]
    [INFO] Using 'UTF-8' encoding to copy filtered resources.
    [INFO] skip non existing resourceDirectory /private/tmp/mapred/src/test/resources
    [INFO] [compiler:testCompile {execution: default-testCompile}]
    [INFO] No sources to compile
    [INFO] [surefire:test {execution: default-test}]
    [INFO] No tests to run.
    [INFO] [jar:jar {execution: default-jar}]
    [INFO] Building jar: /private/tmp/mapred/target/mapred-1.0-SNAPSHOT.jar
    [INFO] ------------------------------------------------------------------------
    [INFO] BUILD SUCCESSFUL
    [INFO] ------------------------------------------------------------------------
    [INFO] Total time: 3 seconds
    [INFO] Finished at: Fri Dec 03 01:15:37 CET 2010
    [INFO] Final Memory: 25M/81M
    [INFO] ------------------------------------------------------------------------

And finally we check if there is a job jar ready to be uploaded to a cluster for action::

    $ ls -la target/
    total 16
    drwxr-xr-x  6 larsgeorge  wheel   204 Dec  3 01:15 .
    drwxr-xr-x  7 larsgeorge  wheel   238 Dec  3 01:15 ..
    drwxr-xr-x  3 larsgeorge  wheel   102 Dec  3 01:15 classes
    drwxr-xr-x  3 larsgeorge  wheel   102 Dec  3 01:15 generated-sources
    -rw-r--r--  1 larsgeorge  wheel  5380 Dec  3 01:15 mapred-1.0-SNAPSHOT.jar
    drwxr-xr-x  3 larsgeorge  wheel   102 Dec  3 01:15 maven-archiver

Done!