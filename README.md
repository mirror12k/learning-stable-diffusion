https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html
might need to install nvidia-docker.

make sure your nvidia-driver-535 matches!

use `nvidia-smi` to check if the driver is correct!

download `sd-v1-4-full-ema.ckpt` from: https://huggingface.co/CompVis/stable-diffusion-v-1-4-original/tree/main

```sh
python3 scripts/txt2img.py --prompt "a professional photograph of an astronaut riding a horse" --ckpt /app/data/768-v-ema.ckpt --config configs/stable-diffusion/v2-inference-v.yaml --H 768 --W 768 --device cuda

env PYTORCH_CUDA_ALLOC_CONF=garbage_collection_threshold:0.6,max_split_size_mb:128 python3 scripts/txt2img.py --prompt "a professional photograph of an astronaut riding a horse" --ckpt /app/data/768-v-ema.ckpt --config configs/stable-diffusion/v2-inference-v.yaml --H 256 --W 256 --device cuda --n_samples 1 --ddim_steps 50

python3 optimizedSD/optimized_txt2img.py --prompt "Cyberpunk style image of a Tesla car reflection in rain" --H 512 --W 512 --seed 27 --n_iter 2 --n_samples 1 --ddim_steps 50 --ckpt /app/data/768-v-ema.ckpt
```
