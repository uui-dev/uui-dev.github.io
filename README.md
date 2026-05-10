# llama-cpp-python

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

---

# Ollama

> [!TIP]
> maximum context size using KV cache q8_0. to set q8_0 for KV cache:
> ```
> sudo systemctl edit ollama.service
> ```
> inside the file, make sure to input the environments like this:
> ```
> ### Editing /etc/systemd/system/ollama.service.d/override.conf
> ### Anything between here and the comment below will become the contents of the drop-in file
> 
> [Service]
> Environment="OLLAMA_FLASH_ATTENTION=1"
> Environment="OLLAMA_KV_CACHE_TYPE=q8_0"
>
> ### Edits below this comment will be discarded
>
>
> ### /etc/systemd/system/ollama.service
> # [Unit]
> # Description=Ollama Service
> # After=network-online.target 
> ```
> and then run:
> ```
> sudo systemctl daemon-reload
> sudo systemctl restart ollama.service
> ```
> 
> To change num_gpu and num_ctx, type this after running `ollama run <model>`:
> ```
> /set parameter num_gpu <num_gpu>
> /set parameter num_ctx <num_ctx>
> ```

| model | parameter | quantization | num_gpu | num_ctx |
| --- | --- | --- | --- | --- |
| cogito:3b-v1-preview-llama-q4_K_M | 3b | q4_K_M | 29 | 22528 (22k) |
| deepseek-r1:1.5b-qwen-distill-q4_K_M | 1.5b | q4_K_M | 29 | 98304 (96k) |
| deepseek-r1:1.5b-qwen-distill-q8_0 | 1.5b | q8_0 | 29 | 96256 (94k) |
| gemma3:4b-it-q4_K_M | 4b | q4_K_M | 35 | 13312 (13k) |
| granite4:3b-h | 3.2b | q4_K_M | 41 | 130048 (127k) |
| granite4:7b-a1b-h | 7b | q4_K_M | 33 (of 41) | 4096 (4k) |
| granite4.1:3b-q2_K | 3b | q2_K | 41 | 48128 (47k) |
| granite4.1:3b-q4_K_S | 3b | q4_K_S | 41 | 32768 (32k) |
| granite4.1:3b-q4_K_M | 3b | q4_K_M | 41 | 30720 (30k) |
| llama3.2:3b-instruct-q4_K_M | 3b | q4_K_M | 29 | 22528 (22k) |
| ministral-3:3b-instruct-2512-q4_K_M | 3b | q4_K_M | 26 (of 27) | 4096 (4k) |
| nemotron-mini:4b-instruct-q4_K_M | 4b | q4_K_M | 33 | 4096 (4k) |
| phi4-mini:3.8b-q4_K_M | 3.8b | q4_K_M | 33 | 11264 (11k) |
| qwen2.5:0.5b-instruct-q8_0 | 0.5b | q8_0 | 25 | 32768 (32k) |
| qwen2.5:1.5b-instruct-q8_0 | 1.5b | q8_0 | 29 | 32768 (32k) |
| qwen2.5:3b-instruct-q6_K | 3b | q6_K | 37 | 32768 (32k) |
| qwen2.5:3b-instruct-q8_0 | 3b | q8_0 | 37 | 8192 (8k) |
| qwen2.5:3b-instruct-q8_0 | 3b | q8_0 | 31 (of 37) | 32768 (32k) |
| qwen2.5:7b-instruct-q4_K_M | 7b | q4_K_M | 20 (of 29) | 4096 (4k) |
| qwen2.5:7b-instruct-q4_K_M | 7b | q4_K_M | 15 (of 29) | 32768 (32k) |
| qwen2.5-coder:0.5b-instruct-q8_0 | 0.5b | q8_0 | 25 | 32768 (32k) |
| qwen2.5-coder:1.5b-instruct-q8_0 | 1.5b | q8_0 | 29 | 32768 (32k) |
| qwen2.5-coder:3b-instruct-q6_K | 3b | q6_K | 37 | 32768 (32k) |
| qwen2.5-coder:3b-instruct-q8_0 | 3b | q8_0 | 37 | 8192 (8k) |
| qwen2.5-coder:3b-instruct-q8_0 | 3b | q8_0 | 31 (of 37) | 32768 (32k) |
| qwen2.5-coder:7b-instruct-q2_K | 7b | q2_K | 29 | 17408 (17k) |
| qwen2.5-coder:7b-instruct-q2_K | 7b | q2_K | 24 (of 29) | 32768 (32k) |
| qwen2.5-coder:7b-instruct-q4_K_M | 7b | q4_K_M | 20 (of 29) | 4096 (4k) |
| qwen2.5-coder:7b-instruct-q4_K_M | 7b | q4_K_M | 15 (of 29) | 32768 (32k) |
| qwen3:0.6b-q8_0 | 0.6b | q8_0 | 29 | 40960 (40k) |
| qwen3:1.7b-q4_K_M | 1.7b | q4_K_M | 29 | 35840 (35k) |
| qwen3:1.7b-q8_0 | 1.7b | q8_0 | 29 | 26624 (26k) |
| qwen3:4b-instruct-2507-q4_K_M | 4b | q4_K_M | 37 | 13312 (13k) |
| qwen3.5:0.8b-q8_0 | 0.8b | q8_0 | 25 | 95232 (93k) |
| qwen3.5:2b-q4_K_M | 2b | q4_K_M | 25 | 46080 (45k) |
| qwen3.5:2b-q8_0 | 2b | q8_0 | 24 (of 25) | 4096 (4k) |
| qwen3.5:4b-q4_K_M | 4b | q4_K_M | 28 (of 33) | 4096 (4k) |
