1.자바 JDK 설치 및 PATH 환경설정

vi /etc/profile 맨 아래에 추가.

자바PATH는 /usr/local/java에 설정하기!

```bash
[root@master ~]# cd
[root@master ~]# vi /etc/profile 

export JAVA_HOME=/usr/local/java
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=$JAVA_HOME/lib:$CLASSPATH

```



2.hadoop-2.7.7 버전 다운 및 압축풀기

```bash
[root@master ~]#  wget https://archive.apache.org/dist/hadoop/common/hadoop-2.7.7/hadoop-2.7.7.tar.gz

[root@master ~]# tar xvfz hadoop-2.7.7.tar.gz 
[root@master ~]# mv hadoop-2.7.7 ..
 
```



3.방화벽 해제 및   호스트 이름 master로 변경

```bash
[root@master ~]# systemctl stop firewalld
[root@master ~]# systemctl disable firewalld
[root@master ~]# hostnamectl set-hostname master
[root@master ~]# hostname

```



4.네트워크 설정 (m1~m4 모두 입력 !! )

HWADDR = m2~m4에서 MAC주소를 각각 새로 생성해서 입력해줘야함.

BOOTPROTO, NETMASK, GATEWAY, DNS1 추가!

IPADDR는 m1~m4까지 

192.168.111.120 , 192.168.111.130 , 192.168.111.140, 192.168.111.150 각각 입력!

```bash
[root@master ~]# cd /etc/sysconfig/network-scripts/
[root@master ~]# vi ifcfg-eno16777728

HWADDR="01:0C:29:27:5B:DB"
TYPE="Ethernet"
BOOTPROTO=none
IPADDR=192.168.111.120
NETMASK=255.255.255.0
GATEWAY=192.168.111.2
DNS1=192.168.111.2
DEFROUTE="yes"
PEERDNS="yes"
PEERROUTES="yes"
IPV4_FAILURE_FATAL="no"
IPV6INIT="yes"
IPV6_AUTOCONF="yes"
IPV6_DEFROUTE="yes"
IPV6_PEERDNS="yes"
IPV6_PEERROUTES="yes"
IPV6_FAILURE_FATAL="no"
NAME="eno16777728"
UUID="52a62176-9405-4228-b91f-ebadb5374c90"
ONBOOT="yes"


```



5.네트워크에 각 ip주소 네이밍하기!

vi /etc/hosts (맨아래에 추가해주기.)

입력다하면 source /etc/hosts로 적용!

적용후 ping slave1, ping slave2, ping slave3로 

네트워크 끼리 연결이 되어있는지 확인.

```bash
[root@master ~]# cd
[root@master ~]# vi /etc/hosts
#
192.168.111.120    master
192.168.111.130    slave1
192.168.111.140    slave2
192.168.111.150    slave3


```



6.SSH Key 생성 및 slave1(m2)~slave3(m4)에 동일하게 적용시키기

```bash
[root@master ~]# ssh-keygen-t rsa
[root@master ~]# ssh-copy-id -i/root/.ssh/id_rsa.pub root@slave1
[root@master ~]#ssh-copy-id -i/root/.ssh/id_rsa.pub root@slave2
[root@master ~]#ssh-copy-id -i/root/.ssh/id_rsa.pub root@slave3
[root@master ~]#ssh-copy-id -i/root/.ssh/id_rsa.pub root@maste


```



7.하둡 설정

```bash
[root@master ~]# cd
[root@master ~]# vi .bashrc
```

.bashrc 파일 맨 아래에 HADOOP_HOME 및 PATH 설정 해주기

```bash
# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
export HADOOP_HOME=/root/hadoop-2.7.7
export PATH=$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$PATH


```



8.master 수정 내용을 slave1~slave3에 전달 완료 후 HDFS 포맷 후 시작!

```bash
[root@master hadoop]#  vi hadoop-env.sh
[root@master hadoop]#  vi mapred-env.sh
[root@master hadoop]#  vi yarn-env.sh
[root@master hadoop]#  vi core-site.xml
[root@master hadoop]#  vi hdfs-site.xml 
[root@master hadoop]#  vi mapred-site.xml
[root@master hadoop]#  cp mapred-site.xml.template mapred-site.xml
[root@master hadoop]#  vi mapred-site.xml
[root@master hadoop]#  vi yarn-site.xml

[root@master hadoop]# scp mapred-env.sh root@slave1:/root/hadoop-2.7.7/etc/hadoop
[root@master hadoop]#  scp yarn-env.sh root@slave1:/root/hadoop-2.7.7/etc/hadoop
[root@master hadoop]# scp core-site.xml root@slave1:/root/hadoop-2.7.7/etc/hadoop
[root@master hadoop]#  vi hdfs-site.xml 
[root@master hadoop]# scp hdfs-site.xml root@slave1:/root/hadoop-2.7.7/etc/hadoop
[root@master hadoop]# cat slaves
[root@master hadoop]#  scp slaves root@slave1:/root/hadoop-2.7.7/etc/hadoop

[root@master hadoop]#  hdfs namenode -format
[root@master hadoop]# start-dfs.sh

```

