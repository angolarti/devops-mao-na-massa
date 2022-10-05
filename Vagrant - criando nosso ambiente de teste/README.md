# Vagrant

## install

```bash
sudo pacman -S linux515-virtualbox-host-modules
sudo /sbin/rcvboxdrv
```

```bash
vagrant plugin uninstall vagrant-vbguest
vagrant plugin install vagrant-vbguest --plugin-version 0.21
vagrant plugin update
```

```ruby
Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.vm.box = "ubuntu18.04.6"
  config.vm.define "core" do |core|
    core.vm.network "public_network", ip: "192.168.1.216", bridge: "en0: Wi-Fi (Wireless)"
    # config.vm.network 'public_network', dev: 'wlp3s0', mode: 'bridge'
    config.ssh.dsa_authentication
    config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"
    config.vm.provision "shell", inline: <<-SHELL
      cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
end
```

Vagrant KVM and with the libvirt plugin:

```bash
vagrant plugin install vagrant-libvirt
```
