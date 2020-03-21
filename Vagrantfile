###################### Vagrantfile #################################
#
# This is a simple Vagrantfile that automates the provisioning of
# VMs and services based on a generic/ubuntu1804 box
#
####################################################################

###### Set required versions ######
Vagrant.require_version ">= 2.0.0"
require 'yaml'
settings = YAML.load_file 'vagrant.yml'

####### Bring up base box #########
Vagrant.configure("2") do |config|

    ####### VM 1 Setup ########
    config.vm.define "basevm1" do |basevm1|

        basevm1.vm.box = "generic/ubuntu1804"
        basevm1.vm.hostname =  settings['basevm1_name']
        basevm1.vm.network :private_network, ip: settings['basevm1ip_address']

        config.vm.provider "virtualbox" do |basevm1|
            # basevm1.gui = true
            basevm1.name = settings['basevm1_name']
            basevm1.customize ["modifyvm", :id, \
             "--memory", settings['basevm1_memory'], \
             "--cpus", settings['basevm1_cpu'], \
             "--cpuexecutioncap", "100"]
          end

        # Uncomment below code for ansible support
        # basevm1.vm.provision "ansible_local" do |ansible|
        #     ansible.verbose = true
        #     ansible.playbook = "provision/playbook.yml"
        #     ansible.limit = "basevm1"
        # end

    end
end

