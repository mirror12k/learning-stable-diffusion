#!/usr/bin/env -S bash -c "docker run -v \${PWD}/data:/app/data -p7860:7860 --rm --runtime=nvidia -it \$(docker build docker 1>&2 && docker build -q docker) \$@"
FROM nvidia/cuda:12.2.0-devel-ubuntu20.04

WORKDIR /app

ARG DEBIAN_FRONTEND=noninteractive
RUN apt update \
	&& apt-get install -y git curl wget python3-pip \
	&& apt-get install -y libgl1 libgtk2.0-dev xserver-xorg-video-nvidia-535 nvidia-driver-535
	# && apt autoclean \
	# && apt autoremove \
	# && apt clean

# RUN git clone https://github.com/Stability-AI/stablediffusion
# RUN cd stablediffusion && pip3 install -r requirements.txt
# RUN git clone https://github.com/basujindal/stable-diffusion
# RUN cd stable-diffusion \
# 	&& pip3 install -e . \
# 	&& pip3 install OmegaConf Pillow einops torchvision pytorch-lightning==v1.6.5 pandas transformers taming-transformers taming-transformers-rom1504 scipy \
# 	&& pip3 install numpy imageio imageio-ffmpeg scikit-image tqdm tensorboardX opencv-python kornia \
# 	&& pip3 install git+https://github.com/openai/CLIP.git
RUN git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
RUN cd stable-diffusion-webui \
	&& pip3 install -r requirements.txt \
	&& cd models/Stable-diffusion \
	&& wget https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors \
	&& wget https://huggingface.co/stabilityai/stable-diffusion-xl-refiner-1.0/resolve/main/sd_xl_refiner_1.0.safetensors \
	&& wget https://huggingface.co/Corruptlake/Sci-Fi-Diffusion/resolve/main/Sci-Fi_Diffusion_1.0.safetensors

CMD bash
