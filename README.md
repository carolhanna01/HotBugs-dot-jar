# HotBugs.jar: A Diverse Dataset of Time-Critcal Bugs for Java Hot Fixing

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

## HotBugs.jar Time-critical Bugs Included

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
| **Total**    | **78**    |

Developed by Carol Hanna, Prof. Federica Sarro, and Prof. Justyna Petke at the [SOLAR group](https://solar.cs.ucl.ac.uk/) within University College London's Department of Computer Science. 

## Disclamer
THIS SOFTWARE DATA SET IS PROVIDED BY THE COPYRIGHT HOLDER AND CONTRIBUTOR "AS IS." BY USING THE SOFTWARE DATA SET, YOU EXPRESSLY UNDERSTAND AND AGREE THAT, EXCEPT TO THE EXTENT PROHIBITED BY LAW, ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE, AND/OR ANY WARRANTIES THAT THIS SOFTWARE DATA SET WILL BE ERROR FREE OR FREE OF HARMFUL COMPONENTS, ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE DATA SET, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

You understand and agree that you will not: 1) make false or misleading statements or representations regarding Fujitsu or Fujitsu products and services; 2) take on any obligation or responsibility, or make any representation, warranty, guarantee or endorsement to anyone on Fujitsu’s behalf (including, without limitation, any of our products or services); and that you will not state or imply that Fujitsu has developed, endorsed, reviewed or otherwise approved of any of your products.  You agree that you will indemnify, defend and hold us harmless from and against any and all claims which may arise under or out of your use of the Software Data Set; your negligence or intentional misconduct; your products, or any integrations you develop, design, promote or distribute using the Software Data Set; any misrepresentations you make with respect to Fujitsu, or Fujitsu products or services.
