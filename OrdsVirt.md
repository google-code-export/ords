# Introduction #

This is a quick overview of the API provided to manage VMs

```
legend:           HTTP-METHOD(ParameterType)

/vm               GET 
/vm/<name>        GET DELETE POST(ChangeRequest) PUT(NodeTypeInfo or TemplateInfo)
/nodetype         GET()
/nodetype/<name>  GET()
/status           GET()

/template         GET()
/template/<name>  GET()
```

# Details #

Currently the JavaDoc is not hosted online. Links to describe the datatypes will be added later. This document currently only gives a overview of the API but doesn't contain the information to implement a client.

A simple example client is provided here: https://svn.oucs.ox.ac.uk/projects/ords/virtualisation-client/

## /vm ##
  * **GET** Returns a list of names of VMs hosted in ORDS.

## /vm/name ##

  * **GET** Returns information about a specific VM. (name, network address, ...)
  * **DELETE** Deletes the VM with the given name
  * **POST** Changes the status of a VM (start/stop)
  * **PUT** Creates a new VM instance from a node type of template

## /nodetype ##

  * **GET** Gets list of node types. New VMs can be instantiated from node types. A node type is usually a SaaS node.

## /nodetype/name ##

  * **GET** Returns a nodetype object. This can **PUT** to `/vm/newvmname` to create a new node instance.

## /status ##

  * **GET** Used to check the status of the service. Also returns the number of open connections in the connection pool.

## /template/`*` ##

Operates in the same way as `/nodetype` and `/nodetype/name` but uses VM templates instead. A VM template is a simple instance of a VM from a VM template but is not managed as a SaaS node.
This is not currently used by ORDS.