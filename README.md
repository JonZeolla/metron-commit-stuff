# Apache Metron Committer Tools

## Prepare Commit

This script automates the process of merging a pull request into the upstream apache git repo.  The script will ask which of the metron repos you are working on, and the respective pull request number.  Most of the remaining information is extracted from Github or JIRA.

In the following example, I use the default `metron` repo, and enter the pull request number (`865`) when prompted.  Using the pull request number, the script can extract most of the remaining required information.

When prompted the `[value in brackets]` will be used by default.  To accept the default, simply press `enter`.  If you would like to change the default, type it in and hit `enter` when done.

(1) Execute the script and answer the questions when prompted.

```
$ ./prepare-commit
  ...using settings from /Users/jzeolla/.metron-prepare-commit
  which repo? [metron]:
  pull request: 865
  origin repo [https://github.com/apache/metron]:
  local working directory [/Users/jzeolla/tmp/metron-pr865]:
Cloning into '/Users/jzeolla/tmp/metron-pr865'...
remote: Counting objects: 36248, done.
remote: Compressing objects: 100% (90/90), done.
remote: Total 36248 (delta 30), reused 31 (delta 13), pack-reused 36138
Receiving objects: 100% (36248/36248), 57.84 MiB | 7.36 MiB/s, done.
Resolving deltas: 100% (13645/13645), done.
From https://git-wip-us.apache.org/repos/asf/metron
 * branch              master     -> FETCH_HEAD
 * [new branch]        master     -> upstream/master
Already on 'master'
Your branch is up to date with 'origin/master'.
Already up to date.
remote: Counting objects: 343, done.
remote: Total 343 (delta 142), reused 142 (delta 142), pack-reused 200
Receiving objects: 100% (343/343), 106.47 KiB | 13.31 MiB/s, done.
Resolving deltas: 100% (172/172), completed with 54 local objects.
From https://github.com/apache/metron
 * [new ref]           refs/pull/865/head -> pr-865

  github contributor's username [ottobackwards]:
  github contributor's email [ottobackwards@gmail.com]:
  issue identifier in jira [METRON-1212]:
  issue description [Bundles and Maven Plugin]:
  commit message [METRON-1212 Bundles and Maven Plugin (ottobackwards via JonZeolla) closes apache/metron#865]:
```

(2) At this point the PR will be LOCALLY merged into master (nothing at this point has been pushed upstream), and you will be shown a summary of the changes that were made.

```
Squash commit -- not updating HEAD
Automatic merge went well; stopped before committing as requested
[master 17ecebf7] METRON-1212 Bundles and Maven Plugin (ottobackwards via JonZeolla) closes apache/metron#865
 Author: ottobackwards <ottobackwards@gmail.com>
 80 files changed, 9838 insertions(+)
 create mode 100644 bundles-maven-plugin/LICENSE
 create mode 100644 bundles-maven-plugin/NOTICE
 create mode 100644 bundles-maven-plugin/README.md
 create mode 100644 bundles-maven-plugin/pom.xml
 create mode 100644 bundles-maven-plugin/src/main/java/org/apache/metron/maven/plugins/bundles/BundleMojo.java
 create mode 100644 bundles-maven-plugin/src/main/java/org/apache/metron/maven/plugins/bundles/BundleProvidedDependenciesMojo.java
 create mode 100644 bundles-maven-plugin/src/main/resources/META-INF/plexus/components.xml
 create mode 100644 metron-bundles/bundles-lib/README.md
 create mode 100644 metron-bundles/bundles-lib/Usage_Sample.md
 create mode 100644 metron-bundles/bundles-lib/pom.xml
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleClassLoaders.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleClassLoadersContext.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleManifestEntry.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleMapper.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleSystem.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleSystemBuilder.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleSystemType.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleThreadContextClassLoader.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/DefaultBundleSystem.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/ExtensionManager.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/ExtensionManagerContext.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/ExtensionMapping.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/InstanceClassLoader.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/NotInitializedException.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/OnDemandBundleSystem.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/VfsBundleClassLoader.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/VfsBundleClassLoaderResource.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/annotation/behavior/RequiresInstanceClassLoading.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/bundle/Bundle.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/bundle/BundleCoordinates.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/bundle/BundleDetails.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/BundleProperties.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/BundleSelector.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/BundleUtil.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/DummyFileObject.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/FileSystemManagerFactory.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/FileUtils.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/ImmutableCollectionUtils.java
 create mode 100644 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/StringUtils.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/AbstractFoo.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/AbstractFoo2.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleClassLoadersContextTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleClassLoadersTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleMapperTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleSystemTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleThreadContextClassLoaderTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleUtilTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/ExtensionClassInitializerTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/ExtensionManagerContextTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/ExtensionManagerTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/integration/BundleMapperIntegrationTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/util/ImmutableCollectionUtilsTest.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/util/ResourceCopier.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/util/TestUtil.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/parsers/BasicParser.java
 create mode 100644 metron-bundles/bundles-lib/src/test/java/org/apache/metron/parsers/interfaces/MessageParser.java
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/BundleMapper/conf/bundle.properties
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/BundleMapper/lib/metron-parser-bar-bundle-0.4.1.bundle
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/BundleMapper/lib2/metron-parser-foo-bundle-0.4.1.bundle
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/BundleMapper/metron-parser-foo-bundle-0.4.1.bundle
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/META-INF/services/org.apache.metron.bundles.AbstractFoo
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/bundle.properties
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/utils-bundles/bundle-with-versioning/META-INF/MANIFEST.MF
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/utils-bundles/bundle-without-dependency/META-INF/MANIFEST.MF
 create mode 100644 metron-bundles/bundles-lib/src/test/resources/utils-bundles/bundle-without-versioning/META-INF/MANIFEST.MF
 create mode 100644 metron-bundles/bundles-testing/README.md
 create mode 100644 metron-bundles/bundles-testing/bundles-test-bundle/pom.xml
 create mode 100644 metron-bundles/bundles-testing/bundles-test-implementation/pom.xml
 create mode 100644 metron-bundles/bundles-testing/bundles-test-implementation/src/main/java/org/apache/test/TestImplementation.java
 create mode 100644 metron-bundles/bundles-testing/bundles-test-integration/pom.xml
 create mode 100644 metron-bundles/bundles-testing/bundles-test-integration/src/test/java/org/apache/test/BundlesTestIntegrationTest.java
 create mode 100644 metron-bundles/bundles-testing/bundles-test-integration/src/test/resources/bundle.properties
 create mode 100644 metron-bundles/bundles-testing/bundles-test-integration/src/test/resources/bundles-test-0.4.2.bundle
 create mode 100644 metron-bundles/bundles-testing/bundles-test-interfaces/pom.xml
 create mode 100644 metron-bundles/bundles-testing/bundles-test-interfaces/src/main/java/org/apache/test/TestInterface.java
 create mode 100644 metron-bundles/bundles-testing/pom.xml
 create mode 100644 metron-bundles/pom.xml


 .travis.yml                                                                                                              |   1 +
 README.md                                                                                                                |   6 +
 bundles-maven-plugin/LICENSE                                                                                             | 202 ++++++++++++++++++++++++++++++
 bundles-maven-plugin/NOTICE                                                                                              |   8 ++
 bundles-maven-plugin/README.md                                                                                           | 232 ++++++++++++++++++++++++++++++++++
 bundles-maven-plugin/pom.xml                                                                                             | 328 ++++++++++++++++++++++++++++++++++++++++++++++++
 bundles-maven-plugin/src/main/java/org/apache/metron/maven/plugins/bundles/BundleMojo.java                               | 743 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 bundles-maven-plugin/src/main/java/org/apache/metron/maven/plugins/bundles/BundleProvidedDependenciesMojo.java           | 328 ++++++++++++++++++++++++++++++++++++++++++++++++
 bundles-maven-plugin/src/main/resources/META-INF/plexus/components.xml                                                   |  52 ++++++++
 metron-bundles/bundles-lib/README.md                                                                                     | 231 ++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/Usage_Sample.md                                                                               | 667 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/pom.xml                                                                                       | 185 +++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleClassLoaders.java                               | 168 +++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleClassLoadersContext.java                        | 404 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleManifestEntry.java                              |  40 ++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleMapper.java                                     | 197 +++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleSystem.java                                     |  76 ++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleSystemBuilder.java                              | 187 ++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleSystemType.java                                 |  34 +++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/BundleThreadContextClassLoader.java                   | 218 ++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/DefaultBundleSystem.java                              | 117 ++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/ExtensionManager.java                                 | 404 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/ExtensionManagerContext.java                          | 365 ++++++++++++++++++++++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/ExtensionMapping.java                                 | 160 ++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/InstanceClassLoader.java                              | 165 ++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/NotInitializedException.java                          |  41 ++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/OnDemandBundleSystem.java                             |  76 ++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/VfsBundleClassLoader.java                             | 483 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/VfsBundleClassLoaderResource.java                     | 110 ++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/annotation/behavior/RequiresInstanceClassLoading.java |  46 +++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/bundle/Bundle.java                                    |  62 ++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/bundle/BundleCoordinates.java                         | 103 +++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/bundle/BundleDetails.java                             | 210 +++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/BundleProperties.java                            | 294 +++++++++++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/BundleSelector.java                              |  57 +++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/BundleUtil.java                                  | 145 ++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/DummyFileObject.java                             | 229 ++++++++++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/FileSystemManagerFactory.java                    |  89 +++++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/FileUtils.java                                   |  48 +++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/ImmutableCollectionUtils.java                    |  65 ++++++++++
 metron-bundles/bundles-lib/src/main/java/org/apache/metron/bundles/util/StringUtils.java                                 | 168 +++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/AbstractFoo.java                                      |  24 ++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/AbstractFoo2.java                                     |  27 ++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleClassLoadersContextTest.java                    | 139 +++++++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleClassLoadersTest.java                           | 105 ++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleMapperTest.java                                 | 175 ++++++++++++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleSystemTest.java                                 | 126 +++++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleThreadContextClassLoaderTest.java               | 142 +++++++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/BundleUtilTest.java                                   | 125 +++++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/ExtensionClassInitializerTest.java                    |  33 +++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/ExtensionManagerContextTest.java                      | 110 ++++++++++++++++
 metron-bundles/bundles-lib/src/test/java/org/apache/metron/bundles/ExtensionManagerTest.java                             |  82 ++++++++++++
```

(3) You will then be asked if you would like to run the test suite against the resultant repo.

```
17ecebf7 (HEAD -> master) METRON-1212 Bundles and Maven Plugin (ottobackwards via JonZeolla) closes apache/metron#865


  run test suite? [yN]
```

(4) If you are happy with the state of this local repo, then simply follow the instructions to push the changes to Apache.  If you are not happy, simply start over.  Nothing changes in Apache Land until you run the following command.

```
    cd /Users/jzeolla/tmp/metron-pr865
    git push upstream master
```

## Checkout PR

The `checkout-pr` script will checkout the branch for the specified pull request.  This makes it easy to checkout the code for a pull request and manually execute a test or validate the code.

```
$ ./checkout-pr 80
Cloning into 'metron-pr-80'...
remote: Counting objects: 7028, done.
remote: Compressing objects: 100% (56/56), done.
remote: Total 7028 (delta 15), reused 0 (delta 0), pack-reused 6960
Receiving objects: 100% (7028/7028), 39.69 MiB | 9.14 MiB/s, done.
Resolving deltas: 100% (2476/2476), done.
Checking connectivity... done.
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
From http://github.com/apache/metron
 * [new ref]         refs/pull/80/head -> pr-80
Switched to branch 'pr-80'

$ cd metron-pr-80/

$ git branch
  master
* pr-80
```

If you execute the command within an existing repository, then the repository will not be cloned again.

```
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean

$ ../checkout-pr 81
remote: Counting objects: 77, done.
remote: Compressing objects: 100% (51/51), done.
remote: Total 77 (delta 10), reused 2 (delta 2), pack-reused 0
Unpacking objects: 100% (77/77), done.
From http://github.com/apache/metron
 * [new ref]         refs/pull/81/head -> pr-81
Switched to branch 'pr-81'

$ git status
On branch pr-81
nothing to commit, working directory clean
```
