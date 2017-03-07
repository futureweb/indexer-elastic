#Nutch-2.3.1-ES5-Indexer

##Description

Apache Nutch 2.3.x is currently designed to work with ElasticSearch 2.3.3. While this works for most I wanted to update the indexer-elastic in Apache Nutch to work with ElasticSearch 5. This is my initial attempt...

##Notable Changes

 - Updated ivy.xml in Apache Nutch:
	 - Added Netty-all version 3 dependency
	 - Updated org.restlet to 2.3.9
 - Updated indexer-elastic to redo connection using newer Transport Client methods.
 
  
##How To Get This Running:

~~~$NUTCH_HOME refers to the extracted location of your Nutch instance. 

 1. Copy ixy.xml to $NUTCH_HOME/ivy/ivy.xml
 2. Copy indexer-elastic to $NUTCH_HOME/src/plugin/
 3. Copy default.properties to $NUTCH_HOME/
 4. Add Following Configuration to $NUTCH_HOME/conf/nutch-site.xml in the < configuration > element
 
 ```xml
<property>
    <name>elastic.host</name>
    <value>localhost</value>
</property>
<property>
    <name>elastic.port</name>
    <value>9300</value>
</property>
<property>
    <name>elastic.cluster</name>
    <value>elasticsearch</value>
</property>
<property>
    <name>elastic.index</name>
    <value>nutchindex</value>
</property>
<property>
  <name>elastic.max.bulk.docs</name>
  <value>250</value>
  <description>Maximum size of the bulk in number of documents.</description>
</property>
<property>
  <name>elastic.max.bulk.size</name>
  <value>2500500</value>
  <description>Maximum size of the bulk in bytes.</description>
</property>
```

 5. Run ant runtime on $NUTCH_HOME then run nutch as you normally would.
