### Import from GGUF

[](https://github.com/ollama/ollama#import-from-gguf)

Ollama supports importing GGUF models in the Modelfile:

1. Create a file named `Modelfile`, with a `FROM` instruction with the local filepath to the model you want to import.
    
    ```
    FROM ./vicuna-33b.Q4_0.gguf
    ```
    

Create the model in Ollama

```
ollama create example -f Modelfile
```

Run the model
ollama run example
[[Ollama - Docker]]

