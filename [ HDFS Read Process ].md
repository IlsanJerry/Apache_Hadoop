## **[ HDFS Read Process ]**



![HdfsImage](C:\Users\student\Desktop\Apache_Hadoop\assets\HdfsImage.jpg)------------------------- HDFS Read Process------------------------------

(1) 클라이언트는 FileSystem(DistributedFileSystem) 객체의 'open ()' 메소드를 호출하여 읽

기 요청을 시작한다. 

 

(2) FileSystem(DistributedFileSystem) 객체는 RPC를 사용하여 NameNode에 연결하고 파일 블

록의 위치 정보를 담고 있는 메타 데이터 정보를 가져온다. 

 

(3) 이 메타 데이터에는 읽고자 하는 파일의 블록에 대한 사본이 저장되너 있는 DataNode 의 주소가 담겨져 있다.

 

(4, 5) DataNode의 주소를 받으면 FSDataInputStream 유형의 객체가 클라이언트에 리턴된다.

FSDataInputStream 객체는 DFSInputStream 을 포함하고 있으며 읽기 관련 메서드가 호

출되면 가장 우선순위가 높은 데이터 노드에서 해당 블록 읽게 된다.

 

(6) 블록의 끝 부분에 도달하면 DFSInputStream은 연결을 닫고 다음 블록의 다음 DataNode를 

찾는다.

 

(7) 클라이언트가 읽기를 완료 하면 close() 메소드를 호출한다 .****