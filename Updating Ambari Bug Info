# HotBugs.jar: A Diverse Dataset of Time-Critcal Bugs for Java Hot Fixing

<p align="center">
  <img src="logo.png" alt="HotBugs.jar Logo" width="300"/>
</p>

HotBugs.jar is built as an extension of the widely used [Bugs.jar](https://github.com/bugs-dot-jar/bugs-dot-jar) dataset. It is composed of a set of Apache Java time-critical bugs that were addressed with a hot fix. It introduces a more focused subset of bugs based on urgency and impact. Each included bug is labeled as high priority in its corresponding Jira issue, was resolved within a short time frame from issue creation, and is associated with a nearby release tag in the project's version history. This focus makes HotBugs.jar especially suited for studying rapid bug resolution, automated repair under production pressure, and tools for emergency software maintenance.

For more information and resources, visit the [HotBugs.jar project page](https://solar.cs.ucl.ac.uk/os/hotfixbenchmark.html).

## How To Install

For the first time, you should clone this repository as well as its submodules:
```
$ git clone --recursive https://github.com/carolhanna01/HotBugs-dot-jar
```

To update the dataset, don't forget to update the submodules as well:
```
$ git pull --recurse-submodules && git submodule update --recursive
```

## Directory & File Structure
To browse a specific bug data, please go to one of the following project directories and select a branch starting with "bugs-dot-jar-" and ending with "\_HOTFIX".  The branch names follow the format: "bugs-dot-jar\_\[JIRA Issue ID\]\_\[Git commit ID of the fixed version\]\_HOTFIX.  Each branch in a project represents the buggy version corresponding to the JIRA Issue and also includes the bug report, the developer patch, and the test results under `.bugs-dot-jar` directory.
```
.
.
.
+-- flink
|   +-- .bugs-dot-jar
|       +-- bug-report.yml
|       +-- developer-patch.diff
|       +-- test-results.txt
+-- hadoop
|   +-- ...
+-- hbase
|   +-- ...
+-- flink
|   +-- ...
.
.
.
```

## The HotBugs.jar Time-critical Bugs

| Project    | Number of HotBugs |
| -------- | ------- |
| Kafka  | 6    |
| Flink | 15     |
| Solr    | 12    |
| HBase  | 5    |
| Karaf | 1     |
| JackRabbit    | 4    |
| Hadoop  | 21    |
| Nifi | 11     |
| Calcite    | 3    |
| Ambari    | 10    |
| **Total**    | **88**    |

## Requirements
Each bug in the dataset may has its own specific requirements, depending on the project it belongs to and the version of the project it affects. These details are documented in the [additional bug information sheet](https://docs.google.com/spreadsheets/d/1oOOJ3CexSJemAFUedXL9inDIqLWjDZ4Furg22MMc8VE/edit?gid=1536192333#gid=1536192333), including build systems, compatible Java versions, and other setup notes.

To run most bugs in this dataset, you will generally need the following tools installed:

- Java: Version 8,11,17,21 (depending on the bug)
- Gradle 4.4.1
- Maven version 3.6.3 or 3.8.4
- Libprotoc 3.12.4 (for Hadoop specifically)

## Example of Running a Bug

For example, you can checkout the buggy version corresponding to the JIRA Issue [FLINK-18425]([https://issues.apache.org/jira/browse/ACCUMULO-1051](https://issues.apache.org/jira/browse/FLINK-18425)) as follows:
```
$ cd flink
$ git branch -a | grep bugs-dot-jar_ | grep _HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-15062_d0fbd344_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-15914_2558c9ee_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-17552_91a0c8c5_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-18425_00863a28_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-18428_95b9adbe_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-19166_42d8dde0_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-24282_724fb3d8_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-25949_74c45c48_HOTFIX
  remotes/origin/bugs-dot-jar_FLINK-26819_9c3be7e6_HOTFIX
  ...
$ git checkout bugs-dot-jar_FLINK-18425_00863a28_HOTFIX
Branch 'bugs-dot-jar_FLINK-18425_00863a28_HOTFIX' set up to track remote branch 'bugs-dot-jar_FLINK-18425_00863a28_HOTFIX' from 'origin'.
Switched to a new branch 'bugs-dot-jar_FLINK-18425_00863a28_HOTFIX'
$ ls -a .bugs-dot-jar
.                      bug-report.yml         
..                     developer-patch.diff   test-results.txt
```

You can then build the project with the following command in the root dir:

```
$ mvn clean install -DskipTests -U
```
By running the following you can find the submodule that the bug resides in and run its corresponding tests to reveal the bug:
```
$ cat .bugs-dot-jar/developer-patch.diff | grep diff
    diff --git a/flink-table/flink-table-common/src/main/java/org/apache/flink/table/data/GenericArrayData.java b/flink-table/flink-table-common/src/main/java/org/apache/flink/table/        data/GenericArrayData.java
    diff --git a/flink-table/flink-table-common/src/main/java/org/apache/flink/table/data/binary/BinaryArrayData.java b/flink-table/flink-table-common/src/main/java/org/apache/flink/        table/data/binary/BinaryArrayData.java
    diff --git a/flink-table/flink-table-runtime-blink/src/test/java/org/apache/flink/table/data/DataStructureConvertersTest.java b/flink-table/flink-table-runtime-blink/src/test/java/      org/apache/flink/table/data/DataStructureConvertersTest.java
$ cd flink-tables
$ mvn clean test
  INFO] ------------------------------------------------------------------------
  [INFO] BUILD FAILURE
  [INFO] ------------------------------------------------------------------------
  [ERROR] Failed to execute goal org.apache.maven.plugins:maven-surefire-plugin:2.22.1:test (default-test) on project flink-table-common: There are test failures.
```
The developer patch can then be applied from the Flink project root dir and tests can be rerun to pass on the patched code:
```
$ cd ..
$ git apply .bugs-dot-jar/developer-patch.diff
$ cd flink-tables
$ mvn clean install
  [INFO] ------------------------------------------------------------------------
  [INFO] BUILD SUCCESS
  [INFO] ------------------------------------------------------------------------
```
## Maintenance

Developed by Carol Hanna, Prof. Federica Sarro, and Prof. Justyna Petke at the [SOLAR group](https://solar.cs.ucl.ac.uk/) within University College London's Department of Computer Science. 

Please direct your inquiries to [carol.hanna.21@ucl.ac.uk](mailto:carol.hanna.21@ucl.ac.uk)

## License

See license.txt
