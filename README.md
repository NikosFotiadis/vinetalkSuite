# Instructions

## Download Instructions
`git clone --recursiv https://github.com/vineyard2020/vinetalkSuite.git`

# Single node deployment
First build vine\_talk according to this instructions [vine\_talk](./vine\_talk/README.md)

Then build vine\_controller according to this instructions [vine\_controller](./vine\_controller/README.md)

To write an application with Vinetalk see module: vine\_talk

# Mesos Deployment.

## Dependencies:
Mesos-1.4
Vinetalk-1.0

## Setup
This guide assumes that both mesos, vine\_talk and vine\_controller are installed\build 

(according to the Single node deployment instructions above) in all nodes, 

mesos master is up and running, variable $MESOS\_MASTER contains the URL of the server,

and variable MESOS\_HOME points to the installation directory of the server.

1. Launch vine-controller to all agent nodes. (for instructions see
module vine\_controller)
2. Update file conf/resourcesWithVaq.txt for each node to reflect the proper amount of 

resources of each node. Note the last element is the number of VAQs of each
node. 
3. Start mesos agents. Use script sbin/mesos-agent-vaq.sh as a reference

## Application Development
This is a three-step process:
1. Develop a single node solution that uses Vinetalk to execute some
kernel. For instructions refer to the single node instructions, found at
module Vinetalk 
2. Develop a Mesos executor (see folder examples)
3. Develop a Mesos Framework (or use an existing one that knows how to
accept vaq resources) of its executor) (see folder examples)

## Examples
Folder examples contains an example on how Vinetalk enabled frameworks use
VAQ resources. There is also an example that demonstrates a proper submission of 
a Vinetalk-based application via the REST API.

Instructions (We assume that all but the first instructions are invoked from folder examples):

1. Compile kernel: from folder resources/kernels run make 
2. To compile an executor: `make executorName`
3. To compile a framework: `make frameworkName`
4. To run the framework found at vaq\_framework.cpp: `make (YYY ?)`

# Publications

Mavridis, S., Pavlidakis, M., Kozanitis, Ch., Chrysos, N., Stamoulias, I., Kachris, C., Soudris, D., & Bilas, A. (2017). VineTalk: Simplifying Software Access and Sharing of FPGAs in Datacenters. 26th International Conference on Field Programmable Logic and Applications (FPL 2017), Ghent, Belgium, 4 - 8 September

