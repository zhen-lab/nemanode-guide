### Working with Nemanode datasets


Here is a JSON snippet from one of the Nemanode datasets:
```json
[
  {
    "ids": [
      278,
      278,
      280
    ],
    "post": "BWM-DL02",
    "post_tid": [
      7063254,
      7063254,
      7063108
    ],
    "pre": "RMHR",
    "pre_tid": [
      7059560,
      7059560,
      7059620
    ],
    "syn": [
      1,
      1,
      1
    ],
    "typ": 0,
    "datasetType": "head",
    "datasetId": "TEM_L3"
  },
  ...
]
```
Each dataset consists of a list of connections.

Each connection will have the following structure:

```json
  {
    "ids": [
      278,
      278,
      280
    ],
    "post": "RIML",
    "post_tid": [
      7063254,
      7063254,
      7063108
    ],
    "pre": "AWAL",
    "pre_tid": [
      7059560,
      7059560,
      7059620
    ],
    "syn": [
      1,
      1,
      1
    ],
    "typ": 0,
    "datasetType": "head",
    "datasetId": "TEM_L3"
  }
```

### Understanding the connection data fields

Each connection has a set fields describing the connection:
- ```pre```: name of the post-synaptic cell (string) e.g. AWAL
- ```post```: name of the post-synaptic cell (string) e.g. RIML
- ```typ```: the type of the connection
    - ```0```: means that the connection is a chemical synapse
    - ```2```: means that the connection is a electrical synapse (gap junction)
- ```datasetType```:  the location of the connection, one of ```tail```, ```head``` ```complete```
- ```datasetId```: the id of the dataset that the connection is apart of 

Each connection also has a set of fields that describe each of the synapses that it represents
- ```ids```:  a list of synapse ids of size N.  syn[0] corresponds to the first synapse, syn[1] corresponse to the second synapse, etc.
- ```syn```: the number of synapses encoded as a list of numbers.  e.g. [1, 1, 1] means there is 3 synapses in the connection
- ```post_tid```: the ids of the post synaptic tree nodes of the synapses (used for the 3d neuron trajectory visualization) 
    - ***Note***: These are not present in the legacy datasets
- ```pre_tid```: the ids of the pre synaptic tree nodes of the synapses (used for the 3d neuron trajectory visualization)
    - ***Note***: These are not present in the legacy datasets

