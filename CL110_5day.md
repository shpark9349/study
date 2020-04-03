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
  
#### 

 rhel7 ~ 8 메이저 버젼 변경으로
 yum  + dnf
 iptables -> nftables
 
## repo 추후 메이저 3년 지나면 불가
** satellite 기반 repo관리 ( 찾아보자 )
* 수동 repo서버 구성 관리 (재구성확인)

 
