DOCKERS

docker ps –a
docker run –itd –name <container_name> <image_name>
docker stop <container_name>
docker rm –f <container_name>
docker exec –it <container_name> <cmd e.g. ./bin/bash>
docker restart tf-server-aziz-03

docker exec –it ubuntu-aziz-01 ./bin/bash
docker exec -it ubuntu-aziz ./bin/bash
nvidia-docker stop tf-gpu-aziz-01
nvidia-docker rm –f wonderful_jackson

docker exec -it tf-gpupy3-aziz-01 ./bin/bash
docker exec -it -e COLUMNS=800 -e LINES=800 ubuntu-aziz-02 ./bin/bash
docker exec -it -e COLUMNS=800 -e LINES=800 tf-serve-aziz-01 ./bin/bash
nvidia-docker exec -it -e COLUMNS=800 -e LINES=800 tf-gpu-p3-aziz-01 ./bin/bash
nvidia-docker exec -it -e COLUMNS=800 -e LINES=800 anaconda-stella ./bin/bash
nvidia-docker exec -it -e COLUMNS=800 -e LINES=800 tf-model-aziz-01 ./bin/bash

nvidia-docker commit ubuntu-aziz-01 ubuntu-aziz-04
nvidia-docker run -itd -name ubuntu-aziz-04

nvidia-docker run -it --name tf-model-aziz-01 --runtime=nvidia -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all anaconda/retinamask
nvidia-docker run -itd --name tf-client-aziz-03 aziz/tf-client --runtime=nvidia --rm nvidia/cuda nvidia-smi -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all 
nvidia-docker run -it --name tf-client-aziz-04 --runtime=nvidia nvidia-smi -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all -v /home/aziz:/home/aziz aziz/tf-client
nvidia-docker run -itd --name tf-gpu-py3-aziz-01 -v /home/aziz:/home/aziz tensorflow/tensorflow:1.5.1-gpu-py3
nvidia-docker run -itd --name tf-server-aziz-03 -p 7013:7013 -v /home/aziz:/home/aziz --runtime=nvidia -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all ubuntu:16.04
nvidia-docker run -itd --name tf-server-aziz-04 -p 7014:7014 -v /home/aziz:/home/aziz --runtime=nvidia -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all ubuntu:16.04
nvidia-docker run -itd --name tf-model-aziz-02 --runtime=nvidia -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all -v /home/aziz/:/home/aziz ubuntu:16.04

docker run -itd --name tf-client-20191113 --gpus '"device=2"' -p 8181:8181 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ ubuntu:16.04

docker run -itd --name tf-svr-histo-20200108 --gpus '"device=0,1"' -p 8502:8500 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ -v /raid/shared/aziz/models:/models/ tensorflow/serving:latest-gpu --rest_api_port=8503 --model_config_file=/models/models.conf --enable_model_warmup=false
docker run -itd --name tf-svr-retina-20200108 -p 8500:8500 --gpus '"device=0,1"' -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ -v /home/cwtan501/data/retina-dsi/tf-serving-retina/tfmodels:/models/ tensorflow/serving:1.12.3-gpu --rest_api_port=8501 --model_config_file=/models/models.conf

docker run -itd --name venv-20200416 --gpus '"device=2,3"' -p 7010:7010 -p 7020:7020 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ tf_gpu-2.0:20191206
docker run -itd --name r-20210214 -p 7030:7030 -p 7040:7040 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ r-base
tensorflow_model_server --port=8500 --rest_api_port=8501 --model_name=${MODEL_NAME} --model_base_path=${MODEL_BASE_PATH}/${MODEL_NAME}

nvidia-docker run --gpus '"device=2"' --rm -ti --mount type=volume,source=

docker run -itd --name api-mic-nginx -p 9010:9010 -p 9011:9011 -v /home/aziz/:/home -v /raid/shared/aziz:/raid/ ubuntu:16.04

--runtime=nvidia
--rm nvidia/cuda nvidia-smi
-e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all 

python -c "import tensorflow as tf; tf.enable_eager_execution(); print(tf.reduce_sum(tf.random_normal([1000, 1000])))"

conda create -n tf-gpu-1.9 tensorflow-gpu=1.9
conda activate tf-gpu-1.9
conda create -n flask flask
\q
apt install nvidia-cuda-toolkit

/home/cwtan501/data/retina-dsi/tf-serving-retina
docker-compose up

created, restarting, running, removing, paused, exited and dead
docker ps -a --format '{{.ID}}\t{{.CreatedAt}}\t{{.Names}}'
docker ps --format "table {{.ID}}\t{{.Labels}}"
docker ps -a --filter 'status=running' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Names}}'
docker ps -a --filter 'status=running' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Ports}}'
docker ps -a --filter 'status=running' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Image}}'
docker ps -a --filter 'ancestor=tf_gpu-2.0' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Image}}'

docker ps -a --filter 'status=created' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Status}}\t{{.Names}}'
docker ps -a --filter 'status=exited' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Status}}\t{{.Names}}'
docker ps -a --filter 'exited=0' --format '{{.ID}}\t{{.CreatedAt}}\t{{.Status}}\t{{.Names}}'

docker ps -a --filter 'id=47d858918ecb' --format 'CONTAINER ID: {{.ID}}\nIMAGE: {{.Image}}\nCOMMAND: {{.Command}}\nCREATED: {{.CreatedAt}}\nSTATUS: {{.Status}}\nPORTS: {{.Ports}}\nNAMES: {{.Names}}\n'

stella.+ 28042  0.1  2.2 177537468 3009412 pts/4 Sl+ 2019 283:03 tensorflow_model_server --port=8500 --rest_api_port=8501 --model_config_file=/home/stella.domingo/tfserving/models.conf

docker inspect --format='{{.Id}} {{.Parent}}' $(docker images --filter since=d11de48c2d90 -q)

du -h | sort -rh | head -5
df -h | sort -r -k 5 -i
du -h /var/ | sort -rh | head -5
du -h /var/lib/docker/ | sort -rh | head -10

ps aux --sort -rss | head -10
ps aux | sort -rk 3,3 | head -n 5
ps aux | sort -k 3,3 | tail -n 5

watch "ps aux | sort -nrk 3,3 | head -n 5"

TF-SERVING

docker run -itd --name tf-client-20191113 --gpus '"device=2"' -p 8181:8181 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ ubuntu:16.04
docker run -itd --name tf-svr-histo-20200108 --gpus '"device=0,1"' -p 7510:7510 --port=8500 --rest_api_port=8501 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ --model_config_file=/models/models.conf tensorflow/serving:1.12.3-gpu

docker run -p 8500:8500 -p 8501:8501 \
  --mount type=bind,source=/path/to/my_model/,target=/models/my_model \
  --mount type=bind,source=/path/to/my/models.config,target=/models/models.config \
  -t tensorflow/serving --model_config_file=/models/models.config

docker run -itd --name tf-server-20200108 -p 8502:8500 -p 8503:8501 --gpus '"device=0,1"' -v /home/aziz/:/home/ -v /raid/shared/aziz/models:/models/ tensorflow/serving:latest-gpu --mount type=bind,source=/raid/shared/aziz/models,target=/models/ --model_config_file=/models/models.conf 

docker run -itd --name tf-svr-histo-20200108 -p 8502:8502 --gpus '"device=0,1"' -v /home/aziz/:/home/ -v /raid/shared/aziz/models:/models/ tensorflow/serving:latest-gpu
docker run -itd --name tf-svr-histo-20200108 -p 7510:7510 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ --gpus '"device=0,1"' tensorflow/serving:1.12.3-gpu
docker run -itd --name tf-svr-histo-20200108 -p 7510:7510 -v /raid/shared/aziz/models:/models/ --gpus '"device=0,1"' tensorflow/serving:1.12.3-gpu

curl -d '{"instances": [1.0, 2.0, 5.0]}' -X POST http://localhost:8500/models/retina-resnet50:predict

docker run -itd --name tf-client-20200101 --gpus '"device=2"' -p 8010:8010 -v /home/aziz/:/home/ -v /raid/shared/aziz:/raid/ ubuntu:16.04

#docker run -itd --name tf-svr-retina-20210201 -p 8500:8500 -v /home/abdaziz.latip/:/home/ -v /home/abdaziz.latip/mip/models/retina:/models/ tensorflow/serving:1.12.3 --rest_api_port=8502 --model_config_file=/models/models.conf --enable_model_warmup=false
#docker run -itd --name tf-svr-histo-20200108 -p 8502:8500 -v /home/abdaziz.latip/:/home/ -v /home/abdaziz.latip/mip/models/histopathology:/models/ tensorflow/serving:2.0.0 --rest_api_port=8503 --model_config_file=/models/models.conf --enable_model_warmup=false
#docker run -itd --name tf-2.6 -p 2026:8888 tensorflow/tensorflow:2.6.0-gpu-jupyter
#docker run -itd --name tf-2.6-gpu --gpus all -p 2036:8888 tensorflow/tensorflow:2.6.0-gpu-jupyter
