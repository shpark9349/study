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
