  !! NIC 0 br-ex
  !! NIC 1 br-tun

   # cat <<EOF> /etc/modprobe.d/kvm.conf
   > options kvm_intel nested=Y
   EOF
   # modprobe -r kvm_intel
   # modprobe -r kvm
   # modprobe kvm_intel
   # cat /sys/module/kvm_intel/parameters/nested 
     Y
   # yum install virt-install libguestfs-xfs libguestfs-tools-c
   # virsh net list 
   -> default
   # virt-builder --root-password password:redhat --size 6G --format qcow -o /var/lib/libvirt/images/allinone.qcow2 centos-7.7
    
   # virt-install --name allinone --vcpu 4 --cpu host-passthrough --memory 16384 --disk /var/lib/libvirt/images/allinone.qcow2,bus=virtio --network default --graphical spice --noautoconsole --import
       control,compute1,compute2 
   # virsh list 
   # virsh domifaddr <ID>
   # virsh console <ID>

   # virsh destroy <ID>
   # virsh undefine <NAME>
   # virt-sysprep -a centos7.qcow2 -> control, compute1, compute2
   
   # for i in control compute1 compute2 ; do virt-install --name $i --vcpu 4 --cpu host-passthrough --memory 16384 --disk /var/lib/libvirt/images/$i.qcow2,bus=virtio --network default --graphic spice --noautoconsole --import ; done
   
   # virsh console ## escape ctrl+]
   hostname
   network config static 
   # vi /root/internal.xml
<network>
  <name>internal</name>
  <uuid>531a7a88-bef2-4922-ba5b-b64304ff11d9</uuid>
  <bridge name='virbr2' stp='on' delay='0'/>
  <mac address='52:54:00:e2:8c:30'/>
  <domain name='internal'/>
  <ip address='192.168.10.1' netmask='255.255.255.0'>
  </ip>
</network>
   # virsh net-define /root/internal.xml
   # virsh net-start /root/internal.xml
   # virsh net-autostart internal 
   
   
   # for i in control compute1 compute2 ; do virt-install --name $i --vcpu 4 --cpu host-passthrough --memory 16384 --disk /var/lib/libvirt/images/$i.qcow2,bus=virtio --network default --network internal  --graphic spice --noautoconsole --import ; done
   
   # virsh console <control, compute1,2>
   # yum install epel-release
   # yum search centos-release-openstack
   # yum install centos-release-openstack-queens
   # yum install openstack-packstack 
   # packstack --gen-answer-file=/root/answers.txt
   
   # packstack --answer-file /root/answers.txt
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
