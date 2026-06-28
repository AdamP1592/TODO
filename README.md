# TODO
This is just a repository that stores a list of project descriptions I intend on tackling in the future.

## Projects:

### RAG Safety Lookup.
2 main models:
1. Interface model
    - Model responsible for utilizing search results
    - Interprets results of search as well as confidence level from Search Model
2. Search Model
    - Very small model responsible for handling search requests(something like haiku)
    - Translate user query into proper terminology for search 
    - Summarize and translate the results of that search (aggregate and normalize)
    - Returns a confidence value as well as the results


### RAG Resume Refiner
- Instead of the standard "build it for them" a system that recommends specific changes and provides reasoning for suggesting them, while also allowing for an underlying initial custom prompt to be wrote for providing the llm direction.

### Compute Cluster Digital Twin
- A simulated compute cluster that allows me to operate as though each node is an independent part of a real network.

### Neuron Growth Cone Dynamics Simulation
- A simulation of the growth and movement of neurons over time.

### Spatiotemporal Attention Transformer Model
- Stablize the movement of a traditional motion governor(like MPCs) utilizing a transformer model trained to make adjustments to stabilize and smooth the motion.
- Done in simu, with rigid body dynamics.

### Robotic Prosthetic Modular EMG Density Grid
[redacted]

## Learning:

### TinyGrad & ONNX for remote physical ai deployment

### Unity for simulation rendering instead of opengl or others

### 