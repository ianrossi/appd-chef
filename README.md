A service that will get a node ready to be consumed by Chef Server in a provisioning environment run by VMWare's Application Directory. (Chef-AppD integration)
The idea is to do most of what a knife bootstrap command does, minus
the assignment of run list items. Currently Linux-only. Once this
service completes successfully on the node, you can then use another
bash script to run:

chef-client -o 'recipe[your_recipe]'

or you can do:

chef-client -j 'YOUR_JSON_HERE'

on the node.

In this setup, Application Director can act as an orchestrator or
composer and manage the provision of clusters, while Chef takes care
of the details per-node. This design will still work fully with Chef
Server and all the power it provides.

Requirements:
- curl installed on the node to be bootstrapped
- An accessible HTTP file repository
- A validation.pem file hosted in the file repository
- A client.rb file that points to the Chef Server hosted on the file
  repository
  
Usage
=====

In order to use this service in VMWare Application Director, download the ChefBootstrap.xml file to your AppD server and use the CLI import instructions from VMWare: 
http://pubs.vmware.com/appdirector-5/index.jsp?topic=%2Fcom.vmware.appdirector5.using.doc%2FGUID-CDFEACB7-861B-4999-9D84-D31344895613.html
