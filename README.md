# Vagrant based IPv6 Gateway

This gateway uses Hurrican Electric's IPv6 TunnelBroker.net service to establish a routed IPv6 /64 subnet to your network.

To use this on YOUR network, configure the following:

1. [Vagrantfile](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/Vagrantfile)
    1. [Line 8](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/Vagrantfile#L8) to define the local IP of your host
    1. [Line 15](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/Vagrantfile#L15) to define the IPv4 gateway address on your LAN
1. [site.yml](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml)
    1. [Line 19](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L19) to define the HE endpoint address to use for your tunnel
    1. [Line 20](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L20) to define the local network endpoint address to use for your tunnel
    1. [Line 22](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L22) to define the tunnel IPv6 address prefix
    1. [Lines 33-39](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L33-L39) to enable IPv4 DHCP and DHCPv6
    1. [Lines 41-45](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L41-L45) to define the local IPv4 network addressing and gateway
    1. [Line 50](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L50) to define the IPv6 routed network (from TunnelBroker.net)
    1. [Lines 215-224](https://github.com/JonTheNiceGuy/vagrant_ipv6gateway/blob/master/site.yml#L215-L224) to define your FIREWALL policy. Note this is not applied fresh each time, it's additive, so if you add something on the end, it's probably going to go after the Deny rule.
1. authorized_keys to define your personal SSH keys... or just leave this blank, and always use "vagrant ssh" to get into the appliance.

This is just a "toy" project for my home network - it's certainly no replacement for "proper" IPv6 from your ISP, but it works for me, and it got me on IPv6.
