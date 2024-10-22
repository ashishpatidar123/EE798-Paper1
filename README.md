# EE798-Paper1
## Model Training
### Training First-Stage Models
Mention the GPU_ID and the configuration file for the first stage model. I have used the DIV2K dataset so use the div2k configuration file.
```
CUDA_VISIBLE_DEVICES=<GPU_ID> python main.py --base configs/first-stage/<config_spec>.yaml -t --gpus 0, --scale_lr False
```
After successfull training of first stage model train the LDM by entering the checkpoint path in the configuration file of the ldm
### Training LDMs
Creates or modifies the config file in `configs/latent-diffusion/`.
Type ckpt_path to load the first_stage_model.

```
CUDA_VISIBLE_DEVICES=<GPU_ID> python main.py --base configs/latent-diffusion/<config_spec>.yaml -t --gpus 0, --scale_lr False
```
### Super-Resolution
run the below line with the exp file path obtained in the logs and mention the input low resolution image size and the scale ratio upto which we want to scale
```
python eval_sr.py --exp logs/<exp_path> --lr_size <input_lr_image_size> --scale_ratio <scale>
```

