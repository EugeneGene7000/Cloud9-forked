Cloud9
======

Privately forked from https://github.com/lintool/Cloud9/ to add more functionality for Klout purposes. May be open-sourced later.

Instructions for building the Klout Cloud9 jar:
```
1. ssh klout@sci1
2. cd ~/dev/Cloud9-forked/
3. git pull -r
4. ant clean; ant
5. sudo cp dist/cloud9-1.6.0-klout.jar /home/research/lib/
```
Then upload to Maven manually http://maven-repo.klout:8081/artifactory/

Also copy to Thunder at ~/thunder/lib/, and to hdfs at /user/thunder/hive_data_store/lib/
This is temporary ^^, no need once https://github.com/klout/code/pull/540 is merged and deployed.


NOTE: Build using Java 1.6 since we were having issues with 1.7. Built on sci1 box since it has the right java version for compiling this jar.


```
ssh <herever lib is >
cd  /home/research/lib/

 LANGUAGE=de
 hadoop jar cloud9-1.5.0-klout.jar \
   edu.umd.cloud9.collection.wikipedia.DumpWikipediaToPlainText \
   -libjars bliki-core-3.0.16.jar,commons-lang3-3.1jarBAK,commons-lang3-3.2.jar \
   -input /data/prod/inputs/wikipedia/20150716/xmldump/${LANGUAGE}wiki-latest-pages-articles.xml \
   -output /data/hive/research/test_wiki_text/20150716/${LANGUAGE} \
   -wiki_language $LANGUAGE \
   -content_format WIKI

```
