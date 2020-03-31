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

