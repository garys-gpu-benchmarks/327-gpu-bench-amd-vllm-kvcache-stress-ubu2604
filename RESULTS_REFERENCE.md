# Results: 327 KV Cache Stress Test

**Main goal:** Analyze LLM KV-cache stress under long contexts  
**Tools:** Start python -m vllm.entrypoints.openai.api_server on port 8000, then run scripts/benchmark_serving.py

Reference results from the validation run on the system shown in each section (recorded 2026-11-22). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× AMD Instinct MI300X VF (196288 MB) · INTEL(R) XEON(R) PLATINUM 8568Y+ · Ubuntu 26.04.1 LTS · kernel 7.0.0-43-generic · driver 7.1.9.31600000
- **Run:** 2026-11-22T15:08:07Z · status **PASS** (exit 0)
- **Time (mm:ss):** setup 04:06 · benchmark 00:06 · whole run 05:16
- **Source:** run 327_20261122_150807
- **Command:** `bash run_benchmark.sh --smoke --model-name mistralai/Mistral-7B-v0.3 --dtype bfloat16 --kv-cache-dtype auto --gpu-memory-utilization 0.9 --max-model-len 128 --input-len 64 --output-len 16 --num-prompts 2 --concurrency 2 --seed 0`

| # | Metric | Result |
|---|---|---|
| 1 | Decode throughput, tokens/s (output_tokens_per_sec) | 401.31036931780636 |
| 2 | Time To First Token p50, ms (ttft_msec) | 21.772549999923285 |
| 3 | TPOT p50, ms (tpot_msec) | 4.69281723333855 |
| 4 | Peak KV-cache usage, GiB (kv_cache_peak_gb) | 0.019532248989820367 |
| 5 | KV-cache usage peak, pct (kv_cache_usage_peak_pct) | 0.01278706971510335 |
<!-- /profile:smoke -->
