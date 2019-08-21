# 용어 정리

## HDFS

#### 1.NameNode

-HDFS의 마스터 노드에 해당한다. HDFS상에 보존되는 파일의 메타데이터와

보존된 파일의 분할된 조각(블록)이 어떤 DataNode에서 관리되는지 등의 정보 관리함.

#### 2.DataNode

-HDFS의 워커 노드를 말한다. HDFS상에 보존된 파일의 블록을 관리함.

```

```

## YARN

#### 1.ResourceManager

-클러스터 전체의 계산 리소스를 관리하고, 클라이언트가 요구한 리소스를 NodeManager로부터

확보하도록 스케줄링한다. 스파크에서의 ResourceManager는 요청된 executor의 개수와

CPU 코어의 수, 메모리 양에 따라 executor 하나 이상의 NodeManager로부터 확보하는 역할을 담당함.

#### 2.NodeManager

-클러스터 전체의 계산 리소스를 관리하는 ResourceManager와는 달리, 자신이 설최된 머신(노드)의

계산 리소스만을 관리한다.ResourceManager로부터 받은 요청에 따라, 필요한 계산 리소스를 확보한

'컨테이너'라는 에플리케이션의 실행 환경을 제공한다. 요청된 컨테이너의 개수에 따라서 

복수의 NodeManager로부터 컨테이너를 확보해 분산 처리한다.

cf.SPARK의 경우 executor가 NodeManager로부터 확보된 컨테이너상에서 작동하는 것이다.

```

```

## HDFS와 YARN의 환경 설정의 파일들

## [core-site.xml, hdfs-site.xml, yarn-site.xml] 설명

### 1.core-site.xml

```xml
<configuration>
	<property>
    	<name>fs.defaultFS</name>
        <value>hdfs://spark-master:8020</value>
    </property>
    <property>
    	<name>hadoop.tmp.dir</name>
        <value>/hadoop/tmp</value>
    </property>
</configuration>
```

##### -fs.defaultFS

​	이용할 분산 파일시스템을 지정한다. HDFS를 쓰기 때문에

​	hdfs://<NameNode의 URL>:<포트번호>와 같은 형식으로 값을 지정함.

##### -hadoop.tmp.dir

​	HDFS와 YARN에서 이용하는 임시 디렉토리를 지정한다.

```

```

### 2.hdfs-site.xml

```xml
<configuration>
	<property>
    	<name>dfs.namenode.name.dir</name>
        <value>file:///hadoop/hdfs/name</value>
    </property>
    <property>
    	<name>dfs.datanode.data.dir</name>
        <value>file:///hadoop/hdfs/data</value>
    </property>
</configuration>
```

##### -dfs.namenode.name.dir

​	NameNode가 HDFS상 파일의 메타데이터를 보존하는 디렉토리를 지정한다.

##### -dfs.datanode.data.dir

​	DataNode가 블록을 보존하는 디렉토리를 지정한다. 

​	블록의 복제를 3으로 했을경우( 즉 master - slave관계에서 slave의 수가 3개 일때)

​	모든 DataNode의 디렉토리 용량의 합을 3으로 나눈값이 

​	HDFS에 저장 가능한 데이터의 용량이 된다.

```

```

### 3.yarn-site.xml

```xml
<configuration>
	<property>
    	<name>yarn.resourcemanager.hostname</name>
        <value>spark-master</value>
    </property>
    <property>
    	<name>yarn.nodemanager.log-dirs</name>
        <value>file:///hadoop/yarn/node-manager/logs</value>
    </property>
      <property>
    	<name>yarn.nodemanager.local-dirs</name>
        <value>file:///hadoop/yarn/node-manager/local</value>
    </property>
</configuration>
```

##### -yarn.resourcemanager.hostname

​	ResourceManager가 동작하는 머신의 호스트명을 설정한다.

##### -yarn.nodemanager.log-dirs

​	컨테이너가 출력하는 로그의 디렉토리를 지정한다.

​	SPARK에서는 executor와 드라이버의 로그가 출력된다.

##### -yarn.nodemanager.local-dirs

​	NodeManager가 이용하는 로컬디스크의 경로를 지정한다.