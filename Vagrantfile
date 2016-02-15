# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "rasmus/php7dev"

  config.vm.synced_folder "/home/grkr/build/nwrfcsdk_x86_64", "/nwrfcsdk"

  config.vm.provision "shell", inline: <<-SHELL
     makephp 71 zts
     newphp 71 debugzts
     echo "/nwrfcsdk/lib" > /etc/ld.so.conf.d/nwrfcsdk.conf
     ldconfig
     sed -i "s/extension=memcached.so/;extension=memcached.so/" /etc/php71/php-cli.ini
     sed -i "s/extension=raphf.so/;extension=raphf.so/" /etc/php71/php-cli.ini
     sed -i "s/extension=propro.so/;extension=propro.so/" /etc/php71/php-cli.ini
     sed -i "s/extension=http.so/;extension=http.so/" /etc/php71/php-cli.ini
  SHELL
end
