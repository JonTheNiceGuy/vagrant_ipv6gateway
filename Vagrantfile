Vagrant.configure("2") do |config|
  config.vm.define "ipv6gateway" do |ipv6gateway|
    ipv6gateway.vm.box = "ubuntu/bionic64"
    ipv6gateway.vm.hostname = "ipv6gateway"
    ipv6gateway.vm.box_check_update = false
    ipv6gateway.vm.boot_timeout = 65535

    ipv6gateway.vm.network "public_network", bridge: "enp0s25", ip: "192.168.1.253", :use_dhcp_assigned_default_route => false

    ipv6gateway.vm.provider "virtualbox" do |vb|
      vb.name = "ipv6gateway"
    end

    ipv6gateway.vm.provision "shell", run: "always", inline: <<-SHELL
      ip route | grep default | grep 192.168.1.254 >/dev/null || ip route add default via 192.168.1.254
      ip route | grep default | grep 10.0.2.2 && ip route del default via 10.0.2.2 || true
    SHELL

    ipv6gateway.vm.provision "ansible_local", run: "always" do |ansible|
      ansible.playbook = "site.yml"
      ansible.install_mode = :pip
    end
  end
end
