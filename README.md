
# To build TVM in Pynq :



## First Test the VTA Simulator working in the TVM package :


#### The VTA simulator library is built by default with TVM. 

We have to add the VTA library to our python path to run the VTA examples. The path can look like this :
If 'tvm' is in home directory :
*home/user/tvm/vta/python/vta/*

Some points to be careful with while using:

* path to a python library would have files such as 

    '___init___.py' 
    
    *graph.py*
    
    *rpc_client.py*

in this case.

* keep in mind the whole path is home/user/tvm... **[ while if one goes to the file location through linux GUI, it shows home/user/tvm... ]**

__$ export PYTHONPATH=/path/to/vta/python:${PYTHONPATH}__

or 

__$ export PYTHONPATH="${PYTHONPATH}:/my/other/path"__


__Comment__ : We add/append the new path to vta library in the tvm directory to your previous PYTHONPATH, so that the other python library files are also accesible !

You can see the paths later by using :

__$ echo $PYTHONPATH__

You should see two paths - one original python libraries and the other tvm/vta path

#### Testing VTA simulator

We run the example file (*test_benchmark_topi_conv2d.py*) installed in the VTA python packaghe or the one attached in the directory **test_benchmark_topi_conv2d** :

If the file is located in the tvm directory:

__$ python <tvm root>/vta/tests/python/integration/test_benchmark_topi_conv2d.py__
   
Once we run this , there are some GOPS that can be seen , when it is running with the host pc hardware : 1.5 ms GOPS for this test
For every convolution layer, the throughput gets reported in GOPS. 

Another example that we run on the VTA Simulator is the RESNET example :
It is also included in the directory **RESNET**

Another example that we run on the VTA Simulator is the Run a Youtube Video Image Classifier


### VTA Configuration in TVM Compiler 

** You can change the TVM comiler according to the VTA Hardware available by providing the configuration specification in the *vta_config.json* file under the TVM root directory

In our case, we did not modify the vta_config.json file as it was working for the FPGA Pynq board h/w.
But if it is needed, one can follow the steps:

__$ cd <tvm root>__
__$ cp vta/config/vta_config.json vta_config.json__
# edit vta_config.json
__$make vta__

## VTA Pynq-Based Test Setup

We set up the VTA Simulator mentioned abpve to run FPGA hardware tests of the complete TVM and VTA software-hardware stack. 

Hardware components used by us:
-- The Pynq FPGA development from Xilinx
-- An Ethernet-to-USB adapter to connect the Pynq board to your development machine.
-- An 8+GB micro SD card.
-- An AC to DC 12V 3A power adapter.

We assume that the Pynq board has been set up , with latest pynq image downloaded.

And it has been assigned a static ip address on the network that the host PC would be connected to.

It was tricky to have the Pynq board connect to the network due to firewall protection, and a dynamic address was allocated.
So important to make sure that it has a static ip address.


### To see what is the static address of the board , follow these steps (if you have a windows based PC connected to the same network) :

-- Steps to verify/check the ip address of pynq needed to connect with the host machine :

* Downloading and opening Putty on the windows machine

* Then logging into a Putty Session to the Host name(or IP address) of the pynq board [as designated while putting it up on the network]

**/ In our case it was 'ca09-vta' 

**/ Use the connection type - *ssh*

* Prompt for username :

__login as : *xilinx*__
__xilinx@ca09-vta's password : *xilinx*__

* Then once the session is on, one can see the terminal bash as :

__xilinx@pynq :~$__

__$ *if-connfig*__

in the command prompt to see ip addresses of the h/w of ca09-vta

* There were 2 other addresses on the ethernet that corresponded to ca09-vta:

* The host PC (linux VM) tried to communicate with both the ip addresses (using ssh)

The ip address that responeded in this case :- __*10.44.4.105*__

The other ip address may also generally work (*but it dint work in our case which maybe because of the firewalls in the intranet*):- __*192.168.2.99*__

Also, the RPC port address of the device in our case was : __*9091*__

This can be seen from the ip address itself or the INFO on command line once we connect with the Pynq board through ssh  

## Connect with VTA H/W i.e. Xilinx Pynq FPGA Board using RPC Server

*  We use the host machine (*in this case a Linux Virtual Machine running on a Windows machine*), to first connect with pynq using ssh

*  Since pynq is on the local network, connected with local machine and not the internet, so we download the tvm directorty in the local machine and the mount or clone the directory from local VM to pynq h/w

* We use *sshfs* for mounting the Pynq's file system to the pynq's file system

So on the Host Linux machien we do the following :

#On Host Side

#Replace mountpoint with new tvm directory in host PC, to be copied to pynbq board [in this case it was: home/raj/tvm]

__$mkdir <mountpoint>__
    
__$sshfs xilinx@10.44.4.127:/home/xilinx <mountpoint>__
    
__$cd <mountpoint>__
    
__$git clone --recursive https://github.com/dmlc/tvm__

#When finished, leave the moutpoint and unmount the directory

__$cd ~__

__$sudo unmount <mountpoint>__
    

** Once the TVM repo has been cloned into Pynq's file system, we directly *ssh* into the pynq h/w and launch the build of the TVM-based RPC server.

** One point - when building TVM as we want to target the Pynq FPGA platform. So here we need the *pynq_sample.json* file to be built rather than the *vta_config.json* default, which targets the VTA simulator on host pc. So we replace the content of vta_config.json file with pynq_sample.json file , in the tvm drectory.

#On host PC , to go directly into pynq FPGA, use ssh :
__ssh xilinx@10.44.4.105__

__#Build TVM runtime library in pynq h/w (would take 5 mins)__

__$cd /home/xilinx/tvm__

__$mkdir build__

__$cp cmake/config.cmake build/.__

__#Copy pynq specific configuration__

__$cp vta/config/pynq_sample.json build/vta_config.json__

__$cd build__

__$cmake ..__

__$make runtime vta -j2__

__#Build VTA RPC server (takes 1 min)__

__$cd ..__

__$sudo ./apps/pynq_rpc/start_rpc_server.sh # pw is 'xilinx'__

##Mention: If one is not in the tvm directory here, then locate to the full address of *start_rpc_server.sh* inside the tvm directory instead of  ./apps/pynq_rpc/start_rpc_server.sh
Once we have started(built and deployed) the RPC server session in the pynq h/w, we should see the following on the command window :

__INFO:root:RPCServer: bind to 0.0.0.0:9091__






































