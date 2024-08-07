FROM nvidia/cuda:11.1.1-cudnn8-devel-ubuntu20.04

ENV FORCE_CUDA="1"
ENV MMCV_WITH_OPS=1
ENV PATH="/opt/conda/bin:$PATH"

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3-pip     \
    libgl1-mesa-glx \
    libsm6          \
    libxext6        \
    libxrender-dev  \
    libglib2.0-0    \
    git             \
    python3-dev     \
    python3-wheel

# Version info from https://pytorch.org/get-started/previous-versions/    
RUN pip3 install --no-cache-dir -f https://download.pytorch.org/whl/cu111/torch_stable.html \
    wheel                   \
    "torch==1.10.1+cu111"   \
    "torchvision==0.11.2+cu111" \
    "torchaudio==0.10.1" 

# Install requirements
COPY ./docker_requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt


RUN mkdir -p workspace
WORKDIR /workspace