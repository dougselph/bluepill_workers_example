# Bluepill Example
Bluepill is a simple process monitoring tool written in Ruby. See [http://github.com/arya/bluepill](http://github.com/arya/bluepill)

The pill file in this repo is an example of using it to start multiple worker processes running the same script.

	Bluepill.application("my_app") do |app|
		5.times do |i|
			app.process("my_worker_#{i}") do |process|
				process.group = "workers"
				process.working_dir = "/my/working/directory"
				process.start_command = "/my/working/directory/worker_script.rb"
				process.pid_file = "/var/run/bluepill/worker_script_#{i}.pid"
				process.daemonize = true
				process.uid = "someuser"
				process.gid = "somegroup"
				process.start_grace_time = 3.seconds
				process.stop_grace_time = 7.seconds
				process.restart_grace_time = 10.seconds
			end
		end
	end

## Starting the processes
Under rvm, as a user other than root, you can load up the workers using:

    rvmsudo bluepill load bluepill_workers.pill
    

Make sure that the user you specify in the pill has write permissions on the pid_file directory you specified.

You might also find some help here:

[https://github.com/spagalloco/bluepill-examples](https://github.com/spagalloco/bluepill-examples)