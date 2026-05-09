> [!TIP]
> Maximum contexts window size to run with RTX 3050 4GB Laptop GPU using
> llama-cpp-python settings:
> ```
> n_gpu_layers=-1,
> flash_attn=True,
> type_k=2, # q4_0
> type_v=2, # q4_0
> ```

| Source | Model | Parameters | Quantization | Contexts Limit | Link |
| --- | --- | --- | --- | --- | --- |
| ggml-org | Gemma 4 | E2B | Q8_0 | 125K | [gemma-4-E2B-it-Q8_0.gguf](https://huggingface.co/ggml-org/gemma-4-E2B-it-GGUF/blob/main/gemma-4-E2B-it-Q8_0.gguf) |
| ggml-org | Gemma 4 | E4B | Q4_K_M | 14K | [gemma-4-E4B-it-Q4_K_M.gguf](https://huggingface.co/ggml-org/gemma-4-E4B-it-GGUF/blob/main/gemma-4-E4B-it-Q4_K_M.gguf) |
| ggml-org | Qwen 3.5 | 0.8B | Q4_0 | 256K | [Qwen3.5-0.8B-Q4_0.gguf](https://huggingface.co/ggml-org/Qwen3.5-0.8B-GGUF/blob/main/Qwen3.5-0.8B-Q4_0.gguf) |
| ggml-org | Qwen 3 | 0.6B | Q4_0 | 40K | [Qwen3-0.6B-Q4_0.gguf](https://huggingface.co/ggml-org/Qwen3-0.6B-GGUF/blob/main/Qwen3-0.6B-Q4_0.gguf) |
| ggml-org | Qwen 3 | 1.7B | Q4_0 | 40K | [Qwen3-1.7B-Q4_K_M.gguf](https://huggingface.co/ggml-org/Qwen3-1.7B-GGUF/blob/main/Qwen3-1.7B-Q4_K_M.gguf) |
| ggml-org | Qwen 3 | 4B | Q4_K_M | 23K | [Qwen3-4B-Q4_K_M.gguf](https://huggingface.co/ggml-org/Qwen3-4B-GGUF/blob/main/Qwen3-4B-Q4_K_M.gguf) |
| ggml-org | Qwen 3 | 4B-Instruct-2507 | Q8_0 | ❌ (not enough vram) | [qwen3-4b-instruct-2507-q8_0.gguf](https://huggingface.co/ggml-org/Qwen3-4B-Instruct-2507-Q8_0-GGUF/blob/main/qwen3-4b-instruct-2507-q8_0.gguf) |
| ggml-org | Qwen 3 | 4B-Thinking-2507 | Q8_0 | ❌ (not enough vram) | [qwen3-4b-thinking-2507-q8_0.gguf](https://huggingface.co/ggml-org/Qwen3-4B-Thinking-2507-Q8_0-GGUF/blob/main/qwen3-4b-thinking-2507-q8_0.gguf) |
