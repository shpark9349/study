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
#### download 이미지 확인
    qemu-img info
    
## network(metadata)
    dnsmask
        -dhcp,dns service
    namespace
        -Router,subnet 제공
    -- vm에 네트워크 할당은 meta
        네트워크 밑으로 subnet 여러개 가능 (PaaS와의 차이점)
        
        
#### 실습
    network create test1   기본적으로 
    subnet create 
    shared= admin만된다
    
    ip netns
    ip netns uid ink 
    virsh list
    virsh domiflist 


#### Nova instance 
    controller
    [root@allinone ~]# openstack-service status nova
    MainPID=1314 Id=openstack-nova-api.service ActiveState=active :REST API 처리 및 파일처리 (proxy)
    MainPID=1358 Id=openstack-nova-cert.service ActiveState=active :인증서 관리
    MainPID=1337 Id=openstack-nova-conductor.service ActiveState=active : B:nova -> DB N: nova-> conductor -> DB
    MainPID=1334 Id=openstack-nova-consoleauth.service ActiveState=active :VNC/SPICE Token인증
    MainPID=1325 Id=openstack-nova-novncproxy.service ActiveState=active :VNC HTML5버전(based JS)
    MainPID=1352 Id=openstack-nova-scheduler.service ActiveState=active : compute 서버사용량 정보를 일정시간 반복실행 정보수집갱신
        (설정가능 상화에 맞게 설정하면 수집하는 시간을 줄일수있음)
    
    
    compute(L/B, OVS)
    MainPID=2418 Id=openstack-nova-compute.service ActiveState=active : 하이퍼바이저 서비스,REST API/proxy/file handling
    
#### glance instance
    [root@allinone ~]# openstack-service status glance
    MainPID=1305 Id=openstack-glance-api.service ActiveState=active
    MainPID=1310 Id=openstack-glance-registry.service ActiveState=active
    
#### 트러블 슈팅포인트 nova log
    MainPID=1314 Id=openstack-nova-api.service ActiveState=active :REST API 처리 및 파일처리 (proxy)
        log: /var/log/nova/nova-api.log
    MainPID=1358 Id=openstack-nova-cert.service ActiveState=active :인증서 관리
        log:  /var/log/nova/nova-cert.log
    MainPID=1337 Id=openstack-nova-conductor.service ActiveState=active : B:nova -> DB N: nova-> conductor -> DB
        log: /var/log/nova/nova-conductor.log
    MainPID=1334 Id=openstack-nova-consoleauth.service ActiveState=active :VNC/SPICE Token인증
        log: /var/log/nova/nova-consoleauth.log
    MainPID=1325 Id=openstack-nova-novncproxy.service ActiveState=active :VNC HTML5버전(based JS)
        log: /var/log/nova/nova-novncproxy.log
    MainPID=1352 Id=openstack-nova-scheduler.service ActiveState=active : compute 서버사용량 정보를 일정시간 반복실행 정보수집갱신
        log: /var/log/nova/nova-scheduler.log
    정보메시지(nova-manage) : /var/log/nova/nova-manage.log
    MainPID=2418 Id=openstack-nova-compute.service ActiveState=active : 하이퍼바이저 서비스,REST API/proxy/file handling
        log: /var/log/nova/nova-compute.log
#### 트러블 슈팅 포인트 network
    host 네트워크정보확인
    ip addr show : 모든 실제 및 가상장치를 표시
    ovs-vsctl show : 가상스위치의 인터페이스와 브릿지를 표시
    ovs-dpctl show : 스위치의 데이터경로를 표시
    openstack network list : 인스턴스에 연결된 네트워크를 식별할수있음
    ip netns list :사용가능한 네트워크 네임스페이스 나열
    
    ip netns exec : 연결테스트에 용의
        ex)ip netns exec qdhcp-xxxx-xx ping -c 3 192.168.0.7
    ip netns exec : 네트워크구성확인
        ex)ip netns exec qdhcp-xxxx-xx ip addr show
            ovs-vsctl show 다시확인
    ip netns qdhcp-xxxx-xx nc 192.168.0.7 22 
