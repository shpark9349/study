#### 교육2일차

    public  ->> 서비스 지속적 추가
    |
    private  ->> 변동이 거의 없음
    |
    (qemu/kvm,xen,Vmware,혼용)
    AWS,GCP

    (openstack)
    Tencent, ali

    private
    공통적인 요구사항:
    미터링 모니터링 확장/축소 서비스구축


    (이미 사양이 정해짐)사용자가 결정
    IaaS :openstack,aws,gcp
    ((SDN or NFV 네트워크기본))
    ((object 기본))
     |  
    flavor
     |
    PaaS :RHV, vmware, xen   _시스템관리자가 결정
    ((compute 기본))
  

    SaaS
    ((container
  
    1H/W - 2accelcator - 3kerel - 4h/v(kvm) - 5qemu - 6virtual/device - 7vm(libvirt) - 8os - 9app
    vtd,vtx(flags)12
    hypervisor function34
    virtual function56
    (RING0-3)1~9
  
    syscall,libcall VMcall hosctcall과 별개 

    1H/W - 2kernel -(liblibc) 3runc(container) - 4runtime - 5container
    images app+lib4
    (3-5) call share


#### openstack as a service
    XaaS
    OaaS


## openstack core API
    Nova
    Neutron
    Keystone
    Cinder
    Glance

    source code 변경관련 dev

## 링구조 설명(intel)
    동작예시1)
    HW(cpu)flag-kvm(driverzone과 userzone)-qemu-vcpu-vm
                        -vmem-vm
                        -vnic..
    동작예시2)
    OS단에서 처리2
    kvm과 같은 역활의 분배 
       --runc--
    HW -cgroup     - CRI-O -container - app
       -namespace
       -seliux
    
    0 = H/W
    원형 0~1 < 가장안쪽
    driver zone - kernel space
    ||
    
    kvm (intel, amd)
    
    ||
    원형 2~3
    user zone - user space

## 리눅스 드라이버
    virtio 반가상화 가속기능
    전가상화 
    vmware의 tools 설치 이후 가속

## Kolla

## TripleO

## Ansible install

## 실습 명령어
    [root@allinone ~]# rpm -qa |grep horizon
    puppet-horizon-9.5.0-1.el7ost.noarch
    python-django-horizon-10.0.2-1.el7ost.noarch
    
    [root@allinone ~]# cd /etc/httpd/conf.d/
    [root@allinone conf.d]# ls
    10-aodh_wsgi.conf            10-keystone_wsgi_main.conf  15-horizon_vhost.conf
    10-gnocchi_wsgi.conf         15-default.conf             openstack-dashboard.conf
    10-keystone_wsgi_admin.conf  15-horizon_ssl_vhost.conf
    
### 설명
    user
    |
    httpd
    |
    horizon 대시보드
    |
    인증 API 요청
    |
    keystone SSO API endpoint**
    |
    endlpoint(internal,public,admin)
    |
    neutron networking,SDN**                              ##  VM  ##
        (linuxbridge,iptables->nftables대체_7->8)
    cinder Block storage*                                ##  VM  ##
        (LVM2,iSCSI) 영구적인 데이터 확보위함
    nova compute instance(vm)**                            ##  VM  ##
        (qemu/kvm,libvirtd)
    glance image,cinder or vm snap save,import/export**   ##  VM  ##
        (impoer/export data를 넣고 뺄수있다)
    heat?(n+c+n+g를 오토메이션관리)internal
    ceilometer?계산 얼마나 사용하고있는지
    swift?object storage  (latancy 길다)
    
## 명령어
    yum install openstack-utils
    openstack-service status
    openstack-status
    서비스의 상태를 확인
    rc 사용전과 후의 권한 확인할수 있음
    위의명령어 sourc rc 사용전과 후의 차이
    
