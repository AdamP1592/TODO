# RAG SAFETY TOOL

## Reasoning
There are many apps that keep a repository of products to identify how safe they are. Where, in doing so, it yields lower latency and dedicated data processing, those require considerable storage overhead and act more as a single view on the product. This can be good for ease, but invalidated data, new products, local-only regulatory concerns, there are many failings of this kind of system. I wanted something that I could have more confidence in. 

So, I am going to build a RAG-based lookup tool that can interface with a variety of global sources directly, on lookup, and translate the information back to you in a reasonable format. I also want this to be agnostic to language.

- Two model split: a low-context smaller model often performs better than a large multidomain model. Where it does introudce more complexity in architecture, the search becomes agnostic to non-legacy model types, where tooling capability is provided directly instead of processed in-chat. Decoupling the two models also allows easy modification of search functionality in isolation of other tasks, allowing an easier path for development. 
- One big benefit a capable small multilingual model handles translation as a natural byproduct of search. So, no aspect of the interface requires that translation, reducing the scope of what it's required to do, allowing for stronger performance. 
- Prioritizing local sources over distant sources can resolve latency issues, but not all local sources are as strong as global ones. So, a multistage system utilizing confidence metrics to ensure the user recieves valid information is necessary. Stage 1: search local, identify confidence in information, respond quickly if it's valid. If it's not valid, move to stage 2. Stage 2: search global, identify confidence in information, relay information as well as confidence in it.

## Sketch
2 main models:
1. Interface model
    - Model responsible for utilizing search results
    - Interprets results of search as well as confidence level from Search Model
    - Two stage search functionality
        1. Inital search prioritizes local sources for lower latency. Confidence and Relevance metrics are utilized to determine if stage 2 is necessary.
        2. Stage 2 is a global search, it will introduce more latency, but will always provide more robust results.

2. Search Model
    - Very small model responsible for handling search requests(something like haiku)
    - Translate user query into proper terminology for search 
    - Summarize and translate the results of that search back to the original language (aggregate and normalize)
    - Returns a confidence and relevance metrics
