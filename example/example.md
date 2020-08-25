```bash
tar xzf oozie-examples.tar.gz
hdfs dfs -put examples/ /tmp/examples
vi examples/apps/map-reduce/job.properties
oozie job -oozie http://c7401.ambari.apache.org:11000/oozie -config examples/apps/map-reduce/job.properties -run
```

```bash
nameNode=hdfs://c7401.ambari.apache.org:8020
jobTracker=c7401.ambari.apache.org:8021
queueName=default
examplesRoot=examples

oozie.wf.application.path=${nameNode}/tmp/${examplesRoot}/apps/map-reduce/workflow.xml
outputDir=map-reduce
```


```bash
job: 0000000-200825011031382-oozie-oozi-W

oozie job -oozie http://c7401.ambari.apache.org:11000/oozie -info 0000000-200825011031382-oozie-oozi-W

export OOZIE_URL="http://c7401.ambari.apache.org:11000/oozie"
oozie job -info 0000000-200825011031382-oozie-oozi-W


oozie job -oozie http://c7401.ambari.apache.org:11000/oozie -kill 0000000-200825011031382-oozie-oozi-W
```

---

```bash
sudo useradd walker
sudo passwd walker
su walker

vi apple.sh
echo $(date) 'apple' $1 >> out.apple
chmod +x apple.sh
```

---

```bash
vi run.sh
vi workflow.xml
vi job.properties

hdfs dfs -copyFromLocal -f run.sh run.sh
hdfs dfs -copyFromLocal -f workflow.xml workflow.xml

hdfs dfs -ls /user/vagrant

oozie job -oozie http://c7401.ambari.apache.org:11000/oozie -config job.properties -run
```

---

```bash
sudo su hdfs
hdfs dfs -mkdir /user/vagrant
hdfs dfs -chown vagrant /user/vagrant
hdfs dfs -chmod 775 /user/vagrant
hdfs dfs -ls /user
```

---

```bash
ssh-keygen -t rsa
sudo cp ~/.ssh/id_rsa.pub /home/hdfs/.ssh/authorized_keys

sudo mkdir -p /home/hdfs/.ssh
sudo chown -R hdfs:hadoop /home/hdfs/.ssh
sudo chmod 600 /home/hdfs/.ssh/authorized_keys
```

---