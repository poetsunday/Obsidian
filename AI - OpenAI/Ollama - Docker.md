![](https://github.com/jmorganca/ollama/assets/3325447/080f3a72-e2fd-4741-8070-ae79a06f943f)

### Ollama Docker image

[![Discord](https://dcbadge.vercel.app/api/server/ollama?style=flat&compact=true)⁠](https://discord.gg/ollama)

[Ollama⁠](https://github.com/jmorganca/ollama)

makes it easy to get up and running with large language models locally.

###### CPU only

docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama

###### Nvidia GPU

Install the [NVIDIA Container Toolkit⁠](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html#installation)

.

**Install with Apt**

1. Configure the repository

curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey \
    | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list \
    | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' \
    | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
sudo apt-get update

1. Install the NVIDIA Container Toolkit packages

sudo apt-get install -y nvidia-container-toolkit

**Install with Yum or Dnf**

1. Configure the repository

curl -s -L https://nvidia.github.io/libnvidia-container/stable/rpm/nvidia-container-toolkit.repo \
    | sudo tee /etc/yum.repos.d/nvidia-container-toolkit.repo

1. Install the NVIDIA Container Toolkit packages

sudo yum install -y nvidia-container-toolkit

**Configure Docker to use Nvidia driver**

sudo nvidia-ctk runtime configure --runtime=docker
sudo systemctl restart docker

**Start the container**

docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama

###### AMD GPU

To run Ollama using Docker with AMD GPUs, use the `rocm` tag and the following command:

docker run -d --device /dev/kfd --device /dev/dri -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:rocm

###### Run model locally

Now you can run a model:

docker exec -it ollama ollama run llama3

###### Try different models

More models can be found on the [Ollama library⁠](https://ollama.com/library)

.

###### Learn more

[htt[[Create LLM from Hugging Face for Ollama]]

ps://github.com/ollama/ollama⁠](https://github.com/ollama/ollama)