# cat input.txt                                               
cat input.txt | python mapper.py                           
cat input.txt | python mapper.py | sort | python reducer.py
hadoop fs -rm input.txt
hadoop fs -rm -r laboutput
hadoop fs -put input.txt
hadoop fs -ls
hadoop jar /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-2.6.0-mr1-cdh5.4.2.jar -files /home/cloudera/BDA-Lab/mapper.py,/home/cloudera/BDA-Lab/reducer.py -mapper "python mapper.py" -reducer "python reducer.py" -input /user/cloudera/input.txt -output /user/cloudera/laboutput
hadoop fs -ls /user/cloudera/laboutput
hadoop fs -cat /user/cloudera/laboutput/part-00000
