### [ Hadoop ] Linux에 [ CentOS 7 ] 하둡 설치하기 

#### 2.VMware 설치 및 VM 옵션 설정



9.VMware Workstation 12Player을 실행후, linuxM을 클릭후

Edit virtual machine settings를 클릭해서 VM옵션 수정을한다.



10.원활한 작업 속도를 위해 Memory를 4GB로 설정.



11.Hard Disk(SCSI)삭제 후, 새로운 하드디스크를 생성.

(디스크 타입 = SCSI  , Create a new virtual disk 로 설정)

(최대 사이즈 = 80GB , Store virtuldisk as a single file로 설정)

cf. SCSI = 서버나 워크스테이션 등에 쓰이는 고속 인터페이스다.



12. Specify Disk File에서

File name : linuxM-0.vmdk로 설정 

(추후에 ISO 디스크 이미지 파일을 VM에 직접 넣어줄 예정.)

cf. VMDK= Virtual Machine Disk 의 약자로 VMware 또는 VirtualBox 와 같은 가상 시스템에서 사용할 가상 하드 디스크 드라이브의 컨테이너를 설명하는 파일 형식.

cf. 가상 이미지 제공 사이트인 [osboxes.org](https://osboxes.org/) 사이트에서 원하는 파일을 받으면VMDK 이미지 파일을 확인 할 수있다.



----------------------12번까지 일단 linuxM셋팅 완료됨 완료후, 일단 VM끄기-------------------------



