# ut-health-final-proj
Final high risk project for AI in Healthcare 

# Create the environment
Install conda from the anaconda website at [www.anaconda.org/download](https://www.anaconda.com/download)


After installing Anaconda, open a command prompt and:
* go to the directory where this repo has been downloaded
* execute `conda env create -f environment.yml`

These are the important packages used:

* __SQLAlchemy__ for loading MIMIC-III data
* __networkx__ for creating the network graph 
* __pyvis__ for visualizing and debugging the network graph

# Project Architecture
<img src="images/proj-architecture.jpg" alt="Architecture" width="800"/>


# Creating the Graph Network

The graph is created in the jupyter file `01-create-network-graph.ipynb`.
This file assumes you have SQL Lite installed and MIMIC-III data loaded into it.

This file generates two main outputs:
* __pickle file__: this is in the [pickle](pickle/) folder which contains the serialized network graph in binary form
* __pyvis file__: this is in the [pyvis](pyvis/) folder which contains the html representation of the network graph

The pickle files are named in the format `patients_graph_max_X_nodes.gpickle`. The `X` in the file name specifies the number of patients nodes, hence, the size of the graph.

E.g.:, 
* `patients_graph_max_10_nodes.gpickle` means the pickle file has 10 patient nodes and is a relatively small and manageable file to process on a laptop.
* `patients_graph_max_40000_nodes.gpickle` means the pickle file has 40,000 patient nodes and is a very large file that cannot be loaded on your laptop.

Pick a pickle file accordingly.

The pyvis files in the [pyvis](pyvis/) folder are named in the same manner.

# Pickle files of network graph
The graph is saved as a pickle file in the directory [pickle](pickle/)

Each pickle file is named according to the number of nodes it contains.

The pickle file has the graph where:
* each node is a patient
* each edge is a diagnosis connecting two patients

# Visual graph
The visual graph is saved as an HTML file in the directory [pyvis](pyvis/). This graph is created with the library `pyvis` and represents the underlying network graph (created with library `networkx`) that it visually represents.

The pyvis graph is useful for:
* visually observing the network graph
* exploring the nodes and edges
* validating the structure of the `networkx` graph that this pyvis graph represents

Sample Pyvis graph with 9 patient nodes connected by shared diagnoses:
<img src="images/sample_pyvis_graph_9_nodes.jpg" alt="Sample Pyvis Graph" width="800"/>
