ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'
 
Vagrant.configure("2") do |config|
 
	config.vm.define "docker-4-unix-on-windows" do |m|	 
		m.vm.provision :shell, inline: "sudo apt-get update"

		m.vm.provider "docker" do |d|
			d.name = 'docker-4-unix-on-windows'
			
			d.force_host_vm = true
			d.has_ssh = true

			#this will look for a Dockerfile in the same directory as the Vagrantfile. 
			#When vagrant up --provider=docker is run, Vagrant automatically builds that Dockerfile and starts a container based on that Dockerfile
			
			d.build_dir = "." 
			d.cmd = ["ping", "-c 5151", "127.0.0.1"]
			d.remains_running = true
			
			d.vagrant_machine = "dockerhostvm"
			d.vagrant_vagrantfile = "./DockerHostVagrantfile"
		end
	end
end