
# To build TVM in Pynq :



## First Test the VTA Simulator working in the TVM package :


The VTA simulator library is built by default with TVM. 

We have to add the VTA library to our python path to run the VTA examples. The path can look like this :
If 'tvm' is in home directory :
*home/user/tvm/vta/python/vta/*

Some points to be careful with while using:

* path to a python library would have files such as 

    *_init_.py*
    
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


## Connect with VTA H/W i.e. Xilinx Pynq FPGA Board

*  We use the host machine (*in this case a Linux Virtual Machine running on a Windows machine*), to first connect with pynq using ssh

*  Since pynq is on the local network, connected with local machine and not the internet, so we download the tvm directorty in the local machine and the mount the directory from local VM to pynq h/w

-- The ip address of pynq was needed to connect with the machine :

* That was done by downloading and using putty on the windows machine

* Then logging into 'ca09-vta' ssh address

* Then using if-connfig to see ip addresses of the h/w of ca09-vta

* There were 2 other addresses on the ethernet that corresponded to ca09-vta:

* The host PC (linux VM) tried to communicate with both the ip addresses (using ssh)

The ip address that responeded in this case :- __*10.44.4.105*__

The other ip address may also generally work (*but it dint work in our case which maybe because of the firewalls in the intranet*):- __*192.168.2.99*__

Also, the RPC port address of the device in our case was : __*9091*__


