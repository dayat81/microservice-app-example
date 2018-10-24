FROM eivantsov/users-api
COPY . .
RUN mvn clean install
RUN chgrp -R 0 /root && \
               chmod -R g+rwX /root && \
               chgrp -R 0 /projects && \
               chmod -R g+rwX /projects

CMD cd /usr/src/app/target && \
    java -jar -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=8000 -Dserver.port=8083 users-api-0.0.1-SNAPSHOT.jar & \
    tail -f /dev/null
