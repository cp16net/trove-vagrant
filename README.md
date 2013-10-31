trove-vagrant
=============

Vagrant file for getting started with Trove

=======
You have a few options for what provider you would like to use with vagrant with this Vagrantfile.

VirtualBox
VMWare Fusion
libvirt
QEMU/KVM

To get things started with vmware_fusion:

    vagrant plugin install vmware_fusion
    vagrant up --provider=vmware_fusion
    vagrant ssh
    ./redstack install
    ./redstack kick-start mysql
    ./fix-iptables.sh
    ./redstack int-tests --group=blackbox

To get things started with libvirt:

    vagrant up --provider=libvirt
    vagrant ssh
    ./redstack install
    ./redstack kick-start mysql
    ./fix-iptables.sh
    ./redstack int-tests --group=blackbox

There are optional environment variables the Vagrantfile looks for:

    TROVE_VM_SOURCE_DIR
        The directory on the host that will be shared with the VM.
        If it's not specified, the directory above this directory (`./../') is used.
&nbsp;

    TROVE_VM_SYNC_DIR
        The directory on the VM that the above directory will be available at.
        If it's not specified, `/vagrant` is used.


    VAGRANT_DEFAULT_PROVIDER
        This is the default provider that will be used so that you do not have to
        retype --provider each time you create a virtual environment.

