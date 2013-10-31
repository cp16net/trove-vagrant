Vagrant.configure("2") do |config|

  SOURCE_DIR = "../"
  if ENV['TROVE_VM_SOURCE_DIR']
    SOURCE_DIR = ENV['TROVE_VM_SOURCE_DIR']
  end

  SYNC_DIR = "/trove"
  if ENV['TROVE_VM_SYNC_DIR']
    SYNC_DIR = ENV['TROVE_VM_SYNC_DIR']
  end

  config.vm.synced_folder SOURCE_DIR, SYNC_DIR
  config.vm.provision :shell, :path => "install-trove.sh", :args => SYNC_DIR

  # support for vmware_fusion
  config.vm.provider :vmware_fusion do |vmf, override|
    config.vm.box = "openstack-trove"
    config.vm.box_url = "http://9e1a2926d405d51127ce-1dd7910aaf75de5d703b77f114f87ea9.r5.cf1.rackcdn.com/openstack-trove.box"
    vmf.gui = "TRUE"
    vmf.vmx["memsize"] = 3072

  end

  # support for virtualbox
  config.vm.provider :virtualbox do |vb, override|
    override.vm.box = "precise64"
    override.vm.box_url = "http://files.vagrantup.com/precise64.box"
    vb.customize ["modifyvm", :id, "--memory", "3072"]
  end

# support for libvirt
  config.vm.provider :libvirt do |libvirt, override|
    libvirt.driver = "qemu"
    libvirt.host = "127.0.0.1"
    libvirt.connect_via_ssh = true
    libvirt.memory = 3072
    libvirt.cpus = 2
    override.vm.box = "precise64"
    # override.vm.box_url = "http://files.vagrantup.com/precise64.box"
    # have to manually create a box since package a box does not work for libvirt
    override.vm.synced_folder SOURCE_DIR, SYNC_DIR, :nfs => true
  end

end
# vim: set ft=ruby:
