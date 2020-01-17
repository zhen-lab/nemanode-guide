### Understanding Zhen Lab datasets


Here is a JSON snippet from one of the legacy datasets:
```json
[
  {
    "ids": [
      301
    ],
    "post": "ASHL",
    "pre": "ADLL",
    "syn": [
      1
    ],
    "typ": 0,
    "datasetType": "complete",
    "datasetId": "l1"
  },
  ...
]
```
Each legacy dataset consists of a list of connections.

Each connection will have the following structure:

```json
  {
    "ids": [
      301
    ],
    "post": "ASHL",
    "pre": "ADLL",
    "syn": [
      1
    ],
    "typ": 0,
    "datasetType": "complete",
    "datasetId": "l1"
  }
```

### Understanding the connection data fields

Each connection has a set fields describing the connection:
- ```pre```: name of the post-synaptic cell (string) e.g. AWAL
- ```post```: name of the post-synaptic cell (string) e.g. RIML
- ```typ```: the type of the connection
    - 0: means that the connection is a chemical synapse
    - 2: means that the connection is a electrical synapse (gap junction)
- ```datasetType```:  the location of the connection, one of ```tail```, ```head``` ```complete```
- ```datasetId```: the id of the dataset that the connection is apart of 

Each connection also has a set of fields that describe each of the synapses that it represents
- ```ids```:  a list of synapse ids of size N.  syn[0] corresponds to the first synapse, syn[1] corresponse to the second synapse, etc.
- ```syn```: the number of synapses encoded as a list of numbers.  e.g. [1, 1, 1] means there is 3 synapses in the connection
