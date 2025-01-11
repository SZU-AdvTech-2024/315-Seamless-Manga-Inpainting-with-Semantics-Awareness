1、环境配置
	pytorch >= 1.10
	torchvision  炬视讯
	pyyaml
	tensorboard  TensorBoard 板
	opencv-python
	tqdm
	py7zr
	kornia  科尼亚
	einops
	安装 Anaconda：https://conda.io/projects/conda/en/latest/user-guide/install/index.html

2、数据集准备和预处理
	下载 CASIA-B 数据集：http://www.cbsr.ia.ac.cn/english/Gait%20Databases.asp
	跑 python datasets/pretreatment.py --input_path CASIA-B --output_path CASIA-B-pkl

3、获取经过训练的模型
	python misc/download_pretrained_model.py

4、训练
	训练开始前，要先在config文件里设置好数据集的路径
	训练：CUDA_VISIBLE_DEVICES=0,1 python -m torch.distributed.launch --nproc_per_node=2 opengait/main.py --	cfgs ./configs/baseline/baseline.yaml --phase train
	测试：CUDA_VISIBLE_DEVICES=0,1 python -m torch.distributed.launch --nproc_per_node=2 opengait/main.py --	cfgs ./configs/baseline/baseline.yaml --phase test