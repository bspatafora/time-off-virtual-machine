# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
  end

  config.vm.network "forwarded_port", guest: 3000, host: 3001

  root_commands = <<-END
    apt-get update

    # Install postgres, create vagrant user
    apt-get install libpq-dev -y
    apt-get install postgresql postgresql-contrib -y
    sudo -u postgres createuser --createdb vagrant

    sudo apt-get install git -y

    sudo apt-get install nodejs -y
  END

  vagrant_user_commands = <<-END
    # Install rbenv, ruby-build, and Ruby 2.1.4
    git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
    echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
    source ~/.bash_profile
    git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
    rbenv install 2.1.4 && rbenv global 2.1.4

    git clone https://github.com/bspatafora/time_off
    cd time_off
    gem install bundler
    bundle install

    rake db:create db:migrate
    rspec
  END

  config.vm.provision "shell", inline: root_commands
  config.vm.provision "shell", inline: vagrant_user_commands, privileged: false
end
