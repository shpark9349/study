## cinder 환경 고민
  ceph
  gluster
  
  
  openstack manila 공유시스템
  
  NFSv4
  
  linux d-bus
  
  관리데몬
  stratisd
  
  
  lvs  볼륨확인
  vgs 스토리지
  
  lsblk
  
  임시 & 스왑
    - _base에서 생성후 각 가상머신 UUID에 backing 파일로 구성
    - 절대 고정데이터는 저장하면 안됨 (DB)
    - cloudinit가 관리 데이터파일도 역시 이것을 통해 전달가능
    오픈스택 개념상 머신은 삭제

  cloudinit 
  
  ksm 데몬
  리소스 체크
  인터벌 고려 해당 동작시 오버헤드 최초구성시 결정 base이미지관련
  
  targetcli
  
  data export 
  볼륨을 이미지화 시킨후 save raw 마운트이후 데이터 저장
