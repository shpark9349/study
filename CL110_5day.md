## node add
  redhat = director
  1. packstack 데모
  2. 수동  
  3. ansible 권장
  
  undercloud > nic5 개발여건 상용서비스와는 소수 가능
  
  overcloud > 상용
  
  upstream:
  Triple-o 
  https://docs.openstack.org/tripleo-quickstart/latest/getting-started.html
  
  
  
#### install 
  packstack :puppet module
  director(Triple-o) :yml.yaml 기반 ansible
  
  install
  openstack ansible + satellite(foreman/katello)
  
  negix 네트워크 LB 및 L4 Vip
  big data 사하라 API 활용 메모리 할당 과점유 별도 node 권장
  물리적인 데이터속도 SSD DAS 권장 10G이상  70%
  
  

#### stacks


#### Ceilometer
  Mongodb 테스트 용도이며 관련 제공자가 자체적으로 수집
  딜레이가 느려서 
  dom
  livertd를 관리하고 모니터하는 대체 고민


 rhel7 ~ 8 메이저 버젼 변경으로
 yum  + dnf
 iptables -> nftables
 
## repo 추후 메이저 3년 지나면 불가
** satellite 기반 repo관리 ( 찾아보자 )
* 수동 repo서버 구성 관리 (재구성확인)


lsmod | grep vxlan
로 사용되어지는 메모리와 모듈확인

ip link |grep vxlan

network작업정보조회
openvswitch log 
  openvswitch/conf.db 파일조회


  분산스위치(vmware와 동일한 스위치기능) 
  DVR 
ㄴ
