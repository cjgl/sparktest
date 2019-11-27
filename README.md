# spark-shell
	val textFile = sc.textFile("file:///tmp/a.txt");
	textFile.first();
	textFile.count();
	
	val textFilter = textFile.filter(line=>line.contains("Spark"));
	textFile.filter(line=>line.contains("Spark")).count();
	
	val textFile1 = sc.textFile("hdfsInput");
	val wordCount = textFile1.flatMap(line =>line.split(" ")).map(x => (x,1)).reduceByKey((a,b) => a+b);
	wordCount.collect

#  spark-submit
	spark-submit \
	--class cn.fy.SparkDemo \
	--driver-library-path /opt/cloudera/parcels/SPARK22.4.0.cloudera21.cdh5.13.3.p0.1041012/lib/spark2/jars \
	--master local \
	/root/sparktest.jar
	
	spark-submit \
	--class cn.fy.JavaWordCount \
	--driver-library-path /opt/cloudera/parcels/SPARK22.4.0.cloudera21.cdh5.13.3.p0.1041012/lib/spark2/jars \
	--master local \
	/root/sparktest.jar JavaWordCount a.txt
	
	spark-submit \
	--class cn.fy.JavaWordCount \
	--driver-library-path /root/lib/*.jar \
	--master local \
	/root/sparktest.jar JavaWordCount a.txt

