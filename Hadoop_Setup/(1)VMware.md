### [ Hadoop ] Linux에 [ CentOS 7 ] 하둡 설치하기 

#### 1.VMware 설치 및 VM 옵션 설정



1.VMware 설치를 위해 https://www.vmware.com/kr.html 에서 

VMware를 설치한다.



2.VMware 작업을 위한 하위 디렉토리들을 만들어 놓는다

(Ex. C:/CentOS/ 에서 linuxM, m1,m2,m3,m4)



3.Vmware 실행 후 , Create a New Virtual Machine 클릭



4.Operating System을 어떻게 설치할거냐는 옵션에

I will install the operating system later. 선택

(추후에 ISO 디스크 이미지 파일을 VM에 직접 넣어줄 예정.)



5.어떤 Operating System을 설치할거냐는 옵션에

(operating system - Linux) (Version - CentOS 64-bit로 설정.)



6.Virtul machine 이름은 ,2번에서 사전에 만든 linuxM(초기 설정을 위한 파일)으로 지정.

(Location 또한 이름과 동일하게 C:\CentOS\linuxM으로 설정한다. )



7.Specify Disk Capacity 

Store virtual disk as a single file :
특징 : 파티션을 나누건않고, 하나의 파일에 다 저장하겠다.
		   즉 가상디스크의 파일을 단일파일로 생성한다는것이다.
(호스트PC의 하드디스크가 NTFS일때 선택)

단점: 파일 하나의 최대 크기가 증가 50GB까지 증가해서 
대용량 파일 복사시, 문제가 발생 할 수 있음.



 Split virtual disk into multiple files :
특징 : 가상디스크 파일을 2GB단위로 끊어서 생성한다. 
		   즉 가상의 디스크가 여러개 생긴것 처럼 해준다.
단점 : 성능측면에서 multiple보다는 single 이 더 좋다.
(호스트PC의 하드디스크가 FAT32일때 선택)



8.VM 완성.