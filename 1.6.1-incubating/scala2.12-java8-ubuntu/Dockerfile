#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM eclipse-temurin:8-jdk-focal

ARG kyuubi_uid=10009

USER root

ENV KYUUBI_USER_HOME /home/kyuubi
ENV KYUUBI_HOME /opt/kyuubi
ENV KYUUBI_LOG_DIR ${KYUUBI_HOME}/logs
ENV KYUUBI_PID_DIR ${KYUUBI_HOME}/pid
ENV KYUUBI_WORK_DIR_ROOT ${KYUUBI_HOME}/work

RUN set -ex; \
   sed -i 's/http:\/\/deb.\(.*\)/https:\/\/deb.\1/g' /etc/apt/sources.list && \
   apt-get update && \
   apt install -y wget bash tini libc6 libpam-modules krb5-user libnss3 procps && \
   mkdir -p ${KYUUBI_HOME} ${KYUUBI_LOG_DIR} ${KYUUBI_PID_DIR} ${KYUUBI_WORK_DIR_ROOT} && \
   rm -rf /var/cache/apt/* && rm -rf /var/lib/apt/lists/*

COPY . ${KYUUBI_HOME}

# setup kyuubi
RUN set -ex && \
   useradd -u ${kyuubi_uid} -g root kyuubi -d ${KYUUBI_USER_HOME} -m && \
   chmod ug+rw -R ${KYUUBI_HOME} && \
   chmod a+rwx -R ${KYUUBI_WORK_DIR_ROOT}

WORKDIR ${KYUUBI_HOME}

CMD [ "./bin/kyuubi", "run" ]

USER ${kyuubi_uid}
