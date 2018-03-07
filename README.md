# vagrant-files
Some customized Vagrantfile's


* TODO: Find a way to automatically adjust the RAM for the VM using the available physical RAM at the host
  * Some relevant discussion here: https://stackoverflow.com/questions/33209305/vagrant-how-to-detect-windows-host-ram-and-cpu
  * Automatically adjust vCPUs based on  physical cores  
    - A bash snippet that outpus the physical cores # (adapted from [here](https://access.redhat.com/discussions/480953)):
    - Also limiting the result to a [reasonable amount](https://blogs.vmware.com/vsphere/2013/02/the-performance-cost-of-smp-the-reason-for-rightsizing.html) of vCPUs of 4:
  ```bash
  physical_cores=$(egrep -e "core id" -e ^physical /proc/cpuinfo|xargs -l2 echo|sort -u|wc -l)
  vcpus=$(( $physical_cores > 4 ? 4 : $physical_cores ))
  ```
