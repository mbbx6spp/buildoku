require 'rubygems'
require 'yaml'

def load_app_config!
  cfg_file = File.join(File.dirname(__FILE__), 'apps.yml')
  $APPS = YAML.load(File.read(cfg_file))
end

load_app_config!

Vagrant::Config.run do |config|
  config.ssh.username = "heroku"
  config.ssh.max_tries = 25
  $APPS.each do |key, app|
    config.vm.share_folder(app['name'], "/var/#{app['name']}",
      app['host_path'], :auto => true)
  end

  config.vm.define :builder do |srv|
    srv.vm.box = "heroku-builder"
    srv.vm.host_name = "builder.heroku.local"
    srv.vm.customize do |vm|
      vm.name = "Heroku Builder VM"
      vm.memory_size = 512 # enough RAM for building your native app
    end
    srv.vm.network "33.33.33.11"
    srv.vm.forward_port "ssh", 22, 22022
  end
end
