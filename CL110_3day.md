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
                    
             provisioning 
    nova-compute   >     VM       <  glance
           | send image
        glance
    
    Project 내부
     object들로 == {meta data}
        object들과 meta data >> db에 저장 추가적인 meta data로 구성
    
    
    PaaS(vmware.rhv)  iso업로드후에설치 설정 프로비저닝(Os설치과정)
    IaaS(AWS,GCP,Tencent) : OS설치없고 이미지를 업체가 제공 프로비저닝없음
                   
    opensource standard image type

    - raw : 거의 100% 일반 디스크성능 기능이 거의없고 지연성이 낮음을 원하는 서버에 많이사용
    - qcow2** : qcow3통합  raw+qcow = qcow3  vmdk와 거의 동일한 기능 제공 qemu copy on write
    - qed : 이전에 xen에 사용 현재는 거의 사용안함

    support

    -vhd 
    
    
## keystone 관련
    policy.json 파일관련 
    admin 권한 이외 public / private / admin
    권한 부분확인요망 rc 부분 cli command 관련 
    # 확인
    echo $?
    
### flavor
    
    어떤 host에서 생성할지 자원이 괜찮은지 확인후 
    조건이 맞는 부분 할당 관련 추후 node가 많을시 설정하여 검색시간 단축
    nova서비스에서 flavor 관리 meta data
     
    spec vcpu,vmem,vdisk 
    
    nova 서비스에서 스케줄러 서비스 관리 
    /etc/nova/nova.conf 내용에 스케줄러 검색하면 확인가능
    내용중 default 관련 필터값을 보면 이해가능
    nova.conf over commit가능
    하이퍼스레드 core 추상적 core로 할당유의
    
    cat /etc/nova/nova.conf |grep -Ev "^#|^$" | sed -e "s/^\[/\n\[/g"
    
    ephemeral disk : 임시디스크이나 설정을 ssd외 다른경로로 지정가능
    DB는 1:1 vcpu할당권장
    meta 추가가능
    
    block device 부분에서 iops제어가능
    nic는 트래픽제어 아직불가 ( rx/tx 필터부분 )
    
    
    
