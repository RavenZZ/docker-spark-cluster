FROM ravenzz/spark-hadoop

MAINTAINER RavenZZ <raven.zhu@outlook.com>


ADD ./target/score-0.0.8-jar-with-dependencies.jar /app/application.jar



ENV SPARK_MASTER_NAME 172.17.30.222
ENV SPARK_MASTER_PORT 50002
ENV SPARK_APPLICATION_JAR_LOCATION /app/application.jar
ENV SPARK_APPLICATION_MAIN_CLASS score.PostBeLikedCount
ENV POST_MONGODB mongodb://172.17.30.240:27017,172.17.30.103:27017/mdpost.post
ENV TASK_MONGODB mongodb://172.17.30.240:27017,172.17.30.103:27017/taskcenter.taskTopic
ENV SCORE_MONGODB mongodb://172.17.30.240:27017,172.17.30.103:27017/mdscore.score
ENV SPARK_APPLICATION_ARGS \
    --input=$POST_MONGODB \
    --output=$SCORE_MONGODB \
    #--sparkMaster=spark://$SPARK_MASTER_NAME:$SPARK_MASTER_PORT \
    --startDate=2017-1-1 \
    --endDate=2017-1-2

COPY ./docker/submit/submit.sh /

#CMD ["/bin/bash", "/submit.sh"]
CMD ping 172.17.10.164