**[ Hadoop HDFS** **명령어 ]**

**https://hadoop.apache.org/docs/r2.7.7/hadoop-project-dist/hadoop-common/FileSystemShell.html**<--문서를 참고함.



hdfs dfs -ls /[디렉토리명 또는 파일명]

지정된 디렉토리의 파일리스트 또는 지정된 파일의 정보를 보여준다.

 

hdfs dfs -lsr /[디렉토리명]

지정된 디렉토리의 파일리스트 및 서브디렉토리들의 파일 리스트도 보여준다.

 

hdfs dfs -mkdir /디렉토리명

지정된 디렉토리를 생성한다.

 

hdfs dfs -cat /[디렉토리/]파일

지정된 파일의 내용을 화면에 출력한다.

 

hdfs dfs -put 사용자계정로컬파일 HDFS디렉터리[/파일]

지정된 사용자계정 로컬 파일시스템의 파일을 HDFS 상 디렉터리의 파일로 복사한다.

 

hdfs dfs -get HDFS디렉터리의파일  사용자계정로컬 디렉터리[/파일]

지정된 HDFS상의 파일을 사용자계정 로컬 파일시스템의 디렉터리나 파일로 복사한다.

 

hdfs dfs -rm /[디렉토리]/파일

지정된 파일을 삭제한다.

 

hdfs dfs -rmr /디렉토리

지정된 디렉터리를 삭제. 비어 있지않은 디렉터리도 삭제하며 서브 디렉토리도 삭제한다.

 

hdfs dfs -tail /[디렉토리]/파일

지정된 파일의 마지막 1kb 내용을 화면에 출력한다.

 

hdfs dfs –chmod 사용자허가모드 /[디렉토리명 또는 파일명]

지정된 디렉토리 또는 파일의 사용자 허가 모드를 변경한다.

 

hdfs dfs -mv /[디렉토리]/old파일 /[디렉토리]/new파일

지정된 디렉토리의 파일을 다른 이름으로 변경하거나 다른 폴더로 이동한다.



