### [ Hadoop ] Linux에 [ CentOS 7 ] 하둡 설치하기 

#### 3.VMware Network 설정



13.cmd-ipconfig 에서

이더넷 어뎁터 VMware Network Adapter VMnet8:

IPv4주소 ----------:192.168.63.1

서브넷마스크 ----:255.255.255.0 인지 확인할것



cf.IP 특징 : IP는 사실 32자리로 이루어진 2진수, IP는 네트워크 영역과 호스트 					IP로 구성됨, 동일한 네트워크 내에서 호스트 IP는 각자 달라야 함.

cf.서브넷마스크 특징 :하나의 IP에서 사용자가 필요한 IP만쓰게, 네트워크 영역과 호스트 영역을 나눠준다. 기본 서브넷 네트워크도 물론 네트워크 영역과 호스트 영역을 나눠주기 때문에 서브넷 마스크라고도 불림.



14.네트워크 변경을 위해서 vmnetcfg.exe를 

C:\Program Files (x86)\VMware\VMware Player에 가져다 놓고 실행한다.



15.vmnetcfg.exe를 실행후 , VMnet8을 클릭후 맨 아래창에

Subnet IP : 192.168.111.0(실습용)

Subnet mask : 255.255.255.0 으로 변경한다.

-------------------------------네트워크 설정 끝 -----------------------------------------------



16.VMware Workstation에서 linuxM에 디스크 탭에

CentOS-7.0-1406-x86_64-DVD.ISO 이미지 파일을 넣는다.