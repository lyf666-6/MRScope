# -
以 Qwen2.5-VL-7B-Instruct 为主干，基于 VRSBench、MME Real RS、XLRS-bench 和 LEVIR-CC 构建统一遥感多任务指令数据，通过 LoRA 完成遥感语义对齐，引入高分辨率自适应切片路由解决超大图和小目标问题，引入差分变化适配器处理双时相变化检测与变化描述，并结合轻量分割/定位任务头、INT4/INT8 量化和推理容错机制，形成兼顾任务性能、资源效率和星载可靠性的多模态遥感大模型系统。
## Runtime Environment

- OS: Ubuntu 22.04.5 LTS
- GPU: NVIDIA GeForce RTX 4080 SUPER, 16 GB VRAM
- Driver: 550.163.01
- Python: 3.10.9
- PyTorch: 2.5.1+cu121
- Transformers: 5.14.0.dev0
- Bitsandbytes: 0.49.2
- Quantization: 4-bit `bitsandbytes`

## Baseline Inference Notes

- Reference model path size: about 16 GB
- Tested image size: 1024 x 768
- Test prompt: `Describe the image in detail.`
- Inference status: success
- Inference scripts: `infer_qwen25vl_official_4bit.py`, `run_infer.py`
- Typical runtime: about 2 to 5 seconds
- Peak VRAM during inference: about 8 GB
- `max_pixels`: `602112`
- `min_pixels`: `200704`
- `max_new_tokens`: `128`