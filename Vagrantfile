# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Dotenv.load

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "japboy/CentOS-7.0-1406-x86_64-Minimal"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "./public", "/vagrant"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  #
  # View the documentation for the provider you're using for more
  # information on available options.
  #
  # Amazon Web Services
  # https://github.com/mitchellh/vagrant-aws#configuration
  #
  config.vm.provider :aws do |provider, override|
    provider.access_key_id = ENV['AWS_ACCESS_KEY']
    provider.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    provider.use_iam_profile = true

    provider.ami = "ami-29dc9228"
    provider.instance_type = "t2.micro"
    provider.keypair_name = ENV['AWS_KEYPAIR_NAME']
    provider.region = "ap-northeast-1"

    provider.security_groups = [
      "default"
    ]
    provider.tags = {
      "Name" => "Testing"
    }

    override.vm.box = "aws"
    override.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"

    override.ssh.pty = true
    override.ssh.username = "ec2-user"
    override.ssh.private_key_path = ENV['AWS_PRIVATE_KEY_PATH']
  end

  # Google Compute Engine
  # https://github.com/mitchellh/vagrant-google#configuration
  #
  config.vm.provider :google do |provider, override|
    provider.google_project_id = ENV['GCE_PROJECT_ID']
    provider.google_client_email = ENV['GCE_CLIENT_EMAIL']
    provider.google_key_location = ENV['GCE_KEY_LOCATION']

    provider.image = "centos-6-v20140619"
    provider.machine_type = "f1-micro"

    provider.name = "my-instance"
    provider.network = "vagrant"

    override.vm.box = "gce"
    override.vm.box_url = "https://github.com/mitchellh/vagrant-google/raw/master/google.box"

    override.ssh.username = ENV['USERNAME']
    override.ssh.private_key_path = ENV['GCE_PRIVATE_KEY_PATH']
  end

  # DigitalOcean
  # https://github.com/smdahlen/vagrant-digitalocean#configure
  #
  config.vm.provider :digital_ocean do |provider, override|
    provider.token = ENV['DO_TOKEN']
    provider.image = "CentOS 7.0 x64"
    provider.size = "512mb"
    provider.ssh_key_name = ENV['DO_SSH_KEY_NAME']
    provider.region = "sfo1"

    override.vm.box = "digitalocean"
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"

    override.ssh.pty = true
    override.ssh.username = ENV['USERNAME']
    override.ssh.private_key_path = ENV['DO_PRIVATE_KEY_PATH']
  end

  # Physical server
  # https://github.com/tknerr/vagrant-managed-servers#configuration
  #
  config.vm.provider :managed do |provider, override|
    provider.server = ENV['HOSTNAME']

    override.vm.box = "managed"
    override.vm.box_url = "https://github.com/tknerr/vagrant-managed-servers/raw/master/dummy.box"

    override.ssh.username = ENV['USERNAME']
    #override.ssh.password = ENV['PASSWORD']
    override.ssh.private_key_path = ENV['PRIVATE_KEY_PATH']
  end

  # Enable provisioning with ansible, specifying a playbook path. Ansible's
  # inventory file will be created automatically when `vagrant up`, and it
  # will be loaded automatically from:
  # `.vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory`
  #
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./provision/site.yml"
    ansible.extra_vars = {
      user: ENV['USERNAME'],
    }
  end
end
