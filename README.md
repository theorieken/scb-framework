# SCB Framework
 
## Description

This framework provides a platform for the implementation and simulation of biological 
multi-scale and multi-component systems. It contains the libraries listed below, which 
contain different components from different space-time levels for free use.

## Nodes and Origins

Biological systems are graph-based and consist of nodes and chemical or electrical edges. 
Nodes are of the type of a class of your choice - to create new nodes you can use the file 
`default.py` in `Framework/Nodes`. You can also use existing nodes from the library below. Origins 
allow you to better organize data and the system itself - by defining origins, you can 
depict the biological system of interest on a different, more accessible scale and assign 
multiple nodes to origins. 
    
## System encoding

The input parameter of the framework is the biological system, which is encoded as a 
json file as follows. It must contain the shown indices, otherwise errors are generated. 
In the data indices of both nodes and origins, you can provide information to your node 
or origin. 

    {
        "name": <the name of your system>,
        "version": <give it a version>,
        "origins": [
            {
                "id": <unique id of origin>,
                "name": <name of origin e.g. Spinal Cord Neuron>,
                "location" <location for better data organisation>,
                "class": <type of origin you want to add>,
                "data": <specific data for constructor>                
            },
            ...
        ],
        "node": [
            {
                "id": <id of the node>,
                "is_input_node": <bool if node gets global system input>,
                "origin_id": <if of origin object the node belongs to>,
                "class": <the type of node>,
                "electrical_edges": [<ids of adjacent electrical nodes>],
                "chemical_edges": [<ids of adjacent chemical nodes>],
                "data": <specific data for nodes constructor>,
                "vars": <optional overwriting of default parameters>            
            },
            ...
        ],
        "input": {
            time: [<a time vector for system input signal>],
            value: [<the corresponding values for the input vector>]        
        }
    } 
    
## Using the Framework

The program is executed in the following way. Later on, the step size will disappear and will be replaced with a 
multiscale approach, where each node element has its own numerical parameters.

    Framework/run.py <system>
    
Of course you can also create your own files in which you instantiate the framework. 

## Bibliotheken

There are currently no public libraries. However, this software is open source - share your computational 
models by creating a pull request. 