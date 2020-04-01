## 내용
    image + instance + network
    |
    qemu-img 도구에서 지원 디스크 생성&관리


Glance : file system backend => /var/lib/glance
  $ openstack image list
                    show
                    set
                    delete
                    create : 이미지생성이 아님 이미지를 업로드함으로
                    
              send image
        VM       <  glance
                    
PaaS(vmware.rhv)  iso업로드후에설치 설정 프로비저닝(Os설치과정)
IaaS(AWS,GCP,Tencent) : OS설치없고 이미지를 업체가 제공 프로비저닝없음
                   
opensource standard image type

- raw : 거의 100% 일반 디스크성능 기능이 거의없고 지연성이 낮음을 원하는 서버에 많이사용
- qcow2** : qcow3통합  raw+qcow = qcow3  vmdk와 거의 동일한 기능 제공 qemu copy on write
- qed : 이전에 xen에 사용 현재는 거의 사용안함

support

-vhd 
