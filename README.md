# Bluepill Example
Bluepill is a simple process monitoring tool written in Ruby. See [http://github.com/arya/bluepill](http://github.com/arya/bluepill)

The pill file in this repo is an example of using it to start multiple worker processes running the same script.

## Starting the processes
Under rvm, as a user other than root, you can load up the workers using:

    rvmsudo bluepill load bluepill_workers.pill
    

Make sure that the user you specify in the pill has write permissions on the pid_file directory you specified.

You might also find some help here:

[https://github.com/spagalloco/bluepill-examples](https://github.com/spagalloco/bluepill-examples)